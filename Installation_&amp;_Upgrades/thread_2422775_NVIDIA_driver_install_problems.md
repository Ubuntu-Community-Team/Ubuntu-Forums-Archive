---
title: "NVIDIA driver install problems"
date: 2019-07-12
forum: Installation &amp; Upgrades
---

### Post by juakofz on 2019-07-12
Hi! I am finding problems installing NVIDIA drivers. I am on a freshly installed Ubuntu 16.04. Basically, it seems like the driver is installing but it's not loading.

I have checked many threads and posts all over the place, but I can't find a solution. My issue presents itself in a similar way to this one: [https://ubuntuforums.org/showthread.php?t=2412484](https://ubuntuforums.org/showthread.php?t=2412484) 

This is my graphics card:
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Device 3e9b
01:00.0 VGA compatible controller: NVIDIA Corporation GP104M [GeForce GTX 1070 Mobile] (rev a1)
```

These are the available drivers:
```
$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd00001BA1sv00001462sd00001214bc03sc00i00
driver   : nvidia-384 - distro non-free
driver   : nvidia-410 - third-party free
driver   : nvidia-396 - third-party free
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-390 - third-party free
driver   : nvidia-430 - third-party free recommended
driver   : nvidia-415 - third-party free
driver   : nvidia-418 - third-party free
```

This is the procedure I followed for installation
```

sudo apt-get purge nvidia-*
sudo apt-get autoremove --purge

sudo add-apt-repository ppa:graphics-drivers
sudo apt-get update

sudo apt-get install nvidia-430
```

After installation and reboot:
```
$ dpkg -l | grep -i  nvidiaii  bbswitch-dkms                                0.8-3ubuntu1                                          amd64        Interface for toggling the power on NVIDIA Optimus video cards
ii  libcuda1-430                                 430.26-0ubuntu0~gpu16.04.1                            amd64        NVIDIA CUDA runtime library
ii  nvidia-430                                   430.26-0ubuntu0~gpu16.04.1                            amd64        NVIDIA binary driver - version 430.26
ii  nvidia-opencl-icd-430                        430.26-0ubuntu0~gpu16.04.1                            amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                 0.8.2                                                 amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                              418.56-0ubuntu0~gpu16.04.1                            amd64        Tool for configuring the NVIDIA graphics driver
```

```

$ lsmod | grep nouveau
$ lsmod | grep nvidia
$
```

```
$ nvidia-settings 

ERROR: Unable to load info from any available system
```

No idea what to do. Any help would be greatly appreciated. Thank you very much!

---

### Post by Bashing-om on 2019-07-12
juakofz; Hello -

Nvidia driver install process is in the throsous of change.

I am not on 16.04 so can not verify this procedure, but let's look.

what results:
```

apt list nvidia-430

```
A null return ?

Now what shows:
```

apt list nvidia-driver-430

```

Note that the naming is changed.

Also worthy of thought is to allow the system to choose and install the driver it thinks best:
Once all purged - including the config file "/etc/X11/xorg.conf" -  :
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

[INDENT][INDENT]in the process to help :)
[/INDENT][/INDENT]

---

### Post by TheFu on 2019-07-12
Good news!  [https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its)  so shortly, 16.04 nvidia driver support should be nearly automatic.  No ETA.

I'm on 16.04 with a 1030 GPU, but usually don't login on that machine's console to actually use it. Here's what I'm running:
```
$ dpkg -l|grep nvidia
ii  nvidia-415                                  415.27-0ubuntu0~gpu16.04.1                   amd64        NVIDIA binary driver - version 415.27
ii  nvidia-opencl-icd-415                       415.27-0ubuntu0~gpu16.04.1                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.2                                        amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             418.56-0ubuntu0~gpu16.04.1                   amd64        Tool for configuring the NVIDIA graphics driver
```

I can wait until the nvidia drivers are updated via apt.  

```
$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:03.1/0000:08:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd00001D01sv00003842sd00006336bc03sc00i00
driver   : nvidia-390 - third-party free
driver   : nvidia-415 - third-party free
driver   : nvidia-384 - distro non-free
driver   : nvidia-418 - third-party free
**driver   : nvidia-430 - third-party free recommended**
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-410 - third-party free
driver   : nvidia-396 - third-party free

```
Perhaps I should install the 430 at my next patch session, which is tomorrow AM.

Ah ... the xorg setup I have is 100% custom due to an active DVI-d to VGA adaptor I have to use to force the correct EDID monitor information.

---

### Post by juakofz on 2019-07-13
> **Bashing-om said:**
> 
what results:
```

apt list nvidia-430

```
A null return ?


```
$ apt list nvidia-430
Listing... Done
nvidia-430/xenial,now 430.26-0ubuntu0~gpu16.04.1 amd64 [installed]

```

> **Bashing-om said:**
> 
Now what shows:
```

apt list nvidia-driver-430

```


```
$ apt list nvidia-driver-430
Listing... Done

```

> **Bashing-om said:**
> 
Also worthy of thought is to allow the system to choose and install the driver it thinks best:
Once all purged - including the config file "/etc/X11/xorg.conf" - :
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

This installed exactly the same drivers and led to the same results :/

---

### Post by TheFu on 2019-07-13
Patching this morning ... 

```
$ sudo ubuntu-drivers autoinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  glmark2-data
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  libcuda1-430 nvidia-opencl-icd-430
The following packages will be REMOVED:
  libcuda1-415 nvidia-415 nvidia-opencl-icd-415
[B]The following NEW packages will be installed:
  libcuda1-430 nvidia-430 nvidia-opencl-icd-430
[/B]0 upgraded, 3 newly installed, 3 to remove and 0 not upgraded.
Need to get 107 MB of archives.
After this operation, 19.3 MB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) xenial/main amd64 nvidia-430 amd64 430.26-0ubuntu0~gpu16.04.1 [99.7 MB]
.....
```
Lots of DKMS action.  I didn't do anything on the machine except the normal update/upgrade and the command at the top of this post.

---

