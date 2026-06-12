---
title: "Oops - set new disklabel..."
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2012-02-25
How do I undo this? I thought I was changing the label for only one partition on the disk... 

The disk is CLONED onto another disk, so data loss is not a concern. I prefer to not do a device copy, if I don't have to. 

[I][B]I think I am now mounted on one of the partitions on this disk too...
[/B][/I]

I still have gparted open. Of course, 'Undo Last Operation' is not available. I've done nothing on that machine, and will do nothing on it until I know exactly what to do on it. Save the 'should haves' too please...

---

### Post by sudodus on 2012-02-25
What does it look like and what should it look like? What tool did you use? Please give more details, for example you can post the output of
```
sudo fdisk -lu
``` and
```
sudo blkid
```

---

### Post by Moozillaaa on 2012-02-25
Thanks there sudodus...

Device 'a' is the device of interest here:


chucknb@chucknb-desktop:~$ sudo fdisk -l
[sudo] password for chucknb: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8f35

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04620462

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1759    14129136    7  HPFS/NTFS
/dev/sdb2            1760        3481    13831965   83  Linux
/dev/sdb3            3482        3736     2048287+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb015a805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdc2            5100       28556   188418352+   7  HPFS/NTFS
/dev/sdc3           28557       60801   259007962+  83  Linux

chucknb@chucknb-desktop:~$ blkid

chucknb@chucknb-desktop:~$ exec sudo -s

root@chucknb-desktop:~# blkid

/dev/sda1: UUID="66EBD5021CC53FFF" LABEL="nb_XP" TYPE="ntfs" 
/dev/sdc1: UUID="6E1A27941A27587B" LABEL="nb_W7" TYPE="ntfs" 
/dev/sdc3: LABEL="Apps" UUID="e5efff72-6bbf-4e1e-8c46-86e86ef422b5" TYPE="ext2" 
/dev/sdc2: UUID="2640B9ED40B9C3B9" LABEL="804Old500" TYPE="ntfs" 
/dev/sdb3: TYPE="swap" UUID="e3a18cf4-76a3-4498-9b8f-ec47b785d7ee" 
/dev/sda2: LABEL="Ubuntu" UUID="32a7f436-76a6-4cca-966f-2d24d2e2702a" TYPE="ext3" 
/dev/sdb2: UUID="ed4bc055-d18f-4c3e-abaf-3215102c6679" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="2CBB78BB57F50B0D" TYPE="ntfs" LABEL="nb_W7" 
root@chucknb-desktop:~#

---

### Post by Moozillaaa on 2012-02-25
Devices sdc1, and sdc2, are copies of the [former] sda1, and sda2, respectively...


edit:
And THANKS for not saying "You should have,", and "Why did you..."

---

### Post by sudodus on 2012-02-25
> **Moozillaaa said:**
> Device 'a' is the device of interest here:
```
sudo fdisk -l
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8f35

   Device Boot      Start         End      Blocks   Id  System
[no partitions listed]
...
Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb015a805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdc2            5100       28556   188418352+   7  HPFS/NTFS
/dev/sdc3           28557       60801   259007962+  83  Linux
...
root@chucknb-desktop:~# blkid

/dev/sda1: UUID="66EBD5021CC53FFF" LABEL="nb_XP" TYPE="ntfs" 
/dev/sdc1: UUID="6E1A27941A27587B" LABEL="nb_W7" TYPE="ntfs" 
/dev/sdc3: LABEL="Apps" UUID="e5efff72-6bbf-4e1e-8c46-86e86ef422b5" TYPE="ext2" 
/dev/sdc2: UUID="2640B9ED40B9C3B9" LABEL="804Old500" TYPE="ntfs" 
/dev/sda2: LABEL="Ubuntu" UUID="32a7f436-76a6-4cca-966f-2d24d2e2702a" TYPE="ext3" 
```

Blkid sees one partition on sda, but fdisk sees no partition. Maybe this is because it is still opened by gparted. Are the partitions on sdc OK (size, type, label etc)?

I have used gparted many times, and I have been lucky so far. I think you should close gparted, but before doing it, maybe you can post the output of ```
df
``` to see what partitions are mounted. To my knowledge gparted would not allow editing a mounted partition, but I don't know if you would be allowed to edit a label.

