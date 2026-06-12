---
title: "(novice) Nvidia driver ERROR- You appear to be running an XServer..."
date: 2017-04-15
forum: Installation &amp; Upgrades
---

### Post by ubuntini2 on 2017-04-15
So I've followed these directions here
[https://ubuntuforums.org/showthread.php?t=1916961](https://ubuntuforums.org/showthread.php?t=1916961)

but when I enter 
```
sudo service lightdm stop
```

my screen goes completely blank(black) and I am unable to proceed.


Anyone able to help?

Running Ubuntu 16.04
Linux version 4.4.0-66-generic (buildd@lgw01-28) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.4)

---

### Post by mooreted on 2017-04-15
That post is from 2012. 

For optimal performance of your Nvidia graphics card, or your Broadcom wireless card, you'll want to install the closed source restricted driver (the proprietary non-free driver). Like this:

Menu button - System Tools - Software Updater

Click Settings... and then click the tab Additional Drivers

When available for your system, you'll be shown one or more installable non-free drivers. Select them.

The required drivers are then automatically downloaded from the internet, from the software repositories of Lubuntu, and (also automatically) installed. Afterwards you will have to do a full reboot of your computer.

Note: Sometimes you're being offered several versions of the restricted driver for your video card. The order of preference is as follows:

1. nvidia-(from highest number to lowest number)
2. nvidia-(from highest number to lowest number)-updates
3. nvidia-experimental

Only choose from the versions that you're being offered, because only those support your video card! Start with the preferred number one, and only work your way down when it doesn't perform well.

---

