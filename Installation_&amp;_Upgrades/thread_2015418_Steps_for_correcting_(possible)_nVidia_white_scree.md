---
title: "Steps for correcting (possible) nVidia white screen error"
date: 2012-07-03
forum: Installation &amp; Upgrades
---

### Post by lookyhere on 2012-07-03
Hi, 

I'm pretty new with Ubuntu so please bear with me but I just wanted to check that I have the steps right for correcting what I think is a problem with my on board nVidia graphics card causing the dreaded white screen of death (which come up after about 5 minutes of use). I've formatted the drive using the ubuntu installer and I'm trying to use the x64 version of 12.04. 

1) Turn on pc (when installing I chose to by pass login so it goes straight to the desktop).
2) Switch from the desktop to terminal with Ctrl+Alt+T
3) Run the following in terminal to get the latest drivers:
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current -f
```
4) Restart the computer and hope for the best.

Could someone verify that this is the right approach?

Once I've fixed that, I'll look at the fact that without the usb stick in the machine that had the installation iso on, I get a blank black screen with a flashing cursor. I'm hoping that [this post]("http://ubuntuforums.org/showthread.php?t=1743535") will help me with that though.

---

### Post by dino99 on 2012-07-03
yes should do the trick, but before, do:

sudo rm /etc/X11/xorg.conf
sudo apt-get purge nvidia-current
sudo apt-get install nvidia-current

then cross fingers ):P

at the end: sudo shutdown -R now

---

### Post by lookyhere on 2012-07-03
Cheers Dino. I thought there was something I had to do to make sure the current driver had been removed completely before updating. I'll update this post when I've given it a go. Wish me luck! :-k

---

