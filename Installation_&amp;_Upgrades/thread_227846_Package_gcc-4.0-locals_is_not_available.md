---
title: "Package gcc-4.0-locals is not available"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by pencortod on 2006-08-02
Please forgive me if this is a really stupid thing, I am a Windows guy trying to work in Ubuntu.
I have 6.06LTS setup and operational and I am attempting to thru the Setup of VMWare server. I have updated the system using Synaptic and I am trying to follow the "How to install VMware server on Ubuntu 6.06 LTS" on Howtoforge.  Everything is going along well until I run the following :

apt-get install gcc binutils-doc cpp-doc gcc-4.0-locales make manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc gcc-4.0-doc libc6-dev-amd64 lib64gcc1 

I get Package gcc-4.0-locales is not available, but is referred to by another package.
This may mean the package is missing, has been obsoleted or is only available from another source.
E: Package gcc-4.0-locales has no installation candidate.

I have reinstalled the gcc-4.0-base as well as the gcc-4.0 using Synaptic but still no happy face.

Can someone point me in the right direction and give me a shove?

Thank You in advance.

---

### Post by zxee on 2006-08-02
> **pencortod said:**
> 

apt-get install gcc binutils-doc cpp-doc gcc-4.0-locales make manpages-dev autoconf automake1.9 libtool flex bison gdb gcc-doc gcc-4.0-doc libc6-dev-amd64 lib64gcc1 

I get Package gcc-4.0-locales is not available, but is referred to by another package.
This may mean the package is missing, has been obsoleted or is only available from another source.
E: Package gcc-4.0-locales has no installation candidate.

I have reinstalled the gcc-4.0-base as well as the gcc-4.0 using Synaptic but still no happy face.

Can someone point me in the right direction and give me a shove?

Thank You in advance.

Sometimes the apt message you provided is caused by not having the correct repositories. You can check your /etc/apt/sources.list against those listed on the forum. Also have you run > sudo apt-get update? Hope that helps.

---

