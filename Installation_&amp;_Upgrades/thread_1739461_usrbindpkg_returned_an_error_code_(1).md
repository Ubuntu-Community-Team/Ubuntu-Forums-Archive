---
title: "/usr/bin/dpkg returned an error code (1)"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by unimous on 2011-04-26
I don't know why, but every time i try to apt-get install something, the same error happens, just like this:

```
**$ sudo apt-get install gcc**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? **Y**
Setting up medibuntu-keyring (2008.04.20) ...
gpg: symbol lookup error: /usr/local/lib/libreadline.so.6: undefined symbol: PC
dpkg: error processing medibuntu-keyring (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 medibuntu-keyring
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dino99 on 2011-04-26
follow this howto:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

clean the sources:

sudo rm /var/cache/apt/archives/*  (ignore the error output)

then update

---

