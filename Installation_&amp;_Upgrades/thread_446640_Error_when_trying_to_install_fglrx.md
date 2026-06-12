---
title: "Error when trying to install fglrx"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by kingbabi on 2007-05-17
I'm running Feisty Fawn and I've been having errors with my video card. (ATI X1300), I've been following [this tutorial]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") and when I come to the part where I'm supposed get the .deb packages
> sudo dpkg -i xorg-driver-fglrx_8.36.5-1*.deb
sudo dpkg -i fglrx-kernel-source_8.36.5-1*.deb
sudo dpkg -i fglrx-amdcccle_8.36.5-1*.deb
I tried to run each of these commands, and I keep getting the same (varying slightly based on the command) error:
```
hoyle@Dr-Computer-Ubuntu:~$ sudo dpkg -i fglrx-amdcccle_8.36.5-1*.deb
dpkg: error processing fglrx-amdcccle_8.36.5-1*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fglrx-amdcccle_8.36.5-1*.deb
```
I'd appreciate your help!

---

