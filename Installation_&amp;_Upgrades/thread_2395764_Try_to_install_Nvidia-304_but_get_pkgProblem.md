---
title: "Try to install Nvidia-304 but get pkgProblem"
date: 2018-07-06
forum: Installation &amp; Upgrades
---

### Post by orangebai on 2018-07-06
Hi, I am new to Ubuntu.
My version is 18.0.4.
I try to install Nvidia drivers for my computer. And here are my graphics card info:
>  lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [GeForce 610M] (rev a1)

and I have added repository:
> 
sudo add-apt-repository ppa:graphics-drivers
sudo apt-get update
sudo apt-get upgrade

I can install Nvidia-390 by:
> 
sudo apt-get install nvidia-390

but when I run 
> 
nvidia-smi

it shows "not supported".
I searched and find that my graphic card can only supported by nvidia-304 cause it is a hybrid gpu.
And then I run
> 
sudo apt-get install nvidia-304
[QUOTE]
get
[QUOTE]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gvfs : Depends: gvfs-daemons (>= 1.36.1-0ubuntu1)
        Depends: gvfs-daemons (< 1.36.1-0ubuntu1.1~)
 libgtk-3-0 : Depends: libwayland-egl1-mesa (>= 10.0.2) but it is not going to be installed or
                       libwayland-egl1
 nvidia-304 : Depends: xorg-video-abi-11 but it is not installable or
                       xorg-video-abi-12 but it is not installable or
                       xorg-video-abi-13 but it is not installable or
                       xorg-video-abi-14 but it is not installable or
                       xorg-video-abi-15 but it is not installable or
                       xorg-video-abi-18 but it is not installable or
                       xorg-video-abi-19 but it is not installable or
                       xorg-video-abi-20 but it is not installable or
                       xorg-video-abi-23
              Depends: xserver-xorg-core but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

I tried several days but failed to fix it.
Can anyone help me?
Thanks a lot

---

### Post by wildmanne39 on 2018-07-06
Hello and welcome to the forum!

Thread closed. Please do not post duplicates, use your other thread you created here:

[https://ubuntuforums.org/showthread.php?t=2395766](https://ubuntuforums.org/showthread.php?t=2395766)

Thanks

---

