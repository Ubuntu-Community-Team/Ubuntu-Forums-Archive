---
title: "Ubuntu 7.10 Installation Failure"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by Budly on 2007-11-19
When I boot from the Live CD the initial, a first screen comes up and I choose the first option to install Ubuntu. The installation starts. After a minute or so the screen characters become totally corrupted in that they become incoherent short lines at semi-random places across my screen.  After another few minutes the screen goes blank and the installation apparently stops completely. But, it is hard at this point to determine what is going on since the installation procedure is giving me no information to work with. Finally I have to reboot to get anything to work but I have no Ubuntu installed. 

Installation seems to be failing but it is really hard to tell what is going on. WHAT is happening when the funny incoherent characters start to show up?

I am running a Pentium 4 with 1 GB of RAM. There is really nothing unusual in my hardware as far as I can tell.  I downloaded (twice!) the Live CD installation image and burned it correctly on a blank CD. I checked the MD5 Sum by the way and it was correct. I use a boot manager (LILO) with Windows 2000 Pro and Mandrake Linux installed and bootable.

---

### Post by taurus on 2007-11-19
Try the alternate CD.

---

### Post by waffen on 2007-11-19
Uhm... I receipt some similar errors... try to burn the CD with Minimum speed (4x-8x)...

---

### Post by Budly on 2007-11-19
To answer some of the interest above: 

I have burned 2 CDs at different times and I do use very slow speeds to burn the CDs. I learned that lesson a long time ago. I also used the Check CD for Errors option and that came back clean as well.

Another thing that I was wondering is could this be related to my video card? I have the Matrox Millennium P750 with 64MB of on-chip RAM. Is Ubuntu misunderstanding what my card is so that it makes an incorrect decision about upgrading to higher resolution during the initial installation?  

I am now downloading and burning the alternate CD image. But, it is not really clear from the Ubuntu web site information just exactly what circumstances the alternate CD is meant to handle. This could be better documented.
 
Thanks for the answers so far!

---

### Post by ChronoSphere on 2007-11-19
I have a similar problem. I installed from the alternate CD, it installs just fine, but when I restart I get all the way to the login screen and the screen becomes garbled and unreadable.

---

### Post by taurus on 2007-11-19
> **ChronoSphere said:**
> I have a similar problem. I installed from the alternate CD, it installs just fine, but when I restart I get all the way to the login screen and the screen becomes garbled and unreadable.

Press <Ctrl><Alt>F2 and log in with your username and password.  Then, reconfigure X again with

```
sudo dpkg-reconfigure xserver-xorg
```
When you are done, get back to the GUI login screen again with <Alt>F7.  Now, restart X with <Ctrl><Alt>Backspace.

---

### Post by Budly on 2007-11-19
OK. The alternate CD did the trick! I am still not sure what the difficulty was but it is now gone so I can get on to other more productive issues. Thanks to all who looked at my post. 
I now have a productive fully updated Ubuntu 7.10 installed!

---

