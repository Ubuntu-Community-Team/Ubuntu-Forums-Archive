---
title: "MP3 support - fails"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2006-12-28
I tried to add mp3 support, by:

1. sudo apt-get install build-essential

which required my 6.06.1 CD

During the installation it founds:

Failed to fetch cdrom:[Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)]/pool/main/g/gcc-4.0/libstdc++6-4.0-dev_4.0.3-1ubuntu5_i386.deb  MD5Sum mismatch

I have no idea how to overcome this!


I have downloaded gst-plugins-good-0.10.5.tar.gz and because of above, step 2 fails as well:

2. sudo ./configure

checking for winsock2.h... no

configure: *** checking feature: enable building of plug-ins with external deps ***
configure: building external plug-ins

configure: *** checking feature: enable building of experimental plug-ins ***
configure: not building experimental plug-ins
checking whether byte ordering is bigendian... no
checking whether byte ordering is bigendian... (cached) no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether we are using the GNU C++ compiler... (cached) no
checking whether g++ accepts -g... (cached) no
checking dependency style of g++... (cached) none
checking for g++... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.


Any hints how to solve it?

bye

Ronald

---

### Post by shrimphead on 2006-12-28
try going into synaptic properties and unchecking the CD as a source and using the packages from the online repos.

and to install mp3 support you should only need to 

```

sudo apt-get install gstreamer-plugins-ugly
```

---

### Post by ELMIT on 2006-12-28
Thanks, but something is still wrong.

grep -v ^# /etc/apt/sources.list

deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://tw.archive.ubuntu.com/ubuntu/](http://tw.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

deb [http://packages.freecontrib.org/ubuntu/freecontrib/](http://packages.freecontrib.org/ubuntu/freecontrib/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/freecontrib/](http://packages.freecontrib.org/ubuntu/freecontrib/) dapper free non-free
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free



and 

 sudo apt-get install gstreamer-plugins-ugly
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gstreamer-plugins-ugly


Maybe I understood "synaptic properties" wrong!

bye

Ronald

---

