---
title: "How to build libc6-2.28 and locales-all-2.28 deb files from source code?"
date: 2021-06-23
forum: Installation &amp; Upgrades
---

### Post by pilot8 on 2021-06-23
We're trying to build libc6-2.28 and locales-all-2.28 deb files from source code for armhf architecture on Ubuntu 18.04. We downloaded the source code from [https://ftp.gnu.org/gnu/glibc/glibc-2.28.tar.gz](https://ftp.gnu.org/gnu/glibc/glibc-2.28.tar.gz).


We used this command to generate the Makefile. Then we run "make" to build:
```
./configure --host=arm-linux-gnueabihf

```

Then we try to create libc6-2.28 deb file. But we found a lot of files not existing. For example, "libc-2.28.so" or "libc.so". What did we do wrong? We need these files before creating deb file.


For locales-all-2.28, it's the same thing. We downloaded "https://launchpad.net/ubuntu/+source/glibc/2.28-0ubuntu1/+build/15300581/+files/locales-all_2.28-0ubuntu1_armhf.deb" for comparison. For instance, in "locales-all_2.28-0ubuntu1_armhf/usr/lib/locale", there are folders like:
```
 aa_DJ/
 aa_DJ.utf8/
 aa_ER/
'aa_ER@saaho'/
 aa_ET/
 af_ZA/
 af_ZA.utf8/
 agr_PE/
 ak_GH/
. . .



```But in our build folder of libc6, those folders can't be found. How to build locales? We need these files before creating deb file.


Thanks in advance!

---

