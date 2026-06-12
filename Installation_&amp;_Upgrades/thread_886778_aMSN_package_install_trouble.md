---
title: "aMSN package install trouble"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by ludeunlimited on 2008-08-11
I use aMSN becouse of the webcam support
but it stopped working a couple of days ago..
I've done some searching and found out I need to install the new version.

I uninstalled the previus version
I installed tcl/tk 8.4.16
Downloaded aMSN from their website, the tcl/tk 8.4 version

here comes the trouble, I get a error message when I use gDebi trying to install it:

"Could not open 'amsn-0.97.2-1.tcl84.x86.package'
the package might be corrupted or you are not allowed to open the file. Check the permissions of the file."

Is there a sudo command I can use to install it to get permission?
By the way I have Ubuntu 8.04 32 bit, but have exact same problem on my other computer with Ubuntu 8.04 64 bit.

Thanks in advance, Morten

---

### Post by Partyboi2 on 2008-08-13
open a terminal and change directory to where the deb package is, so if its on your Desktop type
```
cd ~/Desktop
```
then to install
```
sudo dpkg -i packagename
```
*Change packagename to whatever its called.

---

