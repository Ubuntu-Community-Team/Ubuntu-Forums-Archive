---
title: "Was using ubuntu for 2 months, and now its gone?"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by heatmaka on 2008-11-07
its been a couple days now since, my computer froze on me, and when i did a reboot. it never would work. So i put my cd in, and i can only go on ubuntu threw the Cd. I can't install nothing!!!! it wont do it for me, and i cant do it manually, because there is not even one partition that shows up! It's a blank screen!! And when i try to do it automatically, it says "```
"no root file system is defined, please correct this from the partitioning menu"
```

And i have searched for hours, but i don't understand nothing!! What do i do? I'm thinking about giving up!

When i do a fdisk this is what shows up: ```
 ubuntu@ubuntu:~$ sudo fdisk

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)
  ...
```

And when i try to enter sudo fdisk -l nothing shows up ?!?! LOL


PLEASE SOMEONE HELP  THANKS

---

### Post by cariboo on 2008-11-07
Does your hard drive show up in the BIOS? It sounds like you have a defective hard drive. If you have access to another computer go to the hard drive manufacturers web site and down load the diagnostic tools for your hard drive, then run them. This will give you and indication of the health of your hard drive.

Jim

---

### Post by heatmaka on 2008-11-07
> **cariboo907 said:**
> Does your hard drive show up in the BIOS? It sounds like you have a defective hard drive. If you have access to another computer go to the hard drive manufacturers web site and down load the diagnostic tools for your hard drive, then run them. This will give you and indication of the health of your hard drive.

Jim

i dont have another computer, whats the code i could put in terminal to find out?

everything was working fine, and then i was trying to open a movie file, and BOOM! the screen stopped moving. I reboot, and this happens. But maybe i deleted the patitions my self, when i edited "sudo fdisk -l", because i was reading somewhere, that you delete all of them except one...and i tried that...and then the install still dint work...so i ran ubuntu with the cd, and deleted the last /dev/sda file that was in my fdisk.

I know it was a wrong move, but how can i fix this?

---

### Post by louieb on 2008-11-07
> **heatmaka said:**
> And when i try to enter sudo fdisk -l nothing shows up ?!?! LOL

Sure sounds like the hard drive has gone bad or the connector or power has come loose. 
Even if the drive were empty ```
sudo fdisk -l
``` (lowercase L) would still show the drive. 

> Does your hard drive show up in the BIOS?
...whats the code i could put in terminal to find out?
This is not something you do in a terminal window. Look carefully when the computer 1st boots most of the there is a message flash telling to press this key to enter setup. If no message then you'll need to find your computers user manual. Common key used are esc,  del, F1 and f12.

---

### Post by heatmaka on 2008-11-08
> **louieb said:**
> Sure sounds like the hard drive has gone bad or the connector or power has come loose. 
Even if the drive were empty ```
sudo fdisk -l
``` (lowercase L) would still show the drive. 


This is not something you do in a terminal window. Look carefully when the computer 1st boots most of the there is a message flash telling to press this key to enter setup. If no message then you'll need to find your computers user manual. Common key used are esc,  del, F1 and f12.

Nothing shows up when i enter "sudo fdisk -l".

And when i started and checked in bios it said: "Error 2100: HDDO (Hard disk drive) initialization error (1)"

---

### Post by baruch60610 on 2008-11-08
If you are able (and willing) to open your computer, I would check to see whether your drive is connected properly.  I would not recommend doing this unless you know what you're doing, especially not with a laptop.

When you turn on the computer, check to see whether the hard disk drive light turns on.  It should flicker, and you should hear the drive whirring as it turns, at least right at the beginning.  If you do not, then you may have a problem with the power to the hard drive, or possibly it has seriously died.

If the light flashes a little bit, then you know you've got power.  If you can hear the drive spinning, then you know it's at least doing that.  In that case, it could be a loose cable or broken wire in the data cable.  The data cable is usually a flat grey cable with many fine wires all together like a ribbon, going from the main circuit part of the computer (the 'motherboard') to the disk drive.

You can check to see whether this cable is frayed or somehow loose or disconnected.  If you replace it, that would eliminate any broken wire in the cable.

Other than that, you may want to consider getting a new disk drive for the computer.  That used to be very expensive, but now they're not all that bad.  Just make sure what you buy is compatible with your brand and model of computer.  Get your computer brand, model, model number, and any other information you can, and double check that the new drive would work in it.

Good luck.

---

### Post by heatmaka on 2008-11-08
I'm using a laptop! And i'm sure its not my hard drive, its i deleted my partitions today. It has to be that..

---