---

### Post by Moozillaaa on 2012-02-25
> **sudodus said:**
> Blkid sees one partition on sda, but fdisk sees no partition. Maybe this is because it is still opened by gparted. Are the partitions on sdc OK (size, type, label etc)?

I have used gparted many times, and I have been lucky so far. I think you should close gparted, but before doing it, maybe you can post the output of ```
df
``` to see what partitions are mounted. [COLOR=Red]To my knowledge gparted would not allow editing a mounted partition, but I don't know if you would be allowed to edit a label[/COLOR].

[COLOR=Red]I thought this also...[/COLOR]


Yes - GParted is still open; I have done NOTHING on that computer yet, once I discovered the error.

Device 'C' partitions are still ok - as they were before, as reported by GParted (it re-scanned after the set disklabel task).





root@chucknb-desktop:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2            182869032 154773304  18879640  90% /
varrun                 1898244       232   1898012   1% /var/run
varlock                1898244         0   1898244   0% /var/lock
udev                   1898244        88   1898156   1% /dev
devshm                 1898244       140   1898104   1% /dev/shm
lrm                    1898244     45192   1853052   3% /lib/modules/2.6.24-28-generic/volatile
/dev/sdb2             13614796   3712780   9210420  29% /media/disk-1
/dev/sdb1             14129132  11709228   2419904  83% /media/nb_W7
/dev/sda1             40957684  12861596  28096088  32% /media/disk-2
root@chucknb-desktop:~# 


What does this tell me? And should I run fdisk and block ID again after closing GParted?

---

### Post by sudodus on 2012-02-25
> **Moozillaaa said:**
> [COLOR=Red]I thought this also...[/COLOR]


Yes - GParted is still open; I have done NOTHING on that computer yet, once I discovered the error.

Device 'C' partitions are still ok - as they were before, as reported by GParted (it re-scanned after the set disklabel task).





```
root@chucknb-desktop:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2            182869032 154773304  18879640  90% /
varrun                 1898244       232   1898012   1% /var/run
varlock                1898244         0   1898244   0% /var/lock
udev                   1898244        88   1898156   1% /dev
devshm                 1898244       140   1898104   1% /dev/shm
lrm                    1898244     45192   1853052   3% /lib/modules/2.6.24-28-generic/volatile
/dev/sdb2             13614796   3712780   9210420  29% /media/disk-1
/dev/sdb1             14129132  11709228   2419904  83% /media/nb_W7
/dev/sda1             40957684  12861596  28096088  32% /media/disk-2
root@chucknb-desktop:~# 

```

What does this tell me? And should I run fdisk and block ID again after closing GParted?
Partitions on sda are mounted. I am not sure which way would be the best, to unmount first and close gparted afterwards or the other way around. I guess:

- If you edited the label on a mounted partition, then close gparted first.

- If you mounted the partition(s) after editing the label (but without closing gparted), then unmount first.

---

### Post by Moozillaaa on 2012-02-25
GParted closed.

New fdisk return:

root@chucknb-desktop:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8f35

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04620462

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1759    14129136    7  HPFS/NTFS
/dev/sdb2            1760        3481    13831965   83  Linux
/dev/sdb3            3482        3736     2048287+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb015a805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdc2            5100       28556   188418352+   7  HPFS/NTFS
/dev/sdc3           28557       60801   259007962+  83  Linux
root@chucknb-desktop:~# 




and new block ID return:

root@chucknb-desktop:~# blkid
/dev/sda1: UUID="66EBD5021CC53FFF" LABEL="nb_XP" TYPE="ntfs" 
/dev/sdc1: UUID="6E1A27941A27587B" LABEL="nb_W7" TYPE="ntfs" 
/dev/sdc3: LABEL="Apps" UUID="e5efff72-6bbf-4e1e-8c46-86e86ef422b5" TYPE="ext2" 
/dev/sdc2: UUID="2640B9ED40B9C3B9" LABEL="804Old500" TYPE="ntfs" 
/dev/sdb3: TYPE="swap" UUID="e3a18cf4-76a3-4498-9b8f-ec47b785d7ee" 
/dev/sda2: LABEL="Ubuntu" UUID="32a7f436-76a6-4cca-966f-2d24d2e2702a" TYPE="ext3" 
/dev/sdb2: UUID="ed4bc055-d18f-4c3e-abaf-3215102c6679" TYPE="ext3" SEC_TYPE="ext2" 
/dev/sdb1: UUID="2CBB78BB57F50B0D" TYPE="ntfs" LABEL="nb_W7" 
root@chucknb-desktop:~# 






