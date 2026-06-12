---
title: "Installing CUDA on 18.04 LTS"
date: 2020-01-17
forum: Installation &amp; Upgrades
---

### Post by John Nagle on 2020-01-17
I'm trying to run Tensorflow on Ubuntu 18.04 LTS. Just upgraded from 16.04 LTS. x86-64, Nvidia 640.

The driver part of the CUDA install seems to be OK:

[FONT=courier new]nvcc --version
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2017 NVIDIA Corporation
Built on Fri_Nov__3_21:07:56_CDT_2017
Cuda compilation tools, release 9.1, V9.1.85
john@Nagle-LTS:/usr/local$ nvidia-smi
Fri Jan 17 20:15:42 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 435.21       Driver Version: 435.21       CUDA Version: 10.1     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 640      Off  | 00000000:01:00.0 N/A |                  N/A |
| 30%   31C    P8    N/A /  N/A |    302MiB /  1996MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+

[FONT=times new roman][FONT=arial]But if I try to run Tensorflow's basic test, I get

~/projects/sl/rasa$ python
Python 3.7.6 (default, Jan 17 2020, 10:24:03) 
[GCC 5.4.0 20160609] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import tensorflow as tf
2020-01-17 19:26:02.912477: W tensorflow/stream_executor/platform/default/dso_loader.cc:55] Could not load dynamic library 'libnvinfer.so.6'; dlerror: libnvinfer.so.6: cannot open shared object file: No such file or directory
2020-01-17 19:26:02.912566: W tensorflow/stream_executor/platform/default/dso_loader.cc:55] Could not load dynamic library 'libnvinfer_plugin.so.6'; dlerror: libnvinfer_plugin.so.6: cannot open shared object file: No such file or directory
2020-01-17 19:26:02.912575: W tensorflow/compiler/tf2tensorrt/utils/py_utils.cc:30] Cannot dlopen some TensorRT libraries. If you would like to use Nvidia GPU with TensorRT, please make sure the missing libraries mentioned above are installed properly.

Reading articles about this, it's a known problem, and on older versions there are all sorts of workarounds that bypass the package manager. I don't want to do that; the drivers and nVidia command line tools seem to be OK. But there's nothing in "/usr/local/cuda", the usual place for those libraries.

What installs those shared libraries without messing up anything else?

There's some discussion here: [https://devtalk.nvidia.com/default/topic/1066634/could-not-load-dynamic-library-libnvinfer-so-5-/](https://devtalk.nvidia.com/default/topic/1066634/could-not-load-dynamic-library-libnvinfer-so-5-/)

but itt's for an older version of the NVidia driver. I have driver 435.21 installed; those instructions have very specific version numbers and install driver 418.



[/FONT][/FONT]


[/FONT]

---

### Post by John Nagle on 2020-01-18
It gets worse. I tried to install cuda from the official NVidia site using the official NVidia procedure, at [https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=debnetwork](https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=debnetwork)

That almost worked. It failed with 

Errors were encountered while processing:
 /tmp/apt-dpkg-install-ncjNXt/29-libcublas-dev_10.2.2.89-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

That installed way too much, including a new NVidia driver that stuck my screen at 1024x768.

Now the package manager is stuck.

I get the Ubuntu 18.04 red circle with bar and a line through it, with the message "An error occured, please run package manager from the right-click menu ..." (What right-click menu? That feature seems to be gone from 18.04. But we will let that pass.)

So, tried "sudo apt --fix-broken install". No good: 

Unpacking libcublas-dev (10.2.2.89-1) ...
dpkg: error processing archive /var/cache/apt/archives/libcublas-dev_10.2.2.89-1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/nvblas.h', which is also in package nvidia-cuda-dev 9.1.85-3ubuntu1
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libcublas-dev_10.2.2.89-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Need to remove something and give up on tensorflow/cuda/etc to get going again. But what needs to be removed? Tried removing libcublas-dev. No good.

> sudo apt-get remove libcublas-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'libcublas-dev' is not installed, so not removed
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 cuda-libraries-dev-10-2 : Depends: libcublas-dev (>= 10.2.2.89) but it is not going to be installed
 cuda-samples-10-2 : Depends: libcublas-dev (>= 10.2.2.89) but it is not going to be installed
 cuda-visual-tools-10-2 : Depends: libcublas-dev (>= 10.2.2.89) but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

Now what? I'm willing to give up on cuda and tensorflow to get a working system back.

---

### Post by CatKiller on 2020-01-18
> **John Nagle said:**
> Need to remove something and give up on tensorflow/cuda/etc to get going again. But what needs to be removed? 

I would go for everything. 

The nvidia drivers don't upgrade cleanly between branches in any case, and you seem to be in a bit of a pickle. Purging all the nvidia packages, and probably the cuda ones too, and starting fresh will probably be the best way to get up and running. 

I only played with the cuda packages briefly, and a while ago, but there are metapackage in Nvidia's repository for which components you want to install. In particular, installing cuda but *not* installing the driver (so you can use your existing one instead) is a perfectly normal configuration.

---

### Post by John Nagle on 2020-01-18
I got Ubuntu working again by force-deleting nvidia-cuda-dev, which had a conflict over an include file. Then a Fix Broken Install worked and, after a reboot, the NVidia driver was in control and I had a full screen and OpenGL back.

The problem seems to be that nvidia-cuda-dev and libcublas-dev both want to install "/usr/include/nvblas.h". Right now I have a working system without nvida-cuda-dev.

CUDA is installed. Latest NVidia driver, even. Not sure who installed that.

[FONT=courier new](venv37) john@Nagle-LTS:~/projects/sl/rasa$ nvidia-smi
Sat Jan 18 13:22:38 2020       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 440.33.01    Driver Version: 440.33.01    CUDA Version: 10.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 640      On   | 00000000:01:00.0 N/A |                  N/A |
| 30%   32C    P8    N/A /  N/A |    218MiB /  1996MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+[/FONT]



 TensorFlow won't work, due to some missing .so files, but those may belong to the Python envrironment, so I can play around there with virtualenv without messing up the core system.
It wants  'libnvinfer.so.6: and 'libnvinfer_plugin.so.6'.

Those are mentioned at
[https://devtalk.nvidia.com/default/topic/1066634/could-not-load-dynamic-library-libnvinfer-so-5-/](https://devtalk.nvidia.com/default/topic/1066634/could-not-load-dynamic-library-libnvinfer-so-5-/) and at
[https://docs.nvidia.com/deeplearning/sdk/tensorrt-install-guide/index.html](https://docs.nvidia.com/deeplearning/sdk/tensorrt-install-guide/index.html)

but it's NVidia's "install everything AND the kitchen sink" installs that got me into this mess.

But at least Ubuntu is working again.

---

### Post by CatKiller on 2020-01-18
Glad to hear you're up and running again. 

> **John Nagle said:**
> but it's NVidia's "install everything AND the kitchen sink" installs that got me into this mess.

[Here's](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#package-manager-metas) a list of the  metapackages that nvidia use, in case that's useful.

---

