# Synthetic-Image-Generation-using-Cyclic-GANs
This is done as a part of the ongoing Kaggle competition: I’m Something of a Painter Myself

As a part of the competition, We had to build a GAN that generates 7,000 to 10,000 Monet-style images.

A GAN consists of at least two neural networks: a generator model and a discriminator model. The generator is a neural network that creates the images. For the competition, the generator model generate images in the style of Monet. This generator is trained using a discriminator.The two models work against each other, with the generator trying to trick the discriminator, and the discriminator trying to accurately classify the real vs. generated images.

The discriminator takes in the input image and classifies it as real or fake (generated).The discriminator loss function compares real images to a matrix of 1s and fake images to a matrix of 0s. The perfect discriminator will output all 1s for real images and all 0s for fake images. The discriminator loss outputs the average of the real and generated loss.

The generator wants to fool the discriminator into thinking the generated image is real. The perfect generator will have the discriminator output only 1s. Thus, it compares the generated image to a matrix of 1s to find the loss.

We want our original photo and the twice transformed photo to be similar to one another. Thus, we can calculate the cycle consistency loss by finding the average of their difference.

# To know more about the data, visit: https://www.kaggle.com/c/gan-getting-started/data

# To learn more about GANS, refer to https://www.kaggle.com/competitions/gan-getting-started/discussion/180515

# So what are GANS?
GANs or Generative Adversial Networks comprise atleast two neural networks that are trained simultaneously, namely the generator and the discriminator.

The generator learns how to create new images over time that resemble real images and tries to confuse the discriminator whose sole aim is to differentiate between which image is really real and which one is fake/generated.

# Moving forward to CycleGAN
CycleGAN uses a cycle consistency loss to enable training without the need for paired data. It can translate from one domain to the other without the need of a one-to-one mapping between the source and target domain. All we requre is a directory of source and target images.

# I found this analogy helpful to understand Cyclic GAN architecture
![Uploading image.png…]()



First, we get the regular generator discriminator thing, where the generator tries to generate images that seem to be drawn to the given domain (in the example will be creating zebra images), but it would be possible that the generator generates only the same zebra image or zebra images that do not look like the imputed horse image, this is why the model has a second generator, this second generator uses the first generated image and tries to recreate the original imputed horse image, this way the first generator has to generate zebra images that look like the imputed horse image.

In the end, you will get 4 sub-models:
* A generator that can generate zebras images
* A generator that can generate horses images
* A discriminator that can identify real zebras images
* A discriminator that can identify real horses images

Code requirements: GPU P100
