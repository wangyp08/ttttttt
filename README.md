# ttttttt
Code for Ultra-Fine Entity Typing (ACL 2018)
[Prepare data]
1. Download pretrained word embeddings from http://nlp.stanford.edu/data/glove.840B.300d.zip
2. Download dataset from http://nlp.cs.washington.edu/entity_type/data/ultrafine_acl18.tar.gz
3. unzip Glove word embeddings and dataset in "data" folder

[Configuration]
4. Set three paths at ./resources/constant.py

	FILE_ROOT=where you our dataset.
  
	GLOVE_VEC=the path where you can find pretrained glove vectors.
  
	EXP_ROOT=where you save models.
	
[Train model]
5. On open dataset: 
   python3 main.py MODEL_ID -lstm_type single -enhanced_mention -data_setup joint -add_crowd -multitask

   On Ontonotes dataset:
   python3 main.py onto -lstm_type single -goal onto  -enhanced_mention
   
[Test model]
6. On open dataset:
   python3 main.py MODEL_ID -lstm_type single -enhanced_mention -data_setup joint -add_crowd -multitask -mode test -reload_model_name MODEL_NAME_TIMESTAMP -eval_data crowd/test.json -load

   On Ontonotes dataset:
   python main.py MODEL_ID -lstm_type single -enhanced_mention -mode test -goal onto -reload_model_name MODEL_NAME_TIMESTAMP -load


