---
title: "What the command in Ubuntu LTS for installing nvidia drivers"
date: 2017-08-19
forum: Installation &amp; Upgrades
---

### Post by eze88 on 2017-08-19
After i successfully mount it from usb device. 

Pls do not ask me to update as my network do not have a internet connection

---

### Post by vocx on 2017-08-19
> **eze88 said:**
> After i successfully mount it from usb device. 

Pls do not ask me to update as my network do not have a internet connection
I'm sorry, your post doesn't make much sense. Can you again explain what you want? Your title says "nvidia drivers", but your post say "mount from USB device". You mounted what? For what?

---

### Post by eze88 on 2017-08-19
Apologise, what i mean is i save Nvidia diag driver Deb file on a usb thumb drive

Next i did a sudo fdisk -l to look for the usb thumb drive and i'm able to see /dev/sb1 which is the usb thumb drive containing the nvidia deb file

But i'm clueless how do i install the deb files from /dev/sb1 as in what the command i could execute to run the installation

---

### Post by ajgreeny on 2017-08-19
You will need to know the mountpoint of USB drive and can then try ```
sudo dpkg -i /media/*USB*/*.deb
``` (change USB to whatever your system mountpoint is) but never having used an nvidia driver I have no idea whether or not there are dependencies needed to allow this installation.

Unfortunately, dpkg does not handle dependencies, but it should tell you what extra packages are needed in error messages, which you will then need to download separately, add to the USB and run the command again.

---

