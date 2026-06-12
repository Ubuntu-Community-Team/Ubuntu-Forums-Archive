---
title: "Using theano with GPU on ubuntu 14.04"
date: 2016-09-28
forum: Installation &amp; Upgrades
---

### Post by wangk4 on 2016-09-28
Hi,
I am trying to use theano on a GPU machine, I already install python packages and theano, and cuda 7.5. But when I use "import theano" in python, I got the error message like this:

modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_364_uvm'
modprobe: ERROR: could not insert 'nvidia_364_uvm': Function not implemented
WARNING (theano.sandbox.cuda): CUDA is installed, but device gpu is not available  (error: Unable to get the number of gpus available: unknown error)

Then when I run "nvidia-smi", I got the error message like this:

modprobe: ERROR: ../libkmod/libkmod-module.c:809 kmod_module_insert_module() could not find module by name='nvidia_364'
modprobe: ERROR: could not insert 'nvidia_364': Function not implemented
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

I don't how to make the theano works on the machine.
So dose anyone can give me any suggests? 
What should I do to make it work?

Thanks.

---

