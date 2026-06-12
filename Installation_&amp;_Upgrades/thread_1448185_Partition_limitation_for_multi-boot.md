---
title: "Partition limitation for multi-boot"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by ndrli on 2010-04-06
Hi,

I have a 500G disk and want to setup it as a test machine with many partitions.

The first partition is for Windows XP. It works. I use USB disk to boot Ubuntu, so I can use Ubuntu's command dd to backup my XP partition. 

Than I set more than 10 partitions. Then Ubuntu booted from USB does not always work. It always boots, but when I open a terminal, I get funny characters.. It seems the problem is something to do with number or size of partitions.

Is there a limit for number of partitions or size of partitions?

Any information would be appreciated. Thanks in advance.

---

### Post by mikewhatever on 2010-04-06
If there is a limit, it's obviously higher then 10, and the size of partitions is 2TB, or so I heard. What might be the problem is the numbers which designate partitions. These numbers may change when you create and delete partitions, and if that happens, the boot loader won't be able to find the system partition it needs to boot. Another reason may be installing numerous operating system and then deleting.
Perhaps you can try describing the problem a little better. What funny characters are you talking about? Do you get any errors?

---

### Post by ndrli on 2010-04-06
> **mikewhatever said:**
> If there is a limit, it's obviously higher then 10, and the size of partitions is 2TB, or so I heard. What might be the problem is the numbers which designate partitions. These numbers may change when you create and delete partitions, and if that happens, the boot loader won't be able to find the system partition it needs to boot. Another reason may be installing numerous operating system and then deleting.
Perhaps you can try describing the problem a little better. What funny characters are you talking about? Do you get any errors?

Thanks for your replay. "funny characters" actually are regular characters, but are not what I keyed. Sometimes, some characters keep showing event I do not press any key.

First, my first partition was Windows Vista. Second was Ubuntu. Windows XP was the fourth. Total more than 10 partitions. I installed vista, ubuntu and xp. They all worked.  There was a free space (more than 100G) left on the extended partition. Later I found that free space was moved (not by me) from under extended partition to the top, so partition software complained that I exceeded max number of partitions. I thought the problem was from by EasyBCD  or Vista or combination of them. I thought few people played Vista, Linux with multi-partitions, so the software was not fully tested. So I decide to trash Vista and re-partition whole 500G disk. Now, my first partition is XP. It works. But when I try to boot Ubuntu from USB, I get random problem. When I boot Fedora from USB, the boot process hangs almost every time. 

It seems the problem is related with partitions..

---

### Post by mikewhatever on 2010-04-06
Well, Ubuntu and Fedora not booting may be related to the partitions, but self replicating characters probably aren't. The partition limit error you got was probably the 4 primary partitions per hdd. The first installation of Windows usually needs to be on a primary partition, and extended partitions are primary as well. I really don't know how many logical partitions can be created.

---

### Post by oldfred on 2010-04-06
The number of extended partitions is very large perhaps unlimited. This says the old windows fdisk limited it to 23 total partitions as that was its max. I have seen elsewhere other numbers like 64 or 128.
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

You can have only one extended partition and if your free space is not next to, so you can add it to the extended ( or already inside the extended) you will not be able to create more partitions. 

If you create/delete partitions it can renumber the sda1,sda2 settings and possibly change UUIDs although if you do not touch the partition the UUID should not change.

---

### Post by srs5694 on 2010-04-06
> **oldfred said:**
> The number of extended partitions is very large perhaps unlimited. This says the old windows fdisk limited it to 23 total partitions as that was its max. I have seen elsewhere other numbers like 64 or 128.
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

Logical partitions are stored in a linked-list data structure, meaning that each partition definition contains a pointer to the next one. In principle, this makes for limits based on the size of the pointers involved and the size of the disk. As these pointers are 32 bits and as each pointer and each partition must be at least one sector in size, this makes the theoretical limit (2^32)/2, or about 2 billion partitions on a 2TB disk. What anybody could possibly want with 2 billion 512-byte partitions I can't say, though. ;)

Of course, that's a theoretical limit based on the partition data structures. There are likely to be much more restrictive practical limits within various OSes. I don't happen to know what they are in the Linux kernel or other Linux tools (udev, for instance). I have used Linux systems with upwards of a dozen partitions defined, but I've never tried to find the practical limits.

