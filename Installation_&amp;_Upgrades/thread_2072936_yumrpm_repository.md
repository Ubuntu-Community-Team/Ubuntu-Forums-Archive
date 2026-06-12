---
title: "yum/rpm repository"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by h66m9d on 2012-10-18
hi
how can I add respiratory for yum or rpm in ubuntu?
when I try to install google chrome with yum. It say: "you need more library for this instalation":
> 
root@hamed-desktop:~# rpm -i Desktop/google-chrome-stable_current_i386.rpm
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
warning: Desktop/google-chrome-stable_current_i386.rpm: Header V4 DSA/SHA1 Signature, key ID 7fac5991: NOKEY
error: Failed dependencies:
    lsb >= 4.0 is needed by google-chrome-stable-22.0.1229.94-161065.i386
    libatk-1.0.so.0 is needed by google-chrome-stable-22.0.1229.94-161065.i386
    libc.so.6(GLIBC_2.11) is needed by google-chrome-stable-22.0.1229.94-161065.i386
    libcurl.so.4 is needed by google-chrome-stable-22.0.1229.94-161065.i386
    libgconf-2.so.4 is needed by google-chrome-stable-22.0.1229.94-161065.i386
    libnss3.so(NSS_3.12.3) is needed by google-chrome-stable-22.0.1229.94-161065.i386
    libbz2.so.1 is needed by google-chrome-stable-22.0.1229.94-161065.i386
    libXss.so.1 is needed by google-chrome-stable-22.0.1229.94-161065.i386
    libXcomposite.so.1 is needed by google-chrome-stable-22.0.1229.94-161065.i386
    libXfixes.so.3 is needed by google-chrome-stable-22.0.1229.94-161065.i386
    wget is needed by google-chrome-stable-22.0.1229.94-161065.i386
    xdg-utils is needed by google-chrome-stable-22.0.1229.94-161065.i386
    zlib is needed by google-chrome-stable-22.0.1229.94-161065.i386
    /bin/sh is needed by google-chrome-stable-22.0.1229.94-161065.i386
I like to test that. anyone can help me?

---

### Post by jerrrys on 2012-10-18
root@hamed-desktop:~# rpm -i Desktop/google-chrome-stable_current_i386.rpm
rpm: RPM should not be used directly install RPM packages, use Alien instead!

Use Alien  :)

[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

---

### Post by Cheesemill on 2012-10-18
Why are you trying to install RPM files in Ubuntu? Chrome is available as a .deb file.

RPM files are designed for Red Hat, not Ubuntu.
There is no way to add a RPM repository to a Ubuntu installation.

---

### Post by h66m9d on 2012-10-19
This is just for test!
=============
So why Ubuntu have to support yum/rpm?

---

