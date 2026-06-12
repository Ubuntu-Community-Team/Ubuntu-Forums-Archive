---
title: "disk partitioner problems with Feisty"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by Franscisco on 2007-05-10
Does anyone know why I can't install Feisty, there are seven questions when installing, but when being asked **how I would like to partition the disk**(Fourth questions) it says **starting disk partitioner**, then, **manual** and click next and there is an empty screen that says I need to specify the partition from the root file system (mount point/*/)

---

### Post by 67GTA on 2007-05-10
Have you created a partition for Feisty?

---

### Post by Franscisco on 2007-05-10
Sorry I am new to Linux and I am learning this thing. I really would love to know how to create a partition for Feisty. Thanks

---

### Post by 67GTA on 2007-05-10
If you have another operating system already installed then just choose to let the installer resize the existing partition and install itself. If the hard drive is empty then choose to erase the entire hard drive and letit install itself. Here is a link with more info on installing. Look at the left menu for the partition sections. Just ask if you need more help.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Franscisco on 2007-05-10
Thank you for your time, but I have these questions.

I have XP pro installed, so the partition is 234 of hard disk which means I am using the whole hard drive. You meant inserting the live cd from the BIOS, so when getting to the desktop I followed the steps until there is the Partitioner, from there you meant I can resize the current partition where xp is.

---

### Post by 67GTA on 2007-05-11
Set your bios to be able to boot from cd, click the install icon on the desktop once it is loaded. The install cd will resize your XP partition and install ubuntu in the empty space. Just get to the installer and choose the option to "resize and use free space". >It will leave your XP partition, just resize it for you. The only trouble you may have is that grub (common linux bootloader) will take over your master boot record. Sometimes Windows is not detected and you can't initially boot into windows. If this happens, just post back and someone can help you with that.

---