(checking for differences, to add in a moment)





return for 'df' task:

root@chucknb-desktop:~# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2            182869032 154773652  18879292  90% /
varrun                 1898244       232   1898012   1% /var/run
varlock                1898244         0   1898244   0% /var/lock
udev                   1898244        88   1898156   1% /dev
devshm                 1898244       140   1898104   1% /dev/shm
lrm                    1898244     45192   1853052   3% /lib/modules/2.6.24-28-generic/volatile
/dev/sdb2             13614796   3712780   9210420  29% /media/disk-1
/dev/sdb1             14129132  11709228   2419904  83% /media/nb_W7
/dev/sda1             40957684  12861596  28096088  32% /media/disk-2
root@chucknb-desktop:~#

---

### Post by sudodus on 2012-02-25
sda1 and sda2 are still mounted. fdisk cannot see them. blkid sees them. That did not change.

Obviously your computer still works so sda2 mounted on / works. Can you read files on sda1 mounted on /media/disk-2?

I think you will not really know the outcome of this adventure until you reboot your computer. If you get problems, your partition table (of sda) is probably good enough for ***testdisk or gpart*** (not gparted) to make it perfect. But I think you have a rather good chance, that it will work after reboot. Otherwise do the repair job when booted from another drive (internal or CD or USB). And, when booted from another drive, finally fix your labels to what you want using gparted.

---

### Post by Moozillaaa on 2012-02-25
> **sudodus said:**
> sda1 and sda2 are still mounted. fdisk cannot see them. blkid sees them. That did not change.

Obviously your computer still works so sda2 mounted on / works. Can you read files on sda1 mounted on /media/disk-2?

I think you will not really know the outcome of this adventure until you reboot your computer. If you get problems, your partition table (of sda) is probably good enough for ***testdisk or gpart*** (not gparted) to make it perfect. But I think you have a rather good chance, that it will work after reboot. Otherwise do the repair job when booted from another drive (internal or CD or USB). And, when booted from another drive, finally fix your labels to what you want using gparted.

