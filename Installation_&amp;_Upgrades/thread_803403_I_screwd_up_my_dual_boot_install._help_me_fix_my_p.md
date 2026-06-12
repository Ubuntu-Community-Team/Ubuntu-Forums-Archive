---
title: "I screwd up my dual boot install. help me fix my partition"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by gingk0 on 2008-05-22
I was installing ubuntu along side vista. 

I have 2 hard drives. 

I used partition editor to make some room on my 2nd hard drive and I installed ubuntu. I created a 35Gb empty partition and a 4gb swap file partition. I also see the boot loader to boot off of the 2nd disk.

After I rebooted it went straight to  vista. I see my 2nd drive but when I click on it is asks if I want to format it. 
IN disk manager I see the drive is 0 bytes and it's full. 
I have 145gb of data on that 280gb partition.

Now when I boot to the ubuntu cd and run GParted I see 
/dev/sdb1 (triangle with an exclamation) ntfs 258gb. --- ---
/dev/sdb3 (keys) linux-swap 3.15 GB --- ---
/dev/sdb2            ext2  36.6 Gb  2.52GB used   33.85Gb unused.

When I click on information for /dev/sb1 (triangle with an exclamation).
It  says "failed to startup volume: invalid argument. Failed to mount. The device '/dev/sdb1' doesn't  have a valid NTFS. Maybe you selected the wrong device? Or the whole disk instead of a partition. (e.g. /dev/hda, not /dev/hda1) or the other way around? 

ntfsresize v2.0.0 (libntfs 10:0.)
failed to startup volume: invalid argument.
Error(22): opening /dev/sdb1 as NTFS failed: invalid argument.
Maybe you selected the wrong device? Or the whole disk instead of a partition. (e.g. /dev/hda, not /dev/hda1) or the other way around? 

Unable to read the contents of this file system!


ubuntu@ubuntu:~$ sudo ntfsfix /dev/sdb1
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37896   304399588+   7  HPFS/NTFS
/dev/sda2           37897       38913     8169052+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95cf20c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       33756   271145038+   7  HPFS/NTFS
/dev/sdb2           34167       38913    38130277+  83  Linux
/dev/sdb3           33757       34166     3293325   82  Linux swap / Solaris

Partition table entries are not in disk order



How do I recover my partition?

---

### Post by ajgreeny on 2008-05-22
So you can't boot to either Vista or Ubuntu, is that right?

Have you tried restoring the MBR for Vista as it may simply be a case of doing that and then reinstalling grub to wherever you want it to be, perhaps in place of the MBR or even on a separate disk if easier that way.  I have no idea how you restore the MBR of Vista, or even if it still has that as its boot system, but I'm sure there must be some way to restore the default.

If you have a machine which lets you chose boot priority at boot time by pressing a F* button, it might be easier to use a separate install of grub and keep your Vista boot system as it is.

---

### Post by gingk0 on 2008-05-22
I can boot into windows. 

If I try to run check disk on the 2nd drive. I get an error saying that the drive needs to be formated.

---

### Post by ajgreeny on 2008-05-22
Vista  asks you (or tells you, more like) to reformat the partition because it can't read ext3 file systems.  Don't worry about that, just ignore it for the moment and whatever you do don't reformat or try doing anything to it from windows; you'll be doomed to failure.

Try installing one of the utilities which let windows at least read and see the files on your ubuntu partition.  For XP there was explore2fs, but I don't know about Vista.  From there have a look at the /boot/grub/menu.lst file in the ubuntu partition to see what it lists at the bottom of the file.  Let's go from there.  I'm sure we'll be able to get you up and running, or at the very least let you copy all the files to a usb drive and then reinstall ubuntu.

Also worth running the live ubuntu cd and adding disk mounter to the panel, then try to mount all the partitions it sees by clicking on the icons and chosing **mount xxx**.  That may give us some info or error message about the partitions which might help.

---

### Post by gingk0 on 2008-05-22
> **ajgreeny said:**
> Vista  asks you (or tells you, more like) to reformat the partition because it can't read ext3 file systems.  Don't worry about that, just ignore it for the moment and whatever you do don't reformat or try doing anything to it from windows; you'll be doomed to failure.

Try installing one of the utilities which let windows at least read and see the files on your ubuntu partition.  For XP there was explore2fs, but I don't know about Vista.  From there have a look at the /boot/grub/menu.lst file in the ubuntu partition to see what it lists at the bottom of the file.  Let's go from there.  I'm sure we'll be able to get you up and running, or at the very least let you copy all the files to a usb drive and then reinstall ubuntu.

Also worth running the live ubuntu cd and adding disk mounter to the panel, then try to mount all the partitions it sees by clicking on the icons and choosing **mount xxx**.  That may give us some info or error message about the partitions which might help.

Basically I had some data on the 2nd drive. I partitioned it using the live cd and intended to make a dual boot pc. vista / ubuntu.  vista and ubuntu can read everything  but the ntfs partition on the 2nd disk. 

I downloaded testdisk and it see my data on the ntfs partition. I think the partition table or something like that got screwed up.

I'll post the testdisk log in a minute.

---

### Post by gingk0 on 2008-05-22
See the attached txt.

---

### Post by gingk0 on 2008-05-22
OK I fixed the partition using testdisk. I made a backup 1st. then fixed the boot and mbr. 


Now how do I get it to dual boot. Ubuntu is in stalled already but I never get an option when I restart. It boot right into vista.

---

### Post by Pumalite on 2008-05-22
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

