---
title: "benq e2200hd &amp; Geforce"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by johnthomson on 2010-01-20
Hello, I am trying to install Ubuntu on my Compaq sr5220an
desktop with integrated nvidia geforce 6150 and benq e2200hd monitor. Whatever I do I end up with a black screen. I have tried with 8.10 9.04, 9.10, lucid & debian. All work fine with my old crt monitor. I have installed nvidia-glx (173&185) via text mode,
but no difference. There was originally no xorg.conf, I made one with dpkg, but made no difference. Now I am running Fedora, which is fine, but not what I want to do. Anyone have any idea what to try next ?

many thanks, john

---

### Post by johnthomson on 2010-01-23
Hello, to follow up my own post in case it helps someone.
It seems there is an incompatibility between Ubuntu versions
and Nvidia 6150 combined with Benq e2200hd (1920*1080).
I solved the matter, after a lot of trouble, by using Fedora 12
to download Nvidia drivers "NVIDIA-Linux-x86-190.53-pkg1.run"
copying them to Ubuntu root. Then login to Ubuntu in recovery mode,
and "telinit 3", then sh "NVIDIA........".

---

