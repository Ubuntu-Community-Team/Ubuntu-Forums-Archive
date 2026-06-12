---
title: "Ubuntu 11.10 Usb Installation"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by ExpDisease on 2011-11-13
Hi,

I'm trying to install ubuntu 11.10 with windows 7 but it seems that the installer doesn't see windows 7 so it gives me 2 choice. 

Erase Everyting
Do Something Else

When I say do something else the partition manager appears but also the installer doesn't see any of the partitions

How can I do an installation without deleting windows

---

### Post by darkod on 2011-11-13
This usually happens if the disk has been used in raid and has raid meta data still on it. You can remove the meta data if you boot ubuntu in live mode and in terminal run:

sudo dmraid -E -r /dev/sda

Do this ONLY if you are NOT running raid, otherwise it will destroy your array.

Also, if dual booting with win7 it's better to boot win7 first, use Disk Management to shrink its partition and make unallocated space in ubuntu. Then reboot win7 few times to do its disk checks.

After that boot the ubuntu cd and do the install either by manual partitioning (do something else) or tell it to use the largest available free space.

---

### Post by mjzanga on 2011-11-13
ahh, someone with the same problem as me...I have a dell laptop that came with 3 partitions, first an OEM partition, second a recovery partition, and third the C drive.  I removed the OEM and recovery partitions since they were of no use to me, leaving the 15GB or so at the front of the disk unallocated.  No matter what I do no partitions are detected, and I also noticed that if I run fdisk -l in the command line it returns a string of errors for that particular disk.

---

### Post by mjzanga on 2011-11-13
I'll give that command a shot. I had read something about raid causing problems but what I read said to go in bios and turn off raid, which there was no option for...

---

### Post by darkod on 2011-11-13
> **mjzanga said:**
> ahh, someone with the same problem as me...I have a dell laptop that came with 3 partitions, first an OEM partition, second a recovery partition, and third the C drive.  I removed the OEM and recovery partitions since they were of no use to me, leaving the 15GB or so at the front of the disk unallocated.  No matter what I do no partitions are detected, and I also noticed that if I run fdisk -l in the command line it returns a string of errors for that particular disk.

Doesn't sound like the same, and you should really start separate thread for different solution. But quickly:
Make sure there are no errors on your ntfs partition C:. Boot windows and in command prompt run:

chkdsk c: /r

Sometimes the installer will ignore a disk if it can notice errors on it even if they are in the windows partition. See if that helps.

---

### Post by mjzanga on 2011-11-13
> **darkod said:**
> Doesn't sound like the same, and you should really start separate thread for different solution. But quickly:
Make sure there are no errors on your ntfs partition C:. Boot windows and in command prompt run:

chkdsk c: /r

Sometimes the installer will ignore a disk if it can notice errors on it even if they are in the windows partition. See if that helps.

I'm sorry >.> if you would like to help me out still here is a link to the new thread: [http://ubuntuforums.org/showthread.php?p=11454187#post11454187](http://ubuntuforums.org/showthread.php?p=11454187#post11454187)
also, I have run chkdsk in windows but it didn't help, and dmraid also returned errors.

---

### Post by ExpDisease on 2011-11-13
I tried that command and it gave this output. also i never did a raid =)

no raid disks and with names: "/dev/sda"

I shrinked and made an unallocated space but it didint work either

also when i try to create a volume in that free space it gives this output

Daemon is inhibited

---

### Post by darkod on 2011-11-13
Can you run ubuntu in live mode and post the results of:

sudo fdisk -l (small L)

---

### Post by ExpDisease on 2011-11-13
```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x49f5a956

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       20268   162692096    7  HPFS/NTFS
/dev/sda3           20268       41220   168302592    7  HPFS/NTFS

Disk /dev/sdb: 4005 MB, 4005527552 bytes
124 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00049670

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1017     3909317    c  W95 FAT32 (LBA)

```

---

### Post by darkod on 2011-11-13
Uh, you have GPT partition table, not the old msdos type.

I have installed ubuntu on gpt as a test recently, but as only OS, not together with windows.

Do one more test: Boot live mode again and open Gparted. When it shows /dev/sda and the partitions, look at the right in the column Flags. Does it have any flags for the first partition, /dev/sda1?

---

### Post by ExpDisease on 2011-11-13
Gparted show no partitions =) only sda and it has no partitions. I did nothing on purpose to have gpt =/ 
Can I change it or should I say goodbye to linux on this computer without virtualbox

---

### Post by darkod on 2011-11-13
I was surprised too. msdos table works fine with up to 2TB disks. Only lately 1TB and 2TB disks started to be more common with gpt, but to have a 500GB disk with gpt... No need.

I have seen mentioned some tools to convert to msdos without data loss, but gpt is beyond my expertise. I don't want to play with your data. :)

---

### Post by ExpDisease on 2011-11-13
okey then thanks anyway :)

---

### Post by darkod on 2011-11-13
You can google switching gpt table to msdos and see how you like what you find.

Another option, but it depends if it's worth it, moving all your data temporarily, writing a new blank msdos table on this hdd (that will delete all partition and data), installing win7 again and ubuntu. Putting the data back.

---

### Post by ExpDisease on 2011-11-13
I think it will be too long :) I will just install it to my desktop thats easier :D

---

### Post by ExpDisease on 2011-11-13
> **darkod said:**
> quote


Can I ask you a question. What if I install ubuntu on a external drive would the drivers be a problem if I plug the hdd to different computers, or will it be just fine

---

### Post by darkod on 2011-11-13
Depends. In a lot of cases I would expect it to work, because it has lots of drivers included. It's like installing on lots of different PCs, on most of them works straight out of the box, which means drivers are included.

It will detect new hardware, activate the drivers and it should be fine. There are no guarantees of course.

---

### Post by ExpDisease on 2011-11-13
Ok then I will experiment that. Thanks

---

