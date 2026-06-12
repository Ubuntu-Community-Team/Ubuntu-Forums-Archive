---
title: "pip3 SSL error for Tensorflow installation"
date: 2018-03-01
forum: Installation &amp; Upgrades
---

### Post by papatya2 on 2018-03-01
I try to install Tensorflow. Giving pip3 SSL error...

$ sudo -H pip3 install tensorflow-1.5.0-cp36-cp36m-linux_x86_64.whl
pip is configured with locations that require TTL/SSL, however the ssl module in Python is not available.
....
Could not fetch URL [https://pypi.python.org/simple/tensorflow-tensorboard/:](https://pypi.python.org/simple/tensorflow-tensorboard/:) There was a problem confirming the ssl certificate: Can't connect to HTTPS URL because the SSL module is not available. - skipping

I installed Python, Cuda, cuDNN, other configuration, etc.
Is there any workaround to run pip3 with SSL without reinstalling Python (without uninstall something) ?

System info is below :
Ubuntu 16.04.9 : Ubuntu 5.4.0-6ubuntu1 : GCC 5.4.0
GPU GTX 1080 ti
64 bit
NVIDIA Driver 390.25 : NVIDIA-Linux-x86_64-390.25.run
CUDA Toolkit 9.1
Python3.6.4

---

