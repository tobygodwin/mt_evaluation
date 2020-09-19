## Readme
#### Machine Translation Evaluation

This notebook was produced as part of a team of 3 and formed part of the submission for an NLP Coursework

All of the code that we have produced is present in a .ipynb file, which should be run using Google Colab. The code that we have provided aims to predict the quality of a machine translated sentence, where the translation is between English and German sentences. The data consists of pairs of English sentences and their machine-translated counterparts. The labels for this task were a direct assessment (DA) score for each sentence. The DA score is given by humans, where 0 is the lowest possible quality, and 100 is a perfect translation. The DA scores were presented in a z-standardised form per annotator. 

Thus the task of the is to predict the DA score for new pairs of source sentences and their machine translations.

The code provided is split into the follwing sections:

> Importing data and setting up GPU

> Computing sentence embeddings using the 'FLAIR' library: pre-processing the data and getting the training and validation sets

> Computing embeddings using the pre-trained BERT: pre-processing the data and getting the training and validation sets

> Pytorch Neural Network Regressor 

> Other Regressors that we experimented with

> Writing results into a .txt file

##### Tech

Our code uses the follwing libraries:

* IO module - provided Python interfaces for stream handling
* Torch - a library for creating neural networks and data handling
* Flair - a library for computing sentence embeddings 
* Scipy - a stats based library for data evaluation
* nltk - a library specialising in natural language processing 
* spacy - a library for data handling 
* transformers - a library such that we can import BERT modules
* SKLearn - a library to train regressors and neural networks 
* Keras - a library specilalising in building neural networks 

##### Installation

All of the above libraries need to be installed in order to run our .ipynb file. We have included all of the install commands in the file, therefore if you run each cell one after another each library will be installed. 

##### Instructions for code to be run 

The code is in a .ipynb file, which is in jupyter-notebook form. The code is split into sections that are meant to be run in chronological order. If one does not run the code in the correct order then necessary packages/libraries will not be installed/imported and the code will not run. I have split how to run the code into the follwing steps:

* The first step is to download the required data that will be using, which inclued the English German sentences, as well as the associated translation scores. 
* Next there is the data manipulation using NLP techniques and the BERT and FLAIR libraries. This section uses techniques to make the data easier to manipulate with our regressors, which will help us to evaluate the translations. 
* To use FLAIR embeddings run all of the cells under the 'Computing Sentence Embeddings - FLAIR library'. FLAIR embeddings only return vectors.
* To get BERT embeddings run all cells under 'Computing Embeddings - pretrained BERT'
* To run PyTorch NN regressor run all cells under 'Pytorch NN Regressor'
* The PyTorch NN regressor requires vector inputs. To return vector from the BERT embedding set pooling_fn=None
> de_train_mt = get_bert_embeddings("./train.ende.mt",'de', pooling_fcn=None)
* To run other regression methods run cells under 'Other regressors'. 
* Regressors in 'Other regressors' all take scalar inputs. To return scalar inputs from BERT embeddings set pooling_fn=torch.mean
> de_train_mt = get_bert_embeddings("./train.ende.mt",'de', pooling_fcn=None)
* Finally, we write our results into a .txt file which can be uploaded to the competition website Codalab. 
