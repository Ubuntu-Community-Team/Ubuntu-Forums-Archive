---
title: "Display problem"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by arnarg on 2012-02-03
Hi.
I'm somewhat experienced with Ubuntu (I have had it installed on my laptop for a while) however, I'm having a problem with installing it on my desktop machine. The installation is successful, however when I boot it I only see orange (the base color of the default wallpaper) screen except for the top 10-ish pixels, there I can see a part of the mouse when I move it to the top. I then pressed Ctrl+Alt+F1 to reboot it but nothing appears on the screen so I just entered my user and password blindly and then "sudo reboot" following with my password again and it rebooted, so it's functioning it just doesn't display anything.
Does anyone have an idea what could be the problem? something to do with display drivers maybe?
I installed it from an usb thumb drive which I made bootable with "Make startup disk" in my laptop, and used an Ubuntu 11.10 amd64 iso image from ubuntu.com.
Computer pecs:
Amd Phenom II X6 1090T Black Edition
Sapphire Radeon HD 6850
MSI 870A-G54 mainboard
16GB ram

Help would be much appreciated.
Thanks.

Edit: I installed on ext2 partition if that matters.

---

### Post by arnarg on 2012-02-04
bump

---

### Post by arnarg on 2013-02-06
I know this post is just over a year old but I decided to try installing Ubuntu again. I downloaded an 12.04.1 64-bit image and put it on a usb stick using dd on my laptop (which is running Pear Linux 6). The liveCD worked without problems but when I install the OS and reboot the same problem occurs. It's weird because I can install Pear Linux on this machine without problems and it's based on Ubuntu 12.04. 
I recorded a video of the problem: [http://youtu.be/KVpa2xenzNU](http://youtu.be/KVpa2xenzNU)

Thanks.

---

### Post by dino99 on 2013-02-06
you need to know whats wrong while booting. So remove "quiet splash" from the boot line, to get the verbose mode. You also can try the recovery mode, then watch for errors logged into /var/log/xorg.0.log & into ./xsession-errors

---

### Post by arnarg on 2013-02-06
> **dino99 said:**
> you need to know whats wrong while booting. So remove "quiet splash" from the boot line, to get the verbose mode. You also can try the recovery mode, then watch for errors logged into /var/log/xorg.0.log & into ./xsession-errors

Thanks for your reply. Luckily it kind of magically fixed itself this time :D I made a Pear Linux LiveUSB and selected it from the bootup menu but instead it went straight to the Grub loader and from there booted Ubuntu successfully. For future reference, how do I edit the boot line?

---