In any event, I doubt very much if ndrli's problems are related to having too many partitions. It could be that there are actually two distinct problems: One causing the boot problems and another causing the funny characters. Unfortunately, the problem description is too vague for me to speculate further. It might be helpful to see the precise partition map. This can be done from an emergency boot system by opening a terminal and typing:

```

fdisk -lu

```

A digital photo of the funny characters might also be helpful. Perhaps somebody would recognize them as being a particular alphabet, for instance.

---

### Post by ndrli on 2010-04-06
> **srs5694 said:**
> 

In any event, I doubt very much if ndrli's problems are related to having too many partitions. It could be that there are actually two distinct problems: One causing the boot problems and another causing the funny characters. Unfortunately, the problem description is too vague for me to speculate further. It might be helpful to see the precise partition map. This can be done from an emergency boot system by opening a terminal and typing:

```

fdisk -lu

```A digital photo of the funny characters might also be helpful. Perhaps somebody would recognize them as being a particular alphabet, for instance.

I partitioned the disk using WindowsXp facility. I thought that may make partition table strange for linux. So, today, I used Ubuntu's gParted to re-do part of the partition (from sda8 down). Below is the new partitions.

After I re-partitioned, the first time I booted Ubuntu from USB, I got "funny characters": I pressed 'l' and 's', but got '5' (digital 5) keeping coming. But after that I got success re-boot (3-4 times). So I could not reproduce the problem and get a digital photo.

The boot process for Fedora still have problme. But it went a little further: before it hanged when the logo (fancy 'f') showed up, now some time I got log-in screen. But never be a successful boot.

My theory is: Linux tries to read partition table. but something is strange about the partitions. Linux confused, the behavior is undefined, so sometimes I got "funny characters", sometimes hangs..

The partition data is from 
  cat /proc/partitions
>>>>>>>>>>
major minor  #blocks  name

   7        0     684016 loop0
   8        0  488386584 sda
   8        1   40960000 sda1
   8        2   30720000 sda2
   8        3   30617600 sda3
   8        4          1 sda4
   8        5   40861296 sda5
   8        6   40756873 sda6
   8        7   42620413 sda7
   8        8    4096543 sda8
   8        9    3887698 sda9
   8       10   10241406 sda10
   8       11   11261533 sda11
   8       12   15358108 sda12
   8       13   16386268 sda13
   8       14   17406396 sda14
   8       15   18434556 sda15
 259        0  164762608 sda16
   8       16    3921919 sdb
   8       17    3919841 sdb1
   8       32    3913728 sdc
   8       33    3913712 sdc1
<<<<<<<<<<
sda1 is XP partition. It is working
sda5 and sda6 are NTFS partitions, working
other partitions contain no data, some formated, some are not.
 
Thank you!

---

### Post by oldfred on 2010-04-06
srs5694 knows a lot more about partitions than I do but this does not look correct - major is 259? Run the other listing command:

```
sudo fdisk -lu
```

259        0  164762608 sda16

---

### Post by ndrli on 2010-04-07
I have booted Ubuntu (from LiveUSB - USB made from LiveCD by UNetBootin) about 10 times since I re-partitioned. About 4 times were not successful: when I press letter 'l" on a terminal, digital '3' kept coming. I tried to catch the "funny characters", but when I pressed "Prnt Scrn" key, The shutdown window appears, kept showing up. That means something wrong about keyboard related part was wrong.

Below is the result  from  sudo fdisk -lu. Maybe "Partition 1 does not end on cylinder boundary" caused the problem? I use Windows XP installation CD partitioned first partitions.

>>>>>
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00053ca0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    81922047    40960000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        81922048   143362047    30720000   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3       143362048   204597247    30617600    6  FAT16
Partition 3 does not end on cylinder boundary.
/dev/sda4       204603840   976751999   386074080    f  W95 Ext'd (LBA)
/dev/sda5       204603903   286326494    40861296    7  HPFS/NTFS
/dev/sda6       286326558   367840304    40756873+   7  HPFS/NTFS
/dev/sda7       367840368   453081194    42620413+   7  HPFS/NTFS
/dev/sda8       453081258   461274344     4096543+  82  Linux swap / Solaris
/dev/sda9       461274408   469049804     3887698+  83  Linux
/dev/sda10      469049868   489532679    10241406   83  Linux
/dev/sda11      489532743   512055809    11261533+  83  Linux
/dev/sda12      512055873   542772089    15358108+  83  Linux
/dev/sda13      542772153   575544689    16386268+  83  Linux
/dev/sda14      575544753   610357544    17406396   83  Linux
/dev/sda15      610357608   647226719    18434556   83  Linux
/dev/sda16      647226783   976751999   164762608+   7  HPFS/NTFS

