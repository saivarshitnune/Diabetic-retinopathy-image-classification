#  Automated System for Accurate Classification of Diabetic Retinopathy using AI

Diabetic Retinopathy (DR) is a severe eye condition that can lead to vision loss in individuals with long-standing diabetes. The prevalence of DR is alarmingly high, and early detection and timely treatment are crucial to prevent severe visual impairment. Traditional methods for DR screening involve manual interpretation of retinal images, which can be time-consuming and prone to human error. The increasing incidence of diabetes and the limited number of specialized ophthalmologists further hinder timely and accurate diagnosis.

Current methods for detecting Diabetic Retinopathy are labor-intensive, subjective, and inconsistent. These limitations lead to delays in diagnosis and intervention, which can result in irreversible vision loss for patients. There is an urgent need for an automated, reliable, and accurate system that can assist healthcare professionals in diagnosing and grading the severity of Diabetic Retinopathy efficiently.

![DR_NDr](https://github.com/saivarshitnune/Diabetic-retinory-image-classification/assets/121888709/bb3f20ef-a426-48f9-a2dd-71016445f841)


# About Data
The prevalence of Diabetic Retinopathy is alarmingly high, affecting a significant proportion of individuals with long-standing diabetes. Early detection and timely treatment are crucial for preventing vision loss and improving patient outcomes. However, manual interpretation of retinal images for Diabetic Retinopathy screening can be time-consuming and subject to human error. Therefore, there is a pressing need for an automated and accurate tool that can assist healthcare professionals in grading the severity of Diabetic Retinopathy.

The existing methods for detecting and grading Diabetic Retinopathy often rely on subjective assessments and extensive manual labor, leading to inefficiencies and potential inconsistencies in diagnosis. Moreover, the increasing prevalence of diabetes and the limited availability of ophthalmologists further exacerbate the challenges in timely screening and diagnosis. Therefore, there is a need to develop a robust and reliable automated system that can accurately detect and grade Diabetic Retinopathy, enabling early intervention and personalized treatment plans.


This dataset consists of a large collection of high-resolution retinal images captured under various imaging conditions. A medical professional has assessed the presence of Diabetic Retinopathy in each image and assigned a rating on a scale ranging between 0 and 1, which corresponds to the following categories:

1. Diabetic Retinopathy     --->    0
2. No Diabetic Retinopathy  --->    1

   

The Diabetic Retinopathy Disease Dataset is a comprehensive collection of 2838 high resolution images divided into two classes

 Diabetic Retinopathy (DR)
 
 No Diabetic Retinopathy(No_DR)
 

![Diabetic Table](https://github.com/saivarshitnune/Diabetic-retinory-image-classification/assets/121888709/45d72f7e-4f9b-49e0-97f2-bba933ca7fe6)


# Approach 
1. Preprocess and analyze the dataset of retinal images to understand the key features influencing diabetic retinopathy .
2. Develop a deep learning model to classify the diabetic retinopathy disease effectively.
3. Validate the model's performance using appropriate metrics and ensure its robustness and reliability in real-world scenarios.

# Data Understanding
On detailed scrutiny of the data we found our data is influenced by below mentioned factors.

![Dr_img](https://github.com/saivarshitnune/Diabetic-retinory-image-classification/assets/121888709/93e4a5ae-ceeb-4a16-8b63-4da62a2a107a)


Our classification is mainly influenced by colour of the eye and black spots in the eye.It is observed that
1. For the images which is having Diabetic retinopathy has larger black spots and non red colour in the eye.
2. For the images which is having No Diabetic retinopathy has bright red colour in the eye.

So Our selected model and loss function should be complex enough to classify based on its colour (In a human understading method).


# Model Selection :- 
 As per our understanding the model should be able to learn the subtle differences in the complex visual features. 
 
 Here we are selecting VGG16 and ResNet50 as our model architecture.
 
 1. VGG16 architecture, characterized by its depth and use of small, uniform filters, provides robust feature extraction capabilities. This is particularly 
   advantageous for detecting the subtle and varied signs of Diabetic Retinopathy in retinal images.

   Please refer https://arxiv.org/pdf/1409.1556 for VGG16 understanding.

2. ResNet50 is selected as our model architecture because of its residual connections to tackle vanishing gradient problems in deeper networks. This is particularly 
   advantageous for detecting the subtle and varied signs of Diabetic Retinopathy in retinal images.

   Please refer https://arxiv.org/pdf/1512.03385 for ResNet50 understanding.

# Training
  Frame work : Tensor Flow
  
  Model : ResNet50 and VGG16 
  
  Base weights : ImageNet 
  
  Loss function : CategoricalCrossentropy
  
  Optimizer : Adam
  
  Learningrate : 0.001
  
  Number of epochs : 50
  
  Call backs - EarlyStopping , ModelCheckpoints and LR Reduceonplateau 

# Performance evaluation metrics 
 1. Model :- VGG16
     
     Confusion Matrix :-

       ![cm_dr](https://github.com/saivarshitnune/Diabetic-retinory-image-classification/assets/121888709/eed91491-a18c-4e5f-b3fd-ba04dda3fc01)
     

       1. Diabetic Retinopathy     --->    0
       2. No Diabetic Retinopathy  --->    1

       There are total 9 missclassifications in which 4 images are false positives (No_DR is predicted as DR) and 5 images are false negatives
        (DR is predicted as No_DR).
     

    Classification report :-

    ![Cp_DR](https://github.com/saivarshitnune/Diabetic-retinory-image-classification/assets/121888709/afd9d0f6-dfd4-469e-9f68-32af6d8942e0)

     Achieved an
   
     Test Accuracy of 95.54 %
   
     96% Recall
    
     96% precision
   
     96% F1 score






2. Model - ResNet50
  
   Confusion matrix :-
  
    ![image](https://github.com/saivarshitnune/Diabetic-retinory-image-classification/assets/121888709/e64da56e-44f0-4014-92b5-e9652c973f60)

    1. Diabetic Retinopathy     --->    0
    2. No Diabetic Retinopathy  --->    1

    There are total 21 missclassifications in which 10 images are false positives (No_DR is predicted as DR) and 11 images are false negatives
     (DR is predicted as No_DR)
  

     Classification report :-

      ![Cp_DR](https://github.com/saivarshitnune/Diabetic-retinory-image-classification/assets/121888709/b52ca7ed-6efe-42a9-b4a4-e93aaba2b493)

   
      Achieved an
   
      Test Accuracy of 90.18 %
   
      91% Recall
    
      91% precision
   
      91% F1 score


By observing performance evaluation metrics of the both models VGG16 is over performed on ResNet50. Because the ResNet50 model is overfitting to the input data as it is a more deeper and complex network it requires more data to improve the performance.

# Conclusion :-
 This project showcases the potential of deep learning models, particularly VGG16 and ResNet50 in addressing critical need in contemporary healthcare by leveraging the power of these advanced convolutional neural networks, the proposed system significantly enhances the accuracy and efficiency of retinal image analysis.This approach mitigates the limitations associated with manual interpretation, such as human error and variability in diagnosis, while also addressing the challenges posed by the increasing prevalence of diabetes and the scarcity of specialized ophthalmologists and can be improved by training with more diversified and more number of samples for robust  diabetic retinopathy disease classification.



