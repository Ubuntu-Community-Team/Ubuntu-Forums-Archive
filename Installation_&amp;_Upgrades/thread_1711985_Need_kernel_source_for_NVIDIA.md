---
title: "Need kernel source for NVIDIA"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2011-03-22
I made the subdirectory ~/build and put the NVIDIA driver into it.

When I try to install it it complaints that it needs the kernel source.

I found 
sudo apt-get install fakeroot build-essential crash kexec-tools makedumpfile kernel-wedge
sudo apt-get build-dep linux
sudo apt-get install git-core libncurses5 libncurses5-dev libelf-dev asciidoc binutils-dev

and it installed a directory ~build/ubuntu-lucid

That is not the place the kernel source should be, so NVIDIA complained still that it does not find the kernel source.

I added --kernel-source-path ~/build/ubuntu-lucid/ and it complaint that 
~build/ubuntu-lucid//include/linux/version.h does not exist, ...... 

So how do I get my system running again?

Thanks for your quick help, .... I need that, ... ;-)


bye

Ronald

---

### Post by An Sanct on 2011-03-22
To download the sources, use
```

sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r) 
apt-get source linux-image-$(uname -r)

```
Where **$(uname -r)** returns your currently used kernel version.

PS. The source will be downloaded into the directory, where the command is executed.

---

### Post by ELMIT on 2011-03-22
Still no luck!

I did as you said and moved that all to /usr/src/ where all linux-headers are

I started then to install the NVIDIA as usually with 
sudo sh NVIDIA-Linux-x86_64-260.19.36.run --kernel-source-path /usr/scrc/linux-2.6.32 and get as error:

/usr/src/linux-2.6.32/include/linux/version.h does not exist


What do I next?

---

### Post by ELMIT on 2011-03-22
trying make oldconfig
make include/linux/version.h

brings me a step further. During the try to install the NVIDIA
I get the message:

> ...
If you are using a Linux 2.6 kernel, please make sure you have configured kernel sources matching your kernel installed on  your system. If you specified a separate output directory using either the "KBUILD_OUTPUT" or the "O" KBUILD parameter, make sure to specify this directory with the SYSOUT environment variable or with the equivalent nvidia-installer command line option.

Depending on where and how the kernel sources (or the kernel headers) were installed, you may need to specify their location with the SYSSRC environment variable or the equivalent nvidia-installer command line option.


---

### Post by An Sanct on 2011-03-22
Since it complains about **version.h** is it in another location? Maybe a sub-folder?

---

### Post by ELMIT on 2011-03-22
above two make commands made the version.h and brought me one step further, ....

What should I do next?

---

### Post by ELMIT on 2011-03-22
Anybody? Please!

---

### Post by An Sanct on 2011-03-23
Well :) I haven't had such problems yet, but my first guess is, version.h is needed and if the above two commands produced it for you, put it where it is needed. :)

so to:
[CODE]/usr/src/linux-2.6.32/include/linux/version.h[CODE]

---

