---
title: "Display resolution problem with Ubuntu 10.04 and Asus EeePC 1101"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by jaibris on 2010-05-15
This small laptop comes with Win 7 Home and display resolution 1366x768. I have done a clean install of ubuntu netbook remix 10.04, and everything work well, except the display driver. I got wrong resolution and terrible speed of the display. Is it anyone out there who can help me?:confused:

---

### Post by justsee on 2010-05-15
Hi Jaibris,
I had similar issues getting my 1366x768 TV display working, detailed here: [http://ubuntuforums.org/showthread.php?t=1480033](http://ubuntuforums.org/showthread.php?t=1480033).

I'd suspect you need to take a similar approach to creating a custom modeline to use in your xorg.conf file.

cheers,
justin

---

### Post by kansasnoob on 2010-05-15
I've never had a EEE but I prefer these two methods for creating a new mode:

[http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/](http://www.linuxreaders.com/2009/11/04/change-ubuntu-9-10-resolution/)

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Note: The first of those does not change the login screen resolution, but the second one does. However the second one does not work with auto-login.

I have tried using both together with the regular Gnome desktop and it's fine.

---

### Post by t2491tom on 2010-08-01
I was having a similar problem on my laptop and I just accidentally fixed it today. I was browsing through the software store and saw a program called xresprobe or X Resolution Probe. I figured why not try it maybe it will fix my problem. So I installed it and restarted my computer to see if it would work and it did! It now correctly automatically sets my resolution! I should note that my problem was getting it to set the resolution correctly with the monitor I use (because my laptop screen is broken).

---

### Post by mellowb on 2010-10-16
I had the same problem with my asus and it was fixed after I installed the drivers from video card poulsbo. Check the link [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

---

### Post by guggikofod on 2011-04-19
Hi,

I have just installed Ubuntu 10.10 on Asus EEEpc 1101HA, dual-booting with win7.

I had the typical problems with screen resolution, with only one offered, 1024x768.

After some horsing around (I am a semi-novice user), I found the following to solve my problems (on this page : [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)  )

basically, I carried out the following commands, one by one (taken from the indicated page):

sudo apt-get update
sudo apt-get purge psb-kernel-source
sudo apt-get upgrade
sudo apt-get install psb-kernel-source
sudo apt-get install poulsbo-driver-2d poulsbo-driver-3d poulsbo-config


after re-booting, everything looked beautiful. Thanks to everyone!

---

