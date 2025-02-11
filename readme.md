# Accented Speech Technical Assessment

## Conclusion

This model performs poorly on the given dataset when tasked with classifying filipino and non-filopino accents according to typical evaluation metrics for such a task.

Specifically, the confusion matrix, precision and recall show that there is a significant bias toward non-filipino accents. The precision/recall curve is abyssmal showing that there are many, many misclassifications of the target class.

Additionally, the ROC/AUC is < .5 showing that the model is misclassifying more than it is classifying correctly.

Although, the model performs poorly out of the box on the provided dataset, there are many approaches that can be taken into consideration to improve the performance. Before discussing potential optimizations, let's look closer at the independent aspects of this challenge.

## On the dataset

This dataset is quite different from that of what the speechbrain model was trained on. Specifically in that the Speech Accent dataset share a common passage that is read by different speakers rather than a variety of utterances.

Consequently, the dataset is rather small, especially when dealing with a more 'niche' class like filipino. There are only ~30 instances of speakers from the Philippines. This would motivate a sampling strategy to improve statistical significance. Data augmentation, over-sampling, adding noise/generating samples etc could be useful in training a more robust model.

There is a lot of opportunity for feature engineering that may help models generalize this task better.

## On the model

Although it doesn't perform well in this particular task, this model is certainly powerful and can ~likely~ be tuned to better meet the needs of this task. Some things that could be considered are hyperparameter tuning, changing the learning rate, affecting layers with mechanisms like dropout or potentially saliency maps.

The difficulty the model seems to have is the inability to learn the features that distinguish accent. Typically we would like the model to learn these from the raw data (audio in this case) however, it might be useful to look into other representations such as MFCCs, deltas, wavelets, etc and compare performances.

## On the task

This is a non trivial task given the nature of unstructured data and there are many aspects of domain specific intuition that can help guide experimentation to better results. For instance, looking at relationships of vocal formants within a voice, using unsupervised learning techniques (t-SNE, persistent homology) and trying different architectures in ensemble to get a better insight of how speakers, languages, ages and countries may relate to each other.

I really enjoyed this task and am happy to have been able to dive in! Cheers :)
