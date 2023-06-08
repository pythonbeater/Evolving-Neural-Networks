# Evolving-Neural-Networks
This project was made in scope of Neuroevolution, were the objectivo is to build the first stepping stones for a “DENSER-like” framework.

The purpose of this project is to build the first stepping stones for a “DENSER-like” framework.
Based on the work developed in the practical classes, this project will consist of:

1. Defining a string-based representation for the networks (the genotype).

2. Defining a network class that is able to parse those instructions and build a functional pytorch network structure (the phenotype).

3. Defining a string-based representation for the optimizer.

4. Defining a way to parse those instructions and build and functional pytorch optimizer.

5. Sample all parameter values from a grammar (this allows for a restricted search space and removes the need to deal with invalid combinations).

6. Define 4 simple genetic operators:

a. Network crossover

    b. Add layer mutation
    c. Remove layer mutation
    d. Change optimizer mutation

### __Details__

The grammar should contain a reasonable number of parameters for each of the layers/optimizers. Provided the values of the parameters are standard and within reason, there is no need to justify their choice.

The networks need to be able to use the following layers and their respective parameters:

* Linear : number of features, bias
* BatchNorm1d : eps, momentum
* LayerNorm : eps
* Dropout : dropout probability (p)
* AlphaDropout : dropout probability
* [ Sigmoid , ReLU , PReLU , ELU , SELU , GELU , CELU , SiLU ]

The networks need to be able to be trained using the following optimizers and their respective parameters:

* Adam : lr, betas
* AdamW : lr, betas, weight decay
* Adadelta : lr, rho
* NAdam : lr, betas, momentum decay
* SGD : lr, momentum, nesterov

Each network needs to have at least 1 layer and a maximum 50 layers. This choice needs to be made at random when generating the genotype.

The genetic operators that need to be implemented are the following:
* Crossover : Takes a subset of layers from 2 different networks and swaps them. This subset cannot include the first and final layers.
* Add layer mutation : Add any new layer to any part of the genotype, and rebuild the network. It cannot be added before the first or after the last layer.
* Remove layer mutation : Remove any layer that is neither the first nor the last from the genotype and rebuild the network.
* Change optimizer mutation : Change any parameter from the optimizer genotype and rebuild it. If the type of optimizer is changed, the parameters must also be changed to ensure a valid optimizer is generated.

### __Experimental setup__

Generate 5 random networks and train them. Then, apply crossover to two of them and one of each mutation to the remaining 3 networks. Then, retrain the newly generated networks.
The networks should be trained on the mnist dataset, for 50 epochs, following the same procedure as used in the practical classes (showing the training and validation loss and accuracy per epoch).
