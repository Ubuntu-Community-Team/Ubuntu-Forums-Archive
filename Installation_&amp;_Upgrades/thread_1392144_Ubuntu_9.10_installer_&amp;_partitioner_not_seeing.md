---
title: "Ubuntu 9.10 installer &amp; partitioner not seeing harddisk, but fdisk &amp; gparted see it!"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by duckdown on 2010-01-27
Hello.

I have a single SATA hard drive, not raided, with an XP partition on it.  /dev/sda.  I've already created an 18GB ext4 partition for Ubuntu and 2gb swap partition as well.

For some ridiculous reason the Ubuntu 9.10 isn't even showing /dev/sda as an option to install to!

fdisk -l clearly shows /dev/sda there, and i gparted /dev/sda works like a charm.  So why is the installer being so silly and not even allowing me to select it?  And I can't go back and choose manual mode or anything, the installer jumps right from Timezone Settins into this partitioner screen.

Here is a screenshot of fdisk -l clearly seeing the drive fine, yet the installer not showing it at all.

[img]http://farm5.static.flickr.com/4070/4310318232_456596c756_b.jpg[/img]

Please help!  This is one of the things that drives people away from Linux.. It never TELLS you what the problem is

---

### Post by darkod on 2010-01-27
Even though you are not using the disk in raid, it can have raid settings remains on it from earlier. 9.10 can detect these and gets confused whether you want raid or not. Try this:
First make sure there are no raid settings enabled in BIOS. Even with single disk, they can be trouble.
Then reboot into the live desktop again, and in terminal do:

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

Reboot and start the install process, see if it helped.

---

### Post by duckdown on 2010-01-28
> **darkod said:**
> Even though you are not using the disk in raid, it can have raid settings remains on it from earlier. 9.10 can detect these and gets confused whether you want raid or not. Try this:
First make sure there are no raid settings enabled in BIOS. Even with single disk, they can be trouble.
Then reboot into the live desktop again, and in terminal do:

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

Reboot and start the install process, see if it helped.

THANk you darkod!  I guess that did it?  I ran that command and it asked me to remove "nvidia" from the harddrive? (RAID?)  I have no idea, but I proceeded and upon trying again it finally sees the drive

Much thanks again!

cheers

---

