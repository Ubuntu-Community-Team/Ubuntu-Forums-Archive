---
title: "2 Problems With Disks"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by mrhinman on 2007-11-28
Okay, here's the thing:  I have a 200GB SATA (the main drive) and a 30GB IDE (used for misc files).  The machine had XP Home, and I installed Dapper Drake server and erased the SATA.  The 30GB (NTFS) I was able to successfully copy the files from to a folder on the SATA drive.

First problem:  I get a blinking cursor at boot time.  Nothing happens until I hit a key, then it loads fine.

Second problem:  I can unmount the IDE drive and remove it from the system, but the system gives me a failure at boot time saying a system disk is not present... grrrr....

So I'm at a loss now.  I want to remove this extra drive but the system is not letting me.  I've double-checked that this drive is NTFS (since I had it mounted that way) and that no other partitions exist on it.

Ideas?

P.S. Go easy on me.  I'm a linux noob.

---

### Post by Pumalite on 2007-11-28
Make sure you disable it in BIOS first.

---

### Post by eggdeng on 2007-11-28
You need to post the output of```
 cat /etc/fstab
``` Post  the output of ```
sudo fdisk -l 
```for good measure.

---

### Post by mrhinman on 2007-11-28
Well I tried that, too.  It's really very strange.  Lemme try a few things.  Meanwhile, keep the ideas rolling in.

FSTAB:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
#/dev/hdc1      /windows        ntfs    nls=utf8,umask=0222     0       0
(notice I commented out the NTFS drive here)

FDISK:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23967   192514896   83  Linux
/dev/sda2           23968       24321     2843505    5  Extended
/dev/sda5           23968       24321     2843473+  82  Linux swap / Solaris

Disk /dev/hdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        3649    29310561    7  HPFS/NTFS

---

### Post by Toet on 2007-11-28
The master boot record is on the first disk in your system. By the sounds of it, it is the IDE drive. The bootloader is by default installed on the MBR of the first drive. It looks like there is something wrong there. Can you re-install grub, to see if that solves the problem?

---

### Post by mrhinman on 2007-11-28
> **Toet said:**
> The master boot record is on the first disk in your system. By the sounds of it, it is the IDE drive. The bootloader is by default installed on the MBR of the first drive. It looks like there is something wrong there. Can you re-install grub, to see if that solves the problem?

Well, yes I could.  A little guidance would help here, though.  Can I remove the HDD, then pop in the installation disk, and then..... ?

Is it an easy fix or do I lose everything I've worked on all day?

---

### Post by Toet on 2007-11-28
You could remove the disk from the case and do a re-install. That way, the sata disk is the first disk, and will contain the first MBR. But then do not put back any IDE disk in there, or that disk will be the first one again, leaving you with the same situation. You can also re-install grub, so it will use the 30gb disk.

Re-installing grub or re-setting it up, is something you have to google for, cause I do not know it by heart.

---

### Post by Toet on 2007-11-28
> **mrhinman said:**
> Is it an easy fix or do I lose everything I've worked on all day?

Re-setting grub up will not lose a thing. Re-installing the system will.

---

### Post by mrhinman on 2007-11-28
Okay, I managed to get to the "Reinstall GRUB" screen.  When selecting the correct drive, I get an "Error Code 20" and a failure.  Which is a "Multiboot" error.  When I installed Ubuntu, I asked it to ERASE the drive and install.

grrrrr...

---

