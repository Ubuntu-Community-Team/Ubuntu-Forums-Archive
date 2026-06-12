---
title: "how to install soft (.tar)"
date: 2008-04-17
forum: Installation &amp; Upgrades
---

### Post by brotin on 2008-04-17
I am new ubuntu user. I search internet for installing soft. and then i tried but it not installed (like amarok-1.4.8.tar.bz2, MPlayer-1.0rc2.tar.bz2 and many more) when i step to install always there is some problem like "error: C compiler cannot create executables
See"

Please help me any one

---

### Post by hariprs on 2008-04-17
can you post complete trace that you see during compilation?

---

### Post by ad_267 on 2008-04-18
You should use synaptic to install software.

Go to System - Administration - Synaptic Package Manager. From there you can search for software you want and install it without having to compile source code.

Please read this: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

If you do want to install a file by compiling from source then you will need the build essential package which can be obtained by entering this into a terminal:
```
sudo apt-get install build-essential
```

---

### Post by brotin on 2008-04-18
my complete post is

austin@austin-desktop:~$ cd Desktop
austin@austin-desktop:~/Desktop$ cd gstreamer-0.10.19
austin@austin-desktop:~/Desktop/gstreamer-0.10.19$ sudo ./configure
[sudo] password for austin:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking nano version... 0 (release)
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
austin@austin-desktop:~/Desktop/gstreamer-0.10.19$

---

### Post by ad_267 on 2008-04-18
Did you even read my post?

Install the build-essential package if you want to compile software. If you'd rather install things the easy way then use the synaptic package manager or apt-get from the command line.

---

### Post by zvacet on 2008-04-19
Read [this.]("http://www.cutlersoftware.com/ubuntuinstall/")

---

### Post by brotin on 2008-04-19
i tried by u'r command but it still have problem. what can i do?

---

### Post by Partyboi2 on 2008-04-19
If you are stilling having problems after you have installed build-essential then have a look in the`config.log' in gstreamer-0.10.19 folder for more info.

---

