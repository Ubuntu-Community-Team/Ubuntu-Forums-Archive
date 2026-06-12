---
title: "Select package version with apt get installation"
date: 2017-01-19
forum: Installation &amp; Upgrades
---

### Post by itanon on 2017-01-19
Hi!
 As in the title I'll need to download and install a package via "apt-get install" command but need to specify the version, here's the question:
I need to install the Nvidia cuda toolkit package.
If I issue "apt-get install Nvidia toolkit" it install the last version of this package(version 8)....I need the 6.5... There's a way to specify the version I want when performing apt-get command ?..... I've tried "apt-get install Nvidia toolkit-6.5" but nothing .....Any suggestions about it?
P.s. I'm a newbie so be patience
Thanks!

---

### Post by ian-weisser on 2017-01-19
Which release of Ubuntu? 12.04? 14.04? 16.04? 16.10?
Why 6.5 instead of 8?

---

### Post by mc4man on 2017-01-19
apt-cache madison packagename will show you all available versions of 'packagename'  though in this case it'll be just one, for 16.10 the 8.x version.
6.5.x was only in 15.04, see - [https://launchpad.net/ubuntu/+source/nvidia-cuda-toolkit](https://launchpad.net/ubuntu/+source/nvidia-cuda-toolkit) 
That package depends directly on 3 other same source/version packages & likely some others that may or may not  be specific to 15.04. So you may want to look for some other method than ubuntu packages

(- though you could try getting all the relevant nvidia-cuda-toolkit packages from 15.04 in launchpad & use apt (not apt-get) on all at once. Or dpkg & then fix broken.. Probably won't be fatal if it all fails, just would require some cleanup.

---

### Post by itanon on 2017-01-19
I need CUDA toolkit 6.5 because my GPU's driver ( gtx 330m) only supports that version

---

