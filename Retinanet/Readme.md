## Train a model

* Clone [keras-retinanet](https://github.com/fizyr/keras-retinanet) and install it 

* Prepare data and labels
* Check the validity of labels with:
```
retinanet-debug csv labels.txt classes.csv
```
* Train a model
```
retinanet-train csv  train.txt classes.csv
```
* Convert your best checkpoint with this command:
```
retinanet-convert-model resnet50_csv_07.h5 out7.h5
```

If you do not lknow which is the best, you can evaluate each checkpoint

```
retinanet-evaluate csv  valid.txt classes.csv out7.h5
```

## Export your model to a pb file

[Retinanet_deployment.ipynb](Retinanet_deployment.ipynb )

## Run your Docker
```
docker run -t --rm -p 8501:8501 -v "$PWD/retinanet_savedmodel:/models/retinanet/1" -e MODEL_NAME=retinanet proxy.it.sh:8082/tensorflow/serving:1.15.0-rc2
```

## Check your API
```
http://localhost:8501/v1/models/retinanet
```

## Send a request and get the output
[Retinanet_inference.ipynb](Retinanet_inference.ipynb)

