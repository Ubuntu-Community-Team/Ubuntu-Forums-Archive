---
title: "Updating problem Not Enough Space"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by queerfada on 2010-11-12
Hello,

Im trying to update and I keep getting a message that there is not enough space. I have deleted quite a lot of files and still not enough space

I checked my drives and this is what I have 

S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sda7              15G   13G  1,3G  91% /
varrun                502M  176K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   56K  501M   1% /dev
devshm                502M   12K  502M   1% /dev/shm
lrm                   502M   40M  462M   8% /lib/modules/2.6.24-28-386/volatile
/dev/sda5              32G  1,1G   31G   4% /data
/dev/sda2              20G   15G  4,8G  76% /media/sda2

Any idea what I can do?

for the record I also have windows (I only use it to update my iPhone) but mostly use Ubuntu

---

### Post by queerfada on 2010-11-12
I have cleaned more files and have 1.5 G free, still not enough!!!! How can I clean more files without affecting the system?

---

### Post by drs305 on 2010-11-12
Take a look at this thread, which discusses how to find and fix disk space problems:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

Make sure to empty your trash folders, and root's, and look for backups (like sbackup's) which may have backed up to the system partition instead of the backup partition.

---

### Post by queerfada on 2010-11-12
checked the link, and working with gparted to get more space, the problem is that apart from my fat32 drive, all other drives are locked (have a key icon next to them) and I can´t do anything with them.

I have deleted everything possible, and emptied the trash!

Do I have to change partitions from a live cd?

---

### Post by drs305 on 2010-11-12
To change the size of an Ubuntu system partition, it must be unmounted, so the use of the LiveCD or similar recovery CD/flash drive is normally necessary if using Gparted.

For non-system folders, it may depend on where they are. If a non-system logical partition has a higher number than the system partition, you may be able to unmount it (example: unmount sda7 if sda5 is / ). However, if you are trying to umount a lower partition, the higher logical partitions must be unmounted first (can't unmount sda5 until sda7 is umounted).

So the easy answer is yes, use the LiveCD. Even then, make sure the swap partition is unmounted by selecting it and choosing "Partition, swapoff" (if it's mounted and has a 'key' icon next to it in the lower pane).

---

### Post by queerfada on 2010-11-12
Thank you!

But I have very little experience to do all of this. So I´m considering just clean-installing Linux without any partitions (and losing Windows, I anyway never use it unless I´m working with my iPhone). Is there any way to do that simply? Or I have to join my partitions first and ra ra ra?

---

### Post by drs305 on 2010-11-12
> **queerfada said:**
> Thank you!

But I have very little experience to do all of this. So I´m considering just clean-installing Linux without any partitions (and losing Windows, I anyway never use it unless I´m working with my iPhone). Is there any way to do that simply? Or I have to join my partitions first and ra ra ra?

If you are sure you want to get rid of Windows, you can simple choose to use the entire disk when installing Ubuntu. 

Although I'm not a Windows user, I'd be inclined to keep it; perhaps shrinking it down to about 15% above it's current size (you can always convert it to a data partition at a later date). Use the rest for Ubuntu. 

If you want to shrink Windows, defrag it within Windows, run chckdsk /f, then resize it. I think Windows has it's own partitioning tool. You could then use Gparted to delete all the remaining partitions and during the install tell Ubuntu to use all the allocated space.

You might also want to just make the Ubuntu partition 10-15GB, and keep your data in either a separate /home partition or a separate data partition. I know you are probably looking for a simple solution, but thinking about these things now may prevent some regrets later on.

---

### Post by queerfada on 2010-11-12
you are amazing! Thank you! I will take your advice! I will start working on it!

Cheers mate

---