Disk /dev/sdb: 4007 MB, 4007657472 bytes
16 heads, 32 sectors/track, 15288 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     7827455     3913712    c  W95 FAT32 (LBA)
<<<<<

Thanks.

---

### Post by oldfred on 2010-04-07
But I do not believe the cylinder boundary is a problem. 

I do not fully understand the inner working of hard drives anymore. Ever since hard drives became larger than the MBR style heads, cylinders, track/sector mapping from physical to logical was exceeded it has all become logical. You will notice almost all drives now have 255 heads and 63 sectors as those were the maximums.

Someone who knows more can explain it better.

---

### Post by srs5694 on 2010-04-07
I don't see anything obviously wrong with your partitions; however, I haven't checked every one to see if there might be overlaps. (You can check this yourself; look for partitions whose end points come after the start point of subsequent partitions. Note that /dev/sda4 is an extended partition that serves as a placeholder for all the logical partitions (/dev/sda5 through /dev/sda16 on your disk), so it will overlap with all of the extended partitions.

The cylinder boundary messages are definitely *not* the problem.

To recap your installation and problems; please correct me if I'm misunderstanding something:


[list]
[*]You can boot Windows fine from /dev/sda.
[*]You don't have any bootable Linux installation on /dev/sda; you boot from a USB flash drive and just use /dev/sda for storage.
[*]Something, unknown to you, shifted some of your Linux partitions on /dev/sda at some point.
[*]When you boot Linux from a USB flash drive, the boot either fails your you get problems with keys you type not showing up correctly.
[/list]


I have two questions:


[list]
[*]Do your USB-based Linux installations automatically mount any partitions on /dev/sda, particularly in standard filesystem locations (as /usr, /usr/local, /var, /home, or others)?
[*]What happens if you physically disconnect /dev/sda and boot Linux from USB? (Don't bother answering if the answer to the preceding question was "yes.")
[/list]


My thinking is that, first, if your USB-based installations reference /dev/sda partitions, something on those partitions may have been corrupted. This isn't an issue of the number of size of partitions, but of either that mysterious process that moved your partitions at some point in the past or of some random corruption event. (Filesystem damage in a power failure, for instance.) It's also possible that your USB installations are mounting /dev/sda partitions in the wrong locations -- say, mounting /dev/sda9 where /dev/sda11 should be mounted. This would result in file-not-found errors, and depending on what was using those files, the boot would either fail or you'd get some weird program behaviors.

Second, if your USB-based installations do *not* rely on /dev/sda partitions, you may be able to learn more by booting with /dev/sda disconnected. If the systems continue to misbehave, then you can rule out /dev/sda as a source of that particular problem. If the system behaves more normally, then you can start studying how the USB system accesses /dev/sda.

Finally, you should try booting from an emergency disc like [System Rescue CD](http://www.sysresccd.org/) or [PartedMagic.](http://partedmagic.com/) These tools should enable you to run filesystem diagnostic tools, such as fsck, on your Linux partitions; or if *they* show the same problems as your USB installations, that will be strong evidence that the partition table itself is somehow causing the problem with keyboard mapping.

---

### Post by ndrli on 2010-04-07
Thank you for all inputs from all of you, especially for [srs5694]("http://ubuntuforums.org/member.php?u=1032238")'s suggestion to remove the hard disk. I just removed the hard disk from the computer. I got the same problems. So it is nothing to do with the partitions. My problems started at the time I re-partitioned hard disk, that made me to suspect the partition..

So, for now I will keep current partitions.

I did not install system on USB drive, but booted from LiveUSB (USB made from LiveCD's iso file by Unetbootin). So, LiveUSB may not be always good (That is different issue).

Thank you again.

---

