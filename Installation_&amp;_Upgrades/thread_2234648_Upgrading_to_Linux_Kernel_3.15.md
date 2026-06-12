---
title: "Upgrading to Linux Kernel 3.15"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by terrykiwi83 on 2014-07-15
Just looking for some advice.

I am running 14.04 x64 and would like to upgrade the kernel to the latest stable version of 3.15, however I am just looking to see if anybody else has done this and been successful. If you have could you share with me how you did it.

Thanks.

---

### Post by terrykiwi83 on 2014-07-15
Forgot to mention, my current kernel version is:

> 
Linux POSEIDON 3.14.0-031400rc4-generic #201402232235 SMP Mon Feb 24 03:36:35 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


---

### Post by terrykiwi83 on 2014-07-15
Solved it myself after a bit of research.

Here is what I did to upgrade to the Latest Kernel 3.15.5. The upgrade was a success with no bugs.

> 
sudo apt-get update
sudo apt-get install python-bs4
cd /tmp
rm -rf medigeek-kmp*
wget --no-check-certificate [https://github.com/medigeek/kmp-downloader/tarball/master](https://github.com/medigeek/kmp-downloader/tarball/master) -O kmpd.tar.gz
tar xzf kmpd.tar.gz
cd medigeek-*
python kmpd.py -d


---

