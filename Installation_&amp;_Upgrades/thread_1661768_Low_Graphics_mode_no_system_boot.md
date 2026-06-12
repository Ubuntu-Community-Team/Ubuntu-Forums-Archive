---
title: "Low Graphics mode no system boot"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by dmurphy787 on 2011-01-07
3 days ago Ubuntu 10.04 32 bit crashed for no known reason, when I rebooted the system reported "Low graphics mode" some options relating to the graphics file modification came up as a menu choice but as I am not experienced I did not modify this file. 
I decided to load Ubuntu via a cdrom in trial mode to retrieve my hard disk data and them try and install Ubuntu 10.10.  
On my attempt to install 10.10 the system, the system would load the splash install screen and when told to install it would go to a blank screen, no other disk movement or details.  I tried this a few times even trying to reinstall 10.04 with no joy.  I also had Debian on disk which was able to install.  As Debian had installed correctly I decided to try Ubuuntu again but the screen keeps going blank when asked to install.  I have also tried windows, Fedora 14 and debian again but the only system that loads now is Fedora.  I thought I could live with this but discovered that Fedora does not play music, videos or have wireless without much effort.
Sorry about all of these details but I am really stuck and want to share as much as possible to give someone the information they need to help me... please.  
Can anyone please help with regards to this probem as my system will not allow any other install and it is stuck on Fedora.

---

### Post by sikander3786 on 2011-01-07
Try reconfiguring your graphics.

Applications > Accessories > Terminal:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Note, capital "X" for X11.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Reboot.

---

