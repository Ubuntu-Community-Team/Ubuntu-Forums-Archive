---
title: "bionic beaver minimal server: how to preseed for totally unattended install"
date: 2019-02-24
forum: Installation &amp; Upgrades
---

### Post by denis-beurive on 2019-02-24
Hello,

I've tried to build a custom ISO file for _*Ubuntu Bionic Beaver minimal server*_.

My goal is to make an ISO file for a totally unattended installation process.

I've found many documents that describe different procedures. For example:


[LIST]
[*][https://askubuntu.com/questions/806820/how-do-i-create-a-completely-unattended-install-of-ubuntu-desktop-16-04-1-lts](https://askubuntu.com/questions/806820/how-do-i-create-a-completely-unattended-install-of-ubuntu-desktop-16-04-1-lts)
[*][https://ubuntuforums.org/showthread.php?t=2390710](https://ubuntuforums.org/showthread.php?t=2390710) (??? I am lost...)
[*][https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)
[/LIST]

However, none of these procedures seems to work. It may be normal since some of the procedures apply to other image versions. The directory tree of the image "[FONT=courier new]mini.iso[/FONT]" does not match the given descriptions. I tried many things (*without knowing exactly what I am doing... I admit*).

Is there a documentation that presents the exact procedure to follow in order to generate a custom ISO file, specifically for Ubuntu Bionic Beaver minimal server ?

Thanks,

Denis

---

### Post by denis-beurive on 2019-02-25
For information, I reached my goal with Debian Stretch Minimal.


I give the procedure on this link:


[https://github.com/denis-beurive/preseed-stretch](https://github.com/denis-beurive/preseed-stretch)

   Note   : I have the impression that the installer used by Ubuntu is not exactly the same as the one used by Debian.

---

