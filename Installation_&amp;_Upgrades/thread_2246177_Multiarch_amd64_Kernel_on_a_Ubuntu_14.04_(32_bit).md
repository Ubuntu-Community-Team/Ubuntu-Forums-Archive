---
title: "Multiarch amd64 Kernel on a Ubuntu 14.04 (32 bit)"
date: 2014-09-29
forum: Installation &amp; Upgrades
---

### Post by eruptionjoojo on 2014-09-29
Hello Everyone,

         I have Ubuntu 14.04 (32 bit) installed on my laptop along with Windows 7 (64 bit). I'm wanting to install Mathworks MATLAB R2014a(8.03)(64 bit) under Ubuntu. So, after searching a bit I came to know about "Multiarch", but while I followed the steps listed under the below mentioned webpage, I wasn't able to connect to the internet i.e. eth0 got disabled after restart. The link to the web-page :-

[http://neuro.debian.net/blog/2013/2013-05-31_matlab_64bit_on_32bit.html]("http://neuro.debian.net/blog/2013/2013-05-31_matlab_64bit_on_32bit.html") 

after executing the below mentioned 64-bit kernel install command, it happened to remove my 32 bit kernel & header :-

```
sudo apt-get install linux-image-amd64
``` 

although I had to modify some steps in that like selecting the linux-kernel-image etc. but it went on smoothly except that after the restart system had slowed down as well I wasn't able to access internet i.e. it did not show eth0 under ifconfig.
Thus, I happened to restore my kernel to the previous 32 bit one using the Ubuntu 14.04 (32 bit) CD.

So, I searched a bit more and found this thread :-

[http://ubuntuforums.org/showthread.php?t=1874265&]("http://ubuntuforums.org/showthread.php?t=1874265&")

I followed the steps as mentioned in the thread but keep-on getting an error after excuting the below listed code :-

```
sudo apt-get install gcc-4.6-base:amd64 libacl1:amd64 libattr1:amd64 libc6:amd64 libdbus-1-3:amd64 libgcc1:amd64 libselinux1:amd64 libudev0:amd64 linux-base
``` 

Error :-

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libudev0:amd64 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libudev0:amd64' has no installation candidate

```

As I have read in a few threads that one needs to force install it but still was confused so didn't perform that step. 

                                                 So, I request you to help me in installing Mathworks MATLAB (64 bit) in Ubuntu 14.04 (32 bit). If you want some other information which would aid in sorting out the issue just ask for it.

Regards,
Joojo.

---

