+++
title = "Multi-modal Representation"
author = ["Jethro Kuan"]
lastmod = 2020-02-21T15:10:23+08:00
slug = "multimodal_representation"
draft = false
+++

tags
: [Multi-modal Machine Learning]({{< relref "20200219115844_multimodal_machine_learning" >}})

A multi-modal representation is a representation of data using
information from multiple modalities. The ability to represent data in
a meaningful way is crucial to multimodal problems.


## Key Challenges {#key-challenges}

-   how to combine data from heterogeneous sources
-   how to deal with differing levels of noise, and noise otpology
-   how to deal with missing data


## Categories of multi-modal representations {#categories-of-multi-modal-representations}

<a id="fe1ca450aa5e404428b89a0e174b2e99" href="#baltrusaitis17:_multim_machin_learn">(Baltru\vsaitis et al., 2017)</a> proposes two categories of
multimodal representation:

joint
: combining unimodal signals into the same representation space.

coordinated
: process unimodal signals separately, but enforcing
    certain similarity constraints on them to bring them into a
    coordinated space.


## Joint Representations {#joint-representations}

Joint representations are mostly used in tasks where multimodal data
is present during both training and inference.


### Neural Networks {#neural-networks}

A common approach is to use deep neural networks to create abstract
representations of unimodal data, beore combining them in the last
layer (for example, via concatenation). The hidden layers project the
modalities into a joint space. There is a close relationship between
multimodal representation learning and [multi-modal fusion]({{< relref "20200219121628_multimodal_fusion" >}}) when using
neural networks.

It is common to pretrain these representations using
an [autoencoder]({{< relref "20200219121741_autoencoder" >}}) on unsupervised data, because neural networks require a
lot of labelled data. The neural network approach often yields
superior performance, but is _unable to handle missing data naturally_.


### Probabilistic Graphical Models {#probabilistic-graphical-models}

[Probabilistic Graph Models]({{< relref "pgm" >}}) construct representations through the use
of latent random variables.

A popular approach is [Deep Boltzmann Machines]({{< relref "20200219122016_deep_boltzmann_machines" >}}), which uses [Restricted
Boltzmann machines]({{< relref "20200219122024_restricted_boltzmann_machines" >}}) as building blocks. Each successive layer of a DBM
is expected to represent the data at a higher level of abstraction.
DBMs do not need supervised data for training. It is also possible to
convert them into a deterministic neural network, but this loses the
generative aspect of the model.

One advantage of using multimodal DBMs is that they are [generative
models]({{< relref "20200219123016_generative_models" >}}), allowing them to:

1.  Naturally deal with missing data.
2.  Generate samples of one modality in the presence of at least 1
    modality


## Coordinated Representations {#coordinated-representations}

Separate representations are learnt from each modality, but later
coordinated through a constraint.

**Similarity models** minimize the distance between modalities in the
coordinated space. Neural network approaches such as DeViSE use inner
product and a ranking loss function.

Some models use a **structured coordinated space**, enforcing additional
constraints between the modality representations. These structural
constraints differ across applications, which include [cross-modal hashing]({{< relref "20200219154432_crossmodal_hashing" >}}),
cross-modal retrieval, and image captioning.

Other examples of structured coordinated spaces use enforce a partial
order in the multimodal space. Another special case of this is
[canonical correlation analysis]({{< relref "20200219160013_canonical_correlation_analysis" >}}).

# Bibliography
<a id="baltrusaitis17:_multim_machin_learn" target="_blank">Baltru\vsaitis, Tadas, Ahuja, C., & Morency, L., *Multimodal machine learning: a survey and taxonomy*, CoRR, *()*,  (2017). </a> [↩](#fe1ca450aa5e404428b89a0e174b2e99)
