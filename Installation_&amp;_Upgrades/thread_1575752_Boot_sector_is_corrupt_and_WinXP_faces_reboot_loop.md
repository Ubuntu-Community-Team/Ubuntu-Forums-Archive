---
title: "Boot sector is corrupt and WinXP faces reboot loop after trying to install Ubuntu"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by dtkr on 2010-09-16
Recently, I tried to help my friend install Ubuntu 10.04 side-by-side with Windows XP on his Acer Aspire One netbook.

Unfortunately, the installation process came to a standstill and it quit due to "unexpected errors". 

The second time I started the installation, I realized that the option for installing side by side was gone and that I could not mount the C:\ partition on Ubuntu. 

The error message is listed below:

====================BEGIN ERROR MESSAGE======================

Error mounting: mount exited with exit code 12: Failed to read last sector (299982847): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

===========================END ERROR MESSAGE==================

Thereafter, I quit the installation and rebooted into Windows XP. And the bar which indicates loading at boot time stops after going through one round and I get a BSOD following with a crash and then back to the BIOS. A picture of the boot splash with the "bar" is shown below if you didn't get what

[http://www.shoutmeloud.com/wp-content/uploads/2009/01/xp-boot-problem.jpg]("http://www.shoutmeloud.com/wp-content/uploads/2009/01/xp-boot-problem.jpg")

In short, I am stuck in a reboot loop. Is there any way to repair the boot sector? Any help would be greatly appreciated! ):P

---

### Post by lechien73 on 2010-09-16
It looks like a partition table problem, rather than a boot sector issue.

If you can boot in from a LiveCD/USB, could you run GParted and post a screenshot?

---

### Post by dtkr on 2010-09-16
> **lechien73 said:**
> It looks like a partition table problem, rather than a boot sector issue.

If you can boot in from a LiveCD/USB, could you run GParted and post a screenshot?

Oh, sorry I am currently away from the machine and unable to run GParted. Could you please explain how I can avoid causing partition related problems? And could you please explain what's the difference between a boot sector and partition table problem? 

Basically the installer refuses me the "install side-by-side" option, leaving me with either a total overwrite or manual specification. 

How can I avoid screwing my partition table or boot sector during Linux installations in general?

Thanks for your time (sorry for the barrage of questions),
Darren

---

### Post by aytech on 2010-09-16
Why dont you just create a separate partition for Ubuntu? I always installed it like that and never had problems. Then tell the Ubuntu installer to use the most available space. 
You can try fixing XP mbr, if that will work then restore the system and try to install Ubuntu again, this time I'd suggest to a separate partition ;)

---

### Post by dtkr on 2010-09-16
> **aytech said:**
> Why dont you just create a separate partition for Ubuntu? I always installed it like that and never had problems. Then tell the Ubuntu installer to use the most available space. 
You can try fixing XP mbr, if that will work then restore the system and try to install Ubuntu again, this time I'd suggest to a separate partition ;)

What do you mean by creating a new partition? Don't you have to resize the Windows partition when trying to create space for Ubuntu? How do you not screw the partition table?

---

### Post by aytech on 2010-09-16
> **dtkr said:**
> What do you mean by creating a new partition? Don't you have to resize the Windows partition when trying to create space for Ubuntu? How do you not screw the partition table?
 
Yes, I resize Win parition and create new logical disk. You can use Gparted for that. Then i login to Win for its boot file to recognize the new table, after that start Ubuntu install, tell it to use the "Largest available space". Dunno if thats the best technique, but it always worked fine for me ;)

---

### Post by dtkr on 2010-09-16
Ok, there are some new developments that you guys can look at. I took a screenshot of the GParted session which I just ran. Apparently, the partition table recognizes a size bigger than the specified and this is because I resized the partition without allowing Windows to recognize it. Screenshot is attached.

I cannot mount the device nor access it in anyway. Neither can I access Windows since the partition table is screwed up. I tried using the Windows Recovery Console but i got this: "... has not found any disks".

Is there any way to fix the partition table while keeping the data? Or salvaging the data? Please help as its quite urgent.

Thanks to the Ubuntu Community,
Darren

---

### Post by wilee-nilee on 2010-09-17
Give us a screen shot but use the select area to grab or put the picture time so the we can see gparted completely.

Also right click on that flagged NTFS and read the info I suspect it is telling you to run a chkdsk, let us know what it says.

---

### Post by dtkr on 2010-09-17
> **wilee-nilee said:**
> Give us a screen shot but use the select area to grab or put the picture time so the we can see gparted completely.

Also right click on that flagged NTFS and read the info I suspect it is telling you to run a chkdsk, let us know what it says.

Okay, there's yet another change in the situation. I've used ms-sys to write a new MBR as well as new partition info (using -p option) to the partition (/dev/sda2).

When I booted to XP, I got: "A disk read error occurred. Press Ctrl-Alt-Del to continue." So now its worst than before now. 

Can't get a screenshot cause the computer's not mine. But here's more info... ...

I tried to use the Recovery Console in the WIndows XP install disk but all I got was something like "Windows could not identify any disks".

Darren

---

