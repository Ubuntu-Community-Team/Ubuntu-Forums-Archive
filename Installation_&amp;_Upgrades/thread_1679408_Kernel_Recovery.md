---
title: "Kernel Recovery"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by skr13 on 2011-02-01
Hi,

I run Ubuntu Karmic(kernel 2.6.31-22) on an i386 machine. I was compiling the kernel and halfway through I realised that I did not have the required disk space and the compilation failed with the error - No available space. After I restarted my box, I can't log-in. I used KDE but I don't see KDE at the login screen anymore. I get the following pop at the top right of the screen: "Install problem! The configuration defaults for gnome power manager have not been installed correctly. Please contact computer administrator"

I have 5 different kernel(1 custom) and all of them show the same thing. I tried the recovery mode in vain. 

I would really appreciate any help in fixing this without having to install ubuntu from scratch (I have more than 2 years of work at risk :( .) Is it possible to compile and install the latest kernel from the recovery mode? 

Thanks in advance

---

### Post by skr13 on 2011-02-01
Hi,

I was able to reinstall the latest kernel through the recovery mode. Once in the recovery mode(with networking enabled), I did:

[FONT="Courier New"]
dpkg --configure -a

apt-get update
apt-get dist-upgrade
[/FONT]

Everything was same as before except for the desktop wallpaper.

Hope this helps someone having similar problem.

Cheers
skr

---

