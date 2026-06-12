---
title: "Raspberry Pi 4 4GB, can't get ubuntu-desktop to work"
date: 2020-04-01
forum: Installation &amp; Upgrades
---

### Post by herqulees on 2020-04-01
I have a Raspberry Pi 4 4GB that I'm trying to install Ubuntu 19.10.1 on to, but no matter how many times I wipe the SD card, re-download the Ubuntu image, etc. it fails to start the desktop. Here is what I'm doing:
I download the 64bit (also tried 32bit) 19.10.1 image for the Pi 4 from [https://ubuntu.com/download/raspberry-pi](https://ubuntu.com/download/raspberry-pi)
I follow the directions from [https://ubuntu.com/tutorials/create-an-ubuntu-image-for-a-raspberry-pi-on-windows#1-overview](https://ubuntu.com/tutorials/create-an-ubuntu-image-for-a-raspberry-pi-on-windows#1-overview)
I un-zip the image from its .xz container using 7zip, then use Win32DiskImager to flash the image to my 128GB SD card (I've also tried Rufus and Belina Etcher, also tried an 8GB SD card)
I put the SD card in my Pi 4 and boot with ethernet connected, I wait ~5 minutes to let everything boot and calm down, log in with ubuntu ubuntu, change my password, sudo apt update, sudo apt upgrade, reboot, sudo apt install --no-install-recommends ubuntu-desktop. (I also tried without the --no-install-recommends, and tried with lubuntu-desktop)
Everything downloads and installs fine, there are no popups or anything and after about half an hour it is finished.
At this point I type startx and it fails, if I reboot I'm greeted with a blank screen with a blinking cursor, I can type but nothing happens. I've attached pictures of the screen for the failed startx, and the xorg log file.
What do I need to do to fix this?
[ATTACH=CONFIG]285361[/ATTACH][ATTACH=CONFIG]285362[/ATTACH][ATTACH=CONFIG]285363[/ATTACH]

---

### Post by mastablasta on 2020-04-02
what if you installed some display manager like GDM for ubuntu
```
sudo apt-get install gdm3
```

or LightDM for lubuntu
```
sudo apt-get install lightdm
```

There are others (SLiM, SDDM...) out there, but i am not sure how well they work with current versions of Ubuntu , Gnome, LXQT...

---

### Post by mxlinux99 on 2020-04-05
i don't think this distro has a gui included  

[https://www.youtube.com/watch?v=vzojwG7OB7c](https://www.youtube.com/watch?v=vzojwG7OB7c)

This video explains how to add Mate after the initial install. I was able to get it to work.

Good luck my friend.

---