Thanks... sda2 is my Linux Hardy (I'm booted in Hardy) partition.

sda1 is XP, and it looks like I can still read XP filesystem files. 

I'm trying to get TestDisk app 6.13 started up now, but that's not going well yet. ???

My GRUB is a house of cards - I'd prefer to stay booted ... until at least the disk image is backed up, not just the files...

I'm afraid to even run GParted since closing it... :confused:

Thanks again there tho'...

---

### Post by sudodus on 2012-02-25
> **Moozillaaa said:**
> Thanks... sda2 is my Linux Hardy (I'm booted in Hardy) partition.

sda1 is XP, and it looks like I can still read XP filesystem files. 

I'm trying to get TestDisk app 6.13 started up now, but that's not going well yet. ???

My GRUB is a house of cards - I'd prefer to stay booted ... until at least the disk image is backed up, not just the files...

I'm afraid to even run GParted since closing it... :confused:

Thanks again there tho'...
Wait a minute! In your first post, you wrote > the disk is CLONED onto another disk, so data loss is not a concern

What disk image do you want to backup now? If you want to backup something from a mounted partition, do it with some kind of regular copying tool, (***cp*** is simple, ***rsync*** is more powerful), but don't run a cloning tool on a mounted partition, because the file data and file system table might get out of sync during the cloning operation, and then the clone or image will be corrupted.

---

### Post by Moozillaaa on 2012-02-25
ed.:
Cloned, sort of...

sda1 ntfs is cloned to identical ntfs partition - cp /dev/sda1 ->  /dev/sdc1  (can still be read)
sda2 ext2 Hardy is cloned to slightly larger ntfs partition - cp /dev/sda2 -> /dev/sdc2 (still readable; I'm booted in this one)
sda3, 4 are not important
> **sudodus said:**
> Wait a minute! In your first post, you wrote 

What disk image do you want to backup now? If you want to backup  something from a mounted partition, do it with some kind of regular  copying tool, (***cp*** is simple, ***rsync*** is more  powerful), but don't run a cloning tool on a mounted partition, because  the file data and file system table might get out of sync during the  cloning operation, and then the clone or image will be  corrupted.

-------------------------------------

Any more clues here, Mr. Sudodus?

Notice that in GParted, the entire device shows 'Unallocated'. I CAN read files in the sda1partition however, and I am mounted in sda2, booted in Hardy. sda3 was swap, and sda4 was blank ext3.

A similar situation comes to mind; if I put a 3Tb drive in one of the SATA channels, GParted shows 'Unallocated'. But all 4 x 700G partitions mount, and do read / write without problems.

So the partition table(?) error does not stop the device from being mounted. But what about a boot device, such as this one??? (I have not re-booted).

If you've no ideas, no problem; thanks for looking tho'.




[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213233&d=1330163520[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=213234&d=1330163746[/IMG]

---

### Post by sudodus on 2012-02-25
Hardy was good, but it is not updated to manage new devices, developed after hardy's end of life. This may be one cause of your problems.

What is it you need to backup? And how do you intend to back it up?

Anyway after that backup I suggest that you reboot your computer, if possible from another drive, for example a live system from a CD or USB drive. And it might be a good idea to try a version of Ubuntu that is still supported, 'lucid' 10.04 LTS, 'natty' 11.04 or 'oneiric' 11.10. You may select a flavour with small foot-print, for example Xubuntu or Lubuntu. So one suggestion might be to download an iso-file and make a boot CD or USB.

Do you have another PC for that or would it be necessary to get it done before rebooting this one we have been discussing?

---

### Post by sudodus on 2012-02-25
> **Moozillaaa said:**
> ed.:
Cloned, sort of...

sda1 ntfs is cloned to identical ntfs partition - cp /dev/sda1 ->  /dev/sdc1  (can still be read)
sda2 ext2 Hardy is cloned to slightly larger ntfs partition - cp /dev/sda2 -> /dev/sdc2 (still readable; I'm booted in this one)
sda3, 4 are not important

Well, the files are there, but

1. If sda1 is a windows boot partition, then I don't think it is enough to copy files to get a restored system bootable. But if it is a data partition, no worries, the files should be copied OK.

2. The files of sda2 should be OK, but the file permissions of a linux file system cannot be transferred to ntfs. So if you try to restore the partition, you will have many errors due to changed file permissions, when you try to boot from it.
> 

-------------------------------------

Any more clues here, Mr. Sudodus?

Notice that in GParted, the entire device shows 'Unallocated'. I CAN read files in the sda1partition however, and I am mounted in sda2, booted in Hardy. sda3 was swap, and sda4 was blank ext3.

A similar situation comes to mind; if I put a 3Tb drive in one of the SATA channels, GParted shows 'Unallocated'. But all 4 x 700G partitions mount, and do read / write without problems.

So the partition table(?) error does not stop the device from being mounted. But what about a boot device, such as this one??? (I have not re-booted).

If you've no ideas, no problem; thanks for looking tho'.

To summarize:
1. I think you have secured the files from sda.

2. If sda1 contains a bootable windows file system, and you unmount it, you should be able to make a complete image (a compressed image of the clone) of it without rebooting. If you want to do that, where would you want to write that image?

3. I would not recommend that you try to do that with sda2 without rebooting. I suggest that you try to install a brand new version of Ubuntu instead, but not at once. First you should try which version and flavour that is best for you. Try running live sessions from a CD or USB drive.

---

### Post by Moozillaaa on 2012-02-25
I have 10.04LTS installed on the 30 G disk.

Yep - it looks like all files from sda1, and sda2 are intact...

sda1 is XP. I don't know if XP will whine when I try to boot it from GRUB (if GRUB will load THAT is the question)...

I just prefer to do another cp or dd copy task, before rebooting, to make sure... But how do I 'define' device 'a'?

cp /dev/sd[SIZE=3][COLOR=Red]**?**[/COLOR][/SIZE] /dev/sd[external]???

I haven't gotten Partimage and TestDisk loaded yet

---

### Post by sudodus on 2012-02-25
> **Moozillaaa said:**
> ...
I just prefer to do another cp or dd copy task, before rebooting, to make sure... But how do I 'define' device 'a'?...

You want to copy sda1 with winxp.
1. unmount sda1```
sudo umount /dev/sda1
```

2. Change directory (cd) to the directory, where you want to the image. Make sure there is space for it (at least 2/3 of the uncompressed data size).

3. Be sure that the command is exactly correct! A typing error can destroy a disk or partition.
```
sudo dd if=/dev/sda1 bs=4096 | gzip > dd-sda1-winxp.gz
```

4. It takes time. dd doesn't talk, it works. If you get curious, you can push it to tell how much is done (and it continues to work again after writing 3 lines).
```
ps -au root|grep " dd$"
``` will give you the pid number usually four digits, for example
```
 [COLOR="Red"]4538[/COLOR] pts/1    00:00:01 dd
```
Use that number in the following command
```
sudo kill -USR1 [COLOR="red"]4538[/COLOR]
```

---

### Post by Moozillaaa on 2012-02-25
Good instruction - thanks again there...

I'll post back after shutdown and reboot (holding baited breath here [-o<)



ed.:
Nothing like compounded errors in the works... My sdc2 Hardy backup device was wiped temporarily (on purpose) a few weeks ago, and not yet re-backed up.

So while I can at the moment read all Hardy data to re-back it up, will I be able to make it a bootable image?
backup command:
cp  -r  /*  /media/disk-5/Hardy_backup

This will copy all my Hardy filesystem files. In the event that when I finally reboot, that the Hardy partition is not recognized and doesn't boot, will I be able to restore it using the above backup of the root directory?

---

### Post by sudodus on 2012-02-25
> **Moozillaaa said:**
> Good instruction - thanks again there...

I'll post back after shutdown and reboot (holding baited breath here [-o<)



ed.:
Nothing like compounded errors in the works... My sdc2 Hardy backup device was wiped temporarily (on purpose) a few weeks ago, and not yet re-backed up.

So while I can at the moment read all Hardy data to re-back it up, will I be able to make it a bootable image?
backup command:
cp  -r  /*  /media/disk-5/Hardy_backup

This will copy all my Hardy filesystem files. In the event that when I finally reboot, that the Hardy partition is not recognized and doesn't boot, will I be able to restore it using the above backup of the root directory?
I suggest that you copy the 'hardy' data from / to a linux partition, that is big enough. Start using ***rsync*** for such tasks ```
man rsync
```
```
rsync -av / /media/disk-5/Hardy_backup
``` Do you have a linux partition that has enough free space for such a copy? Otherwise, can you reformat some partition, for example sdc2 to ext3, so that it can preserve the file permissions?

I think some of the content of the active file system / is volatile (not necessary and not suitable to copy) but it might work.

---

### Post by sudodus on 2012-02-25
If you cannot or dare not reformat a drive maybe you can use ***tar*** to make one big archive file with the 'hardy' file system
```
sudo tar -cvf /media/disk-5/Hardy_backup.tar /
``` The last slash is to tell what to put into the archive.

You can compress it using the option -z (or --gzip)
```
sudo tar -cvzf /media/disk-5/Hardy_backup.tar.gz /
```

---

### Post by Moozillaaa on 2012-02-25
Still working on this copy [rsync] task, before re-booting (gulp). Will post when done...

You've been a BIG help. Too bad there's not more like you on the boards here...



The big deal - what have we LEARNED??? Mistakes always SHOULD lead to learning...

Too many backups CANNOT exist, even at the expense of 'messy' drivespace / partitions (total drivespace between all machines = about 27Tb, 12.25Tb is backup offline devices.
Cleanup must be done with caution. (judicious use of 'set disklabel'!!!)

---

### Post by sudodus on 2012-02-26
I'm glad that your backup is making progress. I have received help, at first from colleagues and later on from the internet (including the Ubuntu Forums), and now it is my turn to help when I can :-)

You are so right about backup. Many years ago I learned the lesson: 'Tough guys don't backup their data, they do the work twice instead'

---

### Post by Moozillaaa on 2012-02-26
I rebooted. Hardy GRUB on sda did not load. Error 22. Hardy GRUB *WAS* set up to boot:
Hardy sda2
XP      sda1
W7      sdb1

And it was set up to boot another GRUBLoader on sdc, chainloaded FROM Hardy GRUB, TO boot:
10.04 sdc
W7 sdb1
XP sda1
and BACK to Hardy GRUBLoader (just in case / just for fun)

So I booted device 'c' from BIOS. 10.04 GRUBLoader loaded. 10.04 and W7 booted properly when selected. Hardy GRUBLoader of course, would not load. I dropped from GRUB menu, to grub prompt.
grub> find /boot/grub/stage1 found the 10.04 stage1, but not the Hardy stage1. WAH!!!

BUT, XP on the problem drive however, sda1, when selected  - started a 'repair' startup - loading startup files. :o

I stopped that, in order to minimize writing to the disk. TestDisk, or PartImage might have less chance of full recovery, if ANY writing is done.

So, should TestDisk, and PartImage be run from XP environment ON SAME DISK as Hardy sda??? Or should they be run from 10.04 environment on another disk sdc???

Both apps should succeed at the recovery task, since both XP and Hardy were 'operable / readable', after the set disklabel error...

:confused:

---

### Post by sudodus on 2012-02-26
> **Moozillaaa said:**
> I ...
So, should TestDisk, and PartImage be run from XP environment ON SAME DISK as Hardy sda??? Or should they be run from 10.04 environment on another disk sdc???
...
It is always best to boot from another drive when doing repair jobs (or at least from another partition). So

1. boot from sdc if you can run 10.04 or at least linux,

2. otherwise boot a live session from a CD or USB drive (for example with an Ubuntu install drive).

---

### Post by sudodus on 2012-02-26
... or of course, if you have windows versions of the repair software, boot Windows, but do not use Windows on the drive you are repairing (except chkdsk /f which Windows obviously wants to run. Let that repair job run before you log in to Windows next time!

---

### Post by Moozillaaa on 2012-02-26
GRUB (with Hardy) is properly re-configured. TestDisk, executed from 10.04 environment, on another drive, successfully found all 4 partitions - Hardy, XP, swap, and a spare.

Hardy's GRUB had to be restored, and it then loaded.

Interestingly, after partition restoration, I booted again from 10.04 GRUB, and selected "Chainload to Hardy's GRUBLoader". THAT has not yet been restored (I think the TestDisk made XP, on sda1, the boot partition, although I don't know that for sure). ***[COLOR=Black]AND, BIOS is still set to boot from 10.04 disk,[/COLOR]*** which is on a RAID card. Disk enumeration with RAID cards is often a HUGE dEbaCLe :shock:

***ed.: This was the last problem here - BIOS is changed back, and Hardy GRUB now chainloads to 10.04 GRUBLoader (and back to Hardy, in the meantime).***

While TestDisk was running, it 'found' the partitions 'Created under Vista'. :confused: W7 is probably what it was referring to, but they weren't created under W7 either.

==========

Now - how to integrate Hardy files and settings into 10.04??? Never have I done this successfully. And Hardy is LOADED...

Will update additional notes, to help remember [stuff].

Thanks again there sudodus...

---

### Post by sudodus on 2012-02-26
I'm happy it works now!

Sit back and relax for a while, and take some time to consider what you really want! Do you really want everything on Hardy to migrate to Lucid. It is easy to move documents, pictures, videos and other stand-alone files. But configuration files may be obsolete or incompatible with the new system.

It might be a good idea to install programs to Lucid, when you need them. And you will see that after a year, there will be a different collection of programs that you have and use, compared to what there is on Hardy. Of course there will be overlapping, some programs that you must have (but updated versions from the new repositories).

Also consider that Lucid's end of support is April 2013. At that time Precise, the new LTS version has been around for a year, and should be rather stable. So in April or May, I suggest that you download some iso files of the various flavours of Precise and start testing them live from a CD or USB drive.

---

