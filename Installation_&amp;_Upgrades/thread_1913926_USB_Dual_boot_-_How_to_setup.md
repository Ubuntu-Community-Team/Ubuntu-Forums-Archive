---
title: "USB Dual boot - How to setup"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by airscrew on 2012-01-23
Hi to all,

Newbie to Ubuntu here.
Installed 11.10 on my sons laptop when windows died. 
No probs, and he loves it.

How do I install Ubuntu as a dual-boot for my desktop.??
I am most of the way through it, but I need to know how/where to install grub.
I have scoured this forum, and gone as far as I can with the install, as none of the discussions exactly fits my requirement.

NB. I use it partly as a homeoffice desktop, and I do NOT want to touch the C: drive at all. Although I have an XP disk, it would take AGES to rebuild a 5 year old image...if it aint broken...you know the rest.

Disk/boot config is:

drive 0(a): NTFS 250Gb
C: windows XP SP3 and old progs - 50Gb
D: all data and new progs since I repartitioned and set a weekly D: backup regime - 200Gb

drive 1(b): USB drive 500Gb NTFS
recently changed partitions (gpart) to
W: (as windows sees it)  1st partition. Gpart sees free space 250Gb with 11.10 installed, but NOT bootable YET
X: 100Gb data backup for D:
Z: 50Gb Windows image backup (used DriveImageXML) I DO NOT WANT TO LOOSE THIS IMAGE, and dont have another drive

11.10 installed OK, good iso and chksum, but not bootable


OK, so here is the question.
IDEALLY, I would like to boot into Ubuntu if/when the USB drive is powered.
Heres my thinking.
Bios is <now> set to boot first to CD, then to USB drive (currently no MBR or grub), then to drive 0 normal XP.
If no CD and no USB, it will autoboot to XP.
This works in BIOS. 
OK sofar.

Qs. 
So will this work if grub is installed as Ubuntu only (not dual), and sitting on the USB drive?
Will I have to disconnect (cables) the XP drive to force grub to install onto the USB drive? (i would prefer to do this to ensure I do not touch the XP drive)
Will this cause a drive conflict after I reconnect the XP drive?
Will Ubuntu be able to fully access the data on D:?

NB.
I would strongly prefer to do this totally with the XP drive disconnected.
I would really prefer this to happen during the install process.
I dont want to have to do a load of terminal script post install. I will get it wrong!!
Also, I expect to have re-do the install process, and enticipate reducing the freespace for Ubuntu down from 250Gb to (say) 25B, and free/keep more space for backups in another partition.

Thanks for any and all advice.
Jai.

---

### Post by oldfred on 2012-01-24
Please do not post duplicate threads. We are volunteers here and you require us to do double work.

[http://ubuntuforums.org/showthread.php?t=1913946](http://ubuntuforums.org/showthread.php?t=1913946)

Thread closed.

---

