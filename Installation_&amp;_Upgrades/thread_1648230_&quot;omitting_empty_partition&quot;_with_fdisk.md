---
title: "&quot;omitting empty partition&quot; with fdisk"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by jpmonette on 2010-12-18
Since I installed TinyXP on another partition on my PC, I get "omitting empty partition" when I use fdisk -l.

```
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c446687

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          13       18655   149738496    7  HPFS/NTFS
/dev/sda2           18656       21265    20964825    f  W95 Ext'd (LBA)
/dev/sda3           20614       21265     5237158+   7  HPFS/NTFS
/dev/sda4           21266       30402    73383936    c  W95 FAT32 (LBA)
/dev/sda5           18656       20548    15205459+  83  Linux
/dev/sda6           20549       20613      522081   82  Linux swap / Solaris
```

Also, when I try to use gparted, the program doesn't resolve my partition: I only have a huge unallocated HD. For palimpset, I get an error stopping the application from booting "libgdu:ERROR:gdu-pool.c:2369:device_recurse: assertion failed: (depth < 100)".

I think this problem is similar to mine:

[http://ubuntuforums.org/showthread.php?t=1078820](http://ubuntuforums.org/showthread.php?t=1078820)

Here is the output of what helped to fix the problem (creating the partition.txt):

```
root@azerox:~# sfdisk -d /dev/sda
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=   206848, size=299476992, Id= 7, bootable
/dev/sda2 : start=299692575, size= 41929650, Id= f
/dev/sda3 : start=331147908, size= 10474317, Id= 7
/dev/sda4 : start=341626880, size=146767872, Id= c
/dev/sda5 : start=299692701, size= 30410919, Id=83
/dev/sda6 : start=330103683, size=  1044162, Id=82
```

And this:

```
root@azerox:~# mount /dev/sda3 /mnt && ls -l /mnt 
total 41300
drwxrwxrwx 1 root root     4096 2010-04-25 16:30 Documents and Settings
drwxrwxrwx 1 root root        0 2010-05-06 13:53 Intel
-rwxrwxrwx 1 root root    47564 2004-08-03 21:07 NTDETECT.COM
-rwxrwxrwx 1 root root   250032 2004-08-03 21:07 NTLDR
-rwxrwxrwx 1 root root 41943040 2010-12-17 06:46 PAGEFILE.SYS
drwxrwxrwx 1 root root     4096 2010-04-25 16:38 Program Files
drwxrwxrwx 1 root root        0 2010-05-30 20:00 $RECYCLE.BIN
-rwxrwxrwx 1 root root     6252 2010-12-17 06:49 $$RENAME.TXT
drwxrwxrwx 1 root root        0 2010-04-25 22:33 System Volume Information
drwxrwxrwx 1 root root    28672 2010-12-17 06:49 WINDOWS
```

Thanks a lot for your support.

> NOTE: I also searched for the palimpset error and I found a Bug Report there: [https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/571038](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/571038). I don't know if these informations could help to fix this problem, I think it's related and probably cause by the installation of Windows XP and the way that gparted and palimpset read the partitions.

---

### Post by srs5694 on 2010-12-19
> **jpmonette said:**
> Since I installed TinyXP on another partition on my PC, I get "omitting empty partition" when I use fdisk -l.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          13       18655   149738496    7  HPFS/NTFS
/dev/sda2           18656       21265    20964825    f  W95 Ext'd (LBA)
/dev/sda3           20614       21265     5237158+   7  HPFS/NTFS
/dev/sda4           21266       30402    73383936    c  W95 FAT32 (LBA)
/dev/sda5           18656       20548    15205459+  83  Linux
/dev/sda6           20549       20613      522081   82  Linux swap / Solaris
```

At least part of the problem is that some buggy utility create two overlapping primary partitions. The first, /dev/sda2, is technically an extended partition; but extended partitions are really just specialized primary partitions, and they must not overlap with other primary partitions, such as /dev/sda3. This problem is fixable, but I don't know of any utility that will do it automatically in a point-and-click manner. I know of three ways to do it:

One option is to use the partitions.txt file you've already created and change the size of the extended partition so that it covers both /dev/sda5 and /dev/sda6 but doesn't extend into the range of any of the primary partitions. This requires very close attention to details, and you can easily trash the whole disk if you get something wrong. (Recovery should usually be possible, but you'll need to recover by getting it right.) [This page of mine](http://www.rodsbooks.com/missing-parts/index.html) describes a similar modification; but the problem there is that the extended partition extends beyond the end of the disk.

A second option is to use the *latest version* of my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program. This program automatically converts the old Master Boot Record (MBR) disks, such as you've got, to GUID Partition Table (GPT) format, and can do the reverse conversion, as well. Thus, you'd launch gdisk on the disk, then type "r" to go to the recovery & transformation menu, then type "g" to do the GPT-to-MBR conversion. At this point you'll be able to adjust primary/logical assignments. You want to be sure that the NTFS boot partitions are both primary. Linux is happy on either a logical or a primary partition, but given the number of partitions and their types, the Linux partitions will both have to be logical. Likewise, the FAT partition will have to be primary. When you're satisfied, tell it to finalize the changes and exit. Once this is done, you'll probably have to re-install GRUB on the disk to make it bootable again.

A third way to do it, which involves the least effort or thinking on your part but that's the most dangerous, is to wipe all the partitions (using fdisk or GParted) and then use [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) from an emergency system to locate and recover the partitions. This is easy if it works, but it's possible that TestDisk will fail to identify a partition or misidentify a partition, in which case you'll be in very deep trouble.

Overall, I'd say that the sfdisk approach is probably best, provided you're careful with your arithmetic. If you're not comfortable with that approach, using gdisk might be worth a go; but that's a rather convoluted path to a fix and it's likely to render the system temporarily unbootable. You could also look for a utility that will do the job more directly.

---

### Post by jpmonette on 2010-12-19
```
root@azerox:~# LANG=C fdisk -lu /dev/sda
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c446687

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848   299683839   149738496    7  HPFS/NTFS
/dev/sda2       299692575   341622224    20964825    f  W95 Ext'd (LBA)
/dev/sda3       331147908   341622224     5237158+   7  HPFS/NTFS
/dev/sda4       341626880   488394751    73383936    c  W95 FAT32 (LBA)
/dev/sda5       299692701   330103619    15205459+  83  Linux
/dev/sda6       330103683   331147844      522081   82  Linux swap / Solaris
```

root@azerox:~# sfdisk -d /dev/sda > parts.txt

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=   206848, size=299476992, Id= 7, bootable
/dev/sda2 : start=299692575, size= 41929650, Id= f
/dev/sda3 : start=331147908, size= 10474317, Id= 7
/dev/sda4 : start=341626880, size=146767872, Id= c
/dev/sda5 : start=299692701, size= 30410919, Id=83
/dev/sda6 : start=330103683, size=  1044162, Id=82
```

I don't want to break/lose anything, so how am I suppose to fix this partition table?

---

### Post by srs5694 on 2010-12-20
> **jpmonette said:**
> I don't want to break/lose anything, so how am I suppose to fix this partition table?

You already posted all of that. Please see my previous post. If you have more specific questions, please ask them.

---

### Post by jpmonette on 2010-12-21
I calculate every "(next partition start) - (start + size)" and all the results are positive, so no partition overlap another one. All my extended partitions (5, 6 ,3) have a seperation of 63.

I honestly don't know what to resize to avoid overlapping since nothing is overlapping due to my calculation.

> EDIT: Do I need to resize my /dev/sda4

[QUOTE]/dev/sda4       341626880   488394751    73383936    c  W95 FAT32 (LBA)

since it end @ 488394751 and that the total # of sector is 488397168 ?

I don't get it, since I installed XP on /dev/sda3 and didn't mess with /dev/sda4.[/QUOTE]

---

### Post by srs5694 on 2010-12-22
> **jpmonette said:**
> I calculate every "(next partition start) - (start + size)" and all the results are positive, so no partition overlap another one. All my extended partitions (5, 6 ,3) have a seperation of 63.

I honestly don't know what to resize to avoid overlapping since nothing is overlapping due to my calculation.

> ```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848   299683839   149738496    7  HPFS/NTFS
/dev/sda2       299692575   [COLOR=Red]341622224[/COLOR]    20964825    f  W95 Ext'd (LBA)
/dev/sda3       [COLOR=Red]331147908   341622224[/COLOR]     5237158+   7  HPFS/NTFS
/dev/sda4       341626880   488394751    73383936    c  W95 FAT32 (LBA)
/dev/sda5       299692701   330103619    15205459+  83  Linux
/dev/sda6       330103683   331147844      522081   82  Linux swap / Solaris

```

/dev/sda2 overlaps /dev/sda3. This must be corrected by reducing the size of /dev/sda2.

---

### Post by jpmonette on 2010-12-22
> **srs5694 said:**
> /dev/sda2 overlaps /dev/sda3. This must be corrected by reducing the size of /dev/sda2.

/dev/sda2 is an extended partitions, it contains sda3, sda5 and sda6. It's not suppose to start at the beginning of sda5 and end at the end of sda2?

---

### Post by srs5694 on 2010-12-23
In Linux, the partitions numbered 1-4 are, by definition, primary (or extended) partitions. Thus, an overlap between any partitions 1-4 is an error. Your partitions #2 and #3 overlap; that is an error. Partitions 5 and up are, by definition, logical partitions. Only logical partitions may reside inside an extended partition (and in fact, logical partitions *must* reside within an extended partition).

---

### Post by jpmonette on 2010-12-25
I still don't understand. /dev/sda2 contain sda3, sda5 and sda6 (like I said). sda3 should be a logical partition, it's not overlapping. That's how I formatted it on Windows. I'm not suppose to mark the sda3 as logical instead?

---

### Post by coffeecat on 2010-12-25
Please **listen** to srs5694. He is an expert - a professional in these matters.

> **jpmonette said:**
> sda3 should be a logical partition,

No, it shouldn't. A logical partition cannot have a number 3.

> **jpmonette said:**
>  it's not overlapping.

Yes it is.

> **jpmonette said:**
>  That's how I formatted it on Windows.

Then the Windows software must be buggy.

> **jpmonette said:**
>  I'm not suppose to mark the sda3 as logical instead?

No.

srs5694 has already explained this, but I will say it again. Partitions numbered 1, 2, 3 or 4 can only be primary partitions - or an extended partition which, as srs5694 has explained, is a special type of primary partition. Logical partitions are numbered 5 and upwards - **always**.

You would do well to  follow srs5694's advice. There is no one on this forum who can advise you better.

---

### Post by Rubi1200 on 2010-12-25
I can only reiterate what coffeecat has already said; you have been given advice by one of the experts.

If you need a step by step explanation, please say so and we can try and walk you through this.

Thanks.

---

### Post by jpmonette on 2010-12-25
I just feel I'm asking a question and everyone is answering another question. I want to understand this, I don't want the quick answer without explanation about what I'm doing.

Here's a schema of my drive:

> 100MB free space
------------------
Windows 7 (NTFS)
------------------
Extended Partition
---> Linux (ext4)
---> Swap
---> Windows XP (NTFS)
------------------
DATA (fat32)

The /dev/sda3 is my Windows XP that I installed on the third part of my extend partitions. I guess something has been changed in my partition table setting the Windows XP partition in primary, but not modifying the size of my extended partition to chop it out.

Is it possible to change the Windows XP to be part of the extended partition or do I really have to resize my extended partition to leave the Windows XP partition primary?

---

### Post by Quackers on 2010-12-26
If I can I'd like to clarify something.
sda2 is an extended partition and it probably should contain sda5 and sda6. However, it appears to contain sda3 (by virtue of its start/finish numbers) however this cannot be, as sda3 should undoubtedly be a primary partition.
sda2 needs to be reduced so that it includes sda5 and just about includes sda6 (which ends at 331147844 )

I'm afraid I don't know whether sda3 can be made a logical partition, and even if it can, I'm not sure XP will boot.

I suspect that the best way to go is to follow srs5694's advice in post #2
(In all honesty, it is usually best to follow srs5694's advice, in my experience :-) )

---

### Post by coffeecat on 2010-12-26
@jpmonette, you seem very attached to the idea that sda3 should be  "inside" the extended partition. You've been told more than once that  this is not possible. For a partition to be "inside" an extended  partition, it would have to be a logical one. And, as Quackers has  pointed out, Windows will not boot from a logical partition. Or at least  the Windows boot files **must** be in a primary partition. If you  were to make sda3 (were able to make) - which I assume is your Windows C: - a logical  partition, then you would have to create a separate primary partition  for the boot files. Which is all a bit pointless. 

So...

> **jpmonette said:**
> do I really have to resize my extended partition to leave the Windows XP partition primary?

Yes.

One other thing. You mention that this is how you formatted the drive in Windows. What software did you use? Whatever it was, it has left you with an illogical mess, so I suggest you don't use that software again.

---

### Post by jpmonette on 2010-12-26
I've used GPart to format my logical drives and installed with the Windows XP installer. I guess the XP installer simply installed and changed the partition to primary.

Thanks for answering my questions. I'll give it a try now.


I'll change this:

> # partition table of /dev/sda
unit: sectors

/dev/sda1 : start=   206848, size=299476992, Id= 7, bootable
/dev/sda2 : start=299692575, size= 41929650, Id= f
/dev/sda3 : start=331147908, size= 10474317, Id= 7
/dev/sda4 : start=341626880, size=146767872, Id= c
/dev/sda5 : start=299692701, size= 30410919, Id=83
/dev/sda6 : start=330103683, size=  1044162, Id=82

To this:

> # partition table of /dev/sda
unit: sectors

/dev/sda1 : start=   206848, size=299476992, Id= 7, bootable
/dev/sda2 : start=299692575, size= _31455270_, Id= f
/dev/sda3 : start=331147908, size= 10474317, Id= 7
/dev/sda4 : start=341626880, size=146767872, Id= c
/dev/sda5 : start=299692701, size= 30410919, Id=83
/dev/sda6 : start=330103683, size=  1044162, Id=82

Is this ok?

EDIT: Done it.

---

### Post by jpmonette on 2010-12-26
I wasn't able to restart after this, problem with GRUB2.  I followed the guide available at:

[https://help.ubuntu.com/community/Grub2#Command](https://help.ubuntu.com/community/Grub2#Command) Line and Rescue Monde

(the part named Boot a Specific Kernel Manually)

For anyone who has the same problem, when you finally boot into Linux, don't forget to make the changes permanent by doing an update-grub.

I suggest you to add this info to your tutorial srs5694 in case people can't reboot after a resize.

I can now access all my partitions! Thanks a lot!

---

### Post by Quackers on 2010-12-26
Well done! That's a good result :-)
FYI, any time you reformat a partition (and/or re-install an OS ) it will be given a new UUID and grub will need to be updated to adjust to the new UUID.

---

### Post by coffeecat on 2010-12-27
I'm glad it's sorted. :)

> **jpmonette said:**
> I've used GPart to format my logical drives and installed with the Windows XP installer. I guess the XP installer simply installed and changed the partition to primary.

Now, that's a most interesting observation. You mean you created a logical partition with Gparted, pointed the Windows XP installer to it and the XP installer, instead of telling you that a logical partition is unsuitable, had a go at changing it to a primary but simply succeeded in messing up the partition table?

I'm at a loss for words! :-s

---

### Post by Quackers on 2010-12-27
> **coffeecat said:**
> 

I'm at a loss for words! :-s

Never! :P :):)

---

### Post by jpmonette on 2010-12-30
> **coffeecat said:**
> I'm glad it's sorted. :)



Now, that's a most interesting observation. You mean you created a logical partition with Gparted, pointed the Windows XP installer to it and the XP installer, instead of telling you that a logical partition is unsuitable, had a go at changing it to a primary but simply succeeded in messing up the partition table?

I'm at a loss for words! :-s

Previously, I had Windows XP installed in inside the extended partition without problem (it was in logical). I formatted the space with GParted (it was still a logical partition) and I reinstalled Windows XP. That's where everything started.

---

### Post by coffeecat on 2010-12-31
> **jpmonette said:**
> Previously, I had Windows XP installed in inside the extended partition without problem (it was in logical). I formatted the space with GParted (it was still a logical partition) and I reinstalled Windows XP. That's where everything started.

If Windows C: was previously a logical partition, then there **must** have been a separate primary partition with the boot files. See here:

[http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition](http://www.zyxware.com/articles/2008/07/20/how-to-install-and-boot-windows-on-a-logical-parition)

The boot file primary partition  must have disappeared when you used Gparted.

---

