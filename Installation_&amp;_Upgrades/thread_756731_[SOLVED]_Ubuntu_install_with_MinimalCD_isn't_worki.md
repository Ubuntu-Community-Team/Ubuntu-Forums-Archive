---
title: "[SOLVED] Ubuntu install with MinimalCD isn't working!"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by mark0495 on 2008-04-16
Hello everybody,

I want to install Ubuntu 7.10, so I burned a Desktop CD. When I runned it and selected "Run or Install Ubuntu 7.10", it stucked with the terminal; exactly with the line "Preparing restricted drivers". Then I tried out the MinimalCD; this should download all the files from the internet. I first chose the names etc, and then I chose ubuntu-desktop. I did go away from the computer and waited untill the installation was ready. I rebooted the system and there it booted, but there was no loading screen, and after that, it didn't start the desktop, but a terminal. For now, I'll try to install my working Kubuntu 7.10 CD, but I really want to install Ubuntu. Anyone ideas?

Can anybody help me, please?
Mark0495

---

### Post by dstew on 2008-04-16
> Then I tried out the MinimalCDI have never heard of this. Do you mean the Server edition, or the Alternate Install CD? If you install a minimal (base or server) edition of Ubuntu, you do not get the desktop, only a command-line interface. If you have a working server installation, and internet access, you can install the ubuntu desktop by entering this command on the command line:```
sudo apt-get install ubuntu-desktop
```It takes about an hour to download and install the packages at DSL speed. Once the installation process is finished, enter```
startx
```and you should get a regular Ubuntu desktop.

---

### Post by mark0495 on 2008-04-16
Thank you very much for helping me out, dstew! This Ubuntu 7.10 is working very nice now.    
For the ones who don't know what a MinimalCD is; it's a kind of Boot CD, which isn't very big. It's completely text-based and it uses apt to get all the needed packages via the internet. But I've experienced it isn't working properly, and I'm not going to do it again when I want to install Ubuntu on another PC. For the people who really really really want to know about this MinimalCD, more information is available on this site: [https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")
I'll say it once again; thanks for helping me out, dstew! This problem is SOLVED now!

Mark0495

---

