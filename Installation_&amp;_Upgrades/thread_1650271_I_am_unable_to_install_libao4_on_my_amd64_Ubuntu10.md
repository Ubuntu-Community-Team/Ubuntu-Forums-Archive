---
title: "I am unable to install libao4 on my amd64 Ubuntu10.04"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by isaac_moller on 2010-12-21
Hi,


I am trying to install pianobar_2010.11.06-1_amd64.deb  on my amd64 Ubuntu 10.04 LTS, and I first need to install libao4, but  my synaptic package manager does see it as downloadable it only sees  libao2, and that wont do it.
 I downloaded the files, but I do not know the command lines to install it.
 

HALP?
 

Thanks
Isaac

---

### Post by dino99 on 2010-12-21
i'm on natty right now and have libao4 on i386

to install the package into a terminal:

sudo dpkg -i package

---

### Post by isaac_moller on 2010-12-21
aarrggg maybe libao4 doesn't work with my 64bit version of Ubuntu10.04?

This is what I get when I try to download the package:

moller@moller-desktop:~$ sudo dpkg -i libao4
dpkg: error processing libao4 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libao4


I tried that command inside my libao-1.0.0 folder and no dice (I downloaded and extracted "libao_1.0.0.orig.tar.gz")

Thanks

---

### Post by sikander3786 on 2010-12-22
Instead of tar.gz, download the .deb here and try the same command mentioned by *dino99*.

[http://packages.ubuntu.com/maverick/libao4](http://packages.ubuntu.com/maverick/libao4)

---

### Post by isaac_moller on 2010-12-29
Thank you so much guys I was able to install pianobar after installing the following files:

libao-common_1.0.0-4_amd64.deb


libao4_1.0.0-4_amd64.deb


pianobar_2010.11.06-1_amd64.deb

In that order

Thanks so much

Isaac
Problem solved!

---

