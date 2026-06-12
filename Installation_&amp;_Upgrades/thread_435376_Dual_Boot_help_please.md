---
title: "Dual Boot help please"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by Stink_Dude on 2007-05-06
Total newb question but... How can I get Ubuntu on my D:\ drive? I have Windows XP on my C:\ drive and I wanted to ask you guys how to do it before I tried. Thanks in advance!

---

### Post by Big Ed on 2007-05-06
It can be done:

[http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

Good luck,
Ed

---

### Post by Stink_Dude on 2007-05-06
Wow. I never expected it to be THIS complicated to put Ubuntu on an empty D:\ drive! That's not going to stop me from (probably) being the first 12-year-old to single-handedly dual boot though!

EDIT: wait, does Dual Boot mean both OS's are on the SAME drive? 'cause if so, i guess im not actually trying to DUAL boot at all! i hope not, cause then i would feel like an idiot.:(

---

### Post by Big Ed on 2007-05-06
It's really not that hard.  The Ubuntu installer will do most of the work for you.  But you have to know if your D: drive is on the same physical drive as Windows, but on a separate partition.  Or if it's on a separate physical drive.

You might want to boot straight into Ubuntu, using the cd as a live cd.  That will give you the opportunity to explore your drive/partition geometry without having to risk altering the partition table.

Open a terminal and run 'sudo fdisk -l' to see what drives and partitions you have.

HTH,
Ed

---

### Post by Stink_Dude on 2007-05-06
Once again, THANKS!!!!!:)

P. S. When I boot from CD will it give me an installer menu (like an most exe's in Windows) or will Ubuntu just start? sry in advance 4 my extreme n00bishness.

---

### Post by Big Ed on 2007-05-06
> **Stink_Dude said:**
> EDIT: wait, does Dual Boot mean both OS's are on the SAME drive? 'cause if so, i guess im not actually trying to DUAL boot at all! i hope not, cause then i would feel like an idiot.

Yep, you'll be dual-booting.  You can have the windows and linux partition on the same drive or on different ones.  Doesn't really matter.  Linux (from an fdisk point of view) calls a physical drive a drive.  Windows calls a formatted partition a drive.

Ed

---

### Post by Stink_Dude on 2007-05-07
I tried to install it on my D:\ drive (which turned out to be a partion, like you said) and it gave me the message "No Root File System defined." Help please!

---

### Post by confused57 on 2007-05-07
> **Stink_Dude said:**
> I tried to install it on my D:\ drive (which turned out to be a partion, like you said) and it gave me the message "No Root File System defined." Help please!
If you're sure that you designated a root partition, then you may be seeing this bug:
[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)

---

### Post by Big Ed on 2007-05-07
You have to install to a blank partition.  No windows filesystem on it.  You will also need another small partition for swap, about one to two times the size of your computer's physical memory.  So make sure you have saved anything you want to keep off your D: drive before you do this.  In the partition menu of the install, you will have to _delete_ the partition where D: resides under windows.  Be very, very sure you get the correct partition, because if you delete C:, your windows (and all your data) is gone.  Permanently.

So assuming you have one IDE drive and C: is hda1, D: is hda2 (for one sata - sda1 and sda2):  

1.  You will delete hda2. 
2.  Create new primary partition hda2 of , say, one GB, set it as swap.
3.  Create new primary partition hda3, set as ext3, mount on / (root)
4.  Create any other partitions you need.  (Note that you can have only four primary partition, so if you want more then create an extended partition and put logical drives within it.  The extended partition counts as a primary one.)  Many (most) people have a separate partition for /home.

DO NOT take these partition numbers as gospel.  Check your system first to see where C: sits BEFORE deleting any partitions.

Also, just in case you have a second drive, IDE disks are hda, hdb, hdc, etc.  Sata disks are sda, sdb, sdc, etc.  Partitions on them will be hda1, hda1, hdb1, hdb2, sda1, sda2, etc.  The Partition Howto has lots of good info:  [http://www.tldp.org/HOWTO/Partition/index.html](http://www.tldp.org/HOWTO/Partition/index.html)  It's not new, but partitions haven't changed much lately.

HTH,
Ed

---

### Post by Stink_Dude on 2007-05-08
Fatal Error. I've given up.

---

### Post by Big Ed on 2007-05-08
> **Stink_Dude said:**
> Fatal Error. I've given up.

Don't give up.  There's a bit of a learning curve to Linux, but it's very much worth the effort.  Try doing a re-install and make a note of your choices when offered various options.  As long as you're careful around your windows partition, you can't do any harm.  The other thing you could try is (dare I mention this on an Ubuntu forum?) Fedora.  It's a Redhat based distribution that is also quite good.

[http://fedoraproject.org/wiki/](http://fedoraproject.org/wiki/)

Ed

---

