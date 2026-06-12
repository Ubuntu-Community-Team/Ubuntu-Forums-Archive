---
title: "Help me merge Partitions - Lubuntu 19"
date: 2019-05-30
forum: Installation &amp; Upgrades
---

### Post by navin2004 on 2019-05-30
Please help me solve this partition mess. I had an old HP Laptop running Vista Home with a 160gb hard drive. It was already partitioned into 3. 
Partition 1 was a 120 GB with Windows Vista OS, Partition 2 was some 7 GB Hidden Recovery partition from factory and Partition 3 I created for User data in Windows was 30 GB.

2 years ago I had created a 20 GB Partition out of the 120GB to install Lubuntu 13 which was all fine. I recently then opened up that laptop and saw messages that newer versions were available. So I went through 13 to 16 and then 18 upgrade. I could not go from 18 to 19 as I had the 32 bit Lubuntu and support for that had ended. I looked up and my laptop supports 64 bit and it had a Centrino Duo processor. So after a lot of trouble trying to boot into a Bootable v19 Live CD, I finally was able to boot into using a DVD Drive.
But the installation of v19 did not go smooth. I selected the option to replace v18 with v19 and it gave some error with that partition. So I gave up and took out my Windows 30gb partition and it installed fine on that. But after booting into new v19 and looking through KDE Partition manager I saw an unallocated block between the 100 gb Windows partition and this new v19 on the 30 gb partition. I tried to remove/merge and it did not work. 

So I booted into Vista and used Disk Management to see if I could merge this 20 GB partition into the 30GB Lubuntu v19, but it would not let me. I then installed AOEMI Partition Magic and deleted this 20 GB Unallocated partition. All hell broke loose and GRUB was now going into rescue mode when starting up. So I once again used Live CD to reinstall v19 and this time also went through various options on the partition screen on install and looks like this time it installed on this previous 20 gb partition by "installing along side". Now I had the 30 GB unallocated one, so I mounted that after booting into Lubuntu.

I now have way too many partitions than I like. I am not yet ready to delete Vista and use entire drive for Lubuntu which was one of the option during install. All I want is 3 partitions. The 100 GB with Vista, the 7 GB Windows recovery partition from factory and rest all to Lubuntu.

I ran sudo fdisk -lu and sudo parted -l to see if it gives enough info for experts here to help.
```

Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Disk model: WDC WD1600BEVS-6
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6125db67

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *           63 198969577 198969515 94.9G  7 HPFS/NTFS/exFAT
/dev/sda2       248903680 298823679  49920000 23.8G 83 Linux
/dev/sda3       298825065 312576704  13751640  6.6G  7 HPFS/NTFS/exFAT
/dev/sda4       198981569 248902624  49921056 23.8G  f W95 Ext'd (LBA)
/dev/sda5       198981632 212934880  13953249  6.7G 83 Linux
/dev/sda6       233912320 238086143   4173824    2G 82 Linux swap / Solaris
/dev/sda7       212934882 233906399  20971518   10G 83 Linux
/dev/sda8       238086207 248901631  10815425  5.2G 83 Linux

Partition table entries are not in disk order.

```
```

$ sudo parted -l
Model: ATA WDC WD1600BEVS-6 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type      File system     Flags
 1           32.3kB  102GB  102GB   primary   ntfs            boot

 4          102GB   127GB  25.6GB  extended                  lba

 5          102GB   109GB  7144MB  logical   ext4

 7          109GB   120GB  10.7GB  logical   ext4

 6          120GB   122GB  2137MB  logical   linux-swap(v1)

 8         122GB   127GB  5537MB  logical   ext4

 2      127GB   153GB  25.6GB  primary   ext4
 3      153GB   160GB  7041MB  primary   ntfs

```

---

### Post by CatKiller on 2019-05-30
> **navin2004 said:**
> But after booting into new v19 and looking through KDE Partition manager I saw an unallocated block between the 100 gb Windows partition and this new v19 on the 30 gb partition. I tried to remove/merge and it did not work. 

You can't edit a partition that's in use. You have a swap partition that's in there.

> So I booted into Vista and used Disk Management to see if I could merge this 20 GB partition into the 30GB Lubuntu v19, but it would not let me. I then installed AOEMI Partition Magic and deleted this 20 GB Unallocated partition. All hell broke loose and GRUB was now going into rescue mode when starting up.

You deleted the swap partition that was in there.

> All I want is 3 partitions. The 100 GB with Vista, the 7 GB Windows recovery partition from factory and rest all to Lubuntu.

Partitions aren't arbitrary containers, they are specific locations on the disc. In your case, you are at your maximum of 4 primary partitions for an MBR disc. You have an NTFS partition, an extended partition with a swap logical partition somewhere in the middle, an ext4 partition, and another NTFS partition. It is your extended partition that's confused you, I think.

One way to do what you want would be to boot from the live installer and turn off swap: you can't edit a partition in use, and the installer will use a swap partition if it's there. Then delete the swap partition and the extended partition that enclosed it, and move your ext4 partition to the left, and then finally extend the partition to the right. Then mount and chroot into that ext4 partition so that you can configure GRUB to not look for the (now destroyed) swap partition. You don't actually need a swap partition: these days, a swap file is fine.

A slightly simpler, but more brutal, way would be to do the deletions above, but also delete your ext4 partition. That will give you a single contiguous space to do a fresh install into.

---

### Post by Impavidus on 2019-05-30
The second part of the Lubuntu version number is important. 18.10 is as different from 18.04 as it is from 19.04. Be specific. The third part is not so important. 18.04.1 or 18.04.2 doesn't matter too much after installing the regular upgrades (except that before *.2 you don't automatically get the HWE stack).

Did you install Lubuntu 13.something 2 years ago? It was already dead by then. But that doesn't matter now. Windows Vista is dead too, BTW.

Windows partition manager can't handle Linux partitions. Linux partitioning tools can handle Windows partitions, but not very reliably. Best to use Windows tools for Windows partitions and Linux tools for Linux partitions.

Lubuntu 18.04 is a long term support release. It will be supported until April 2021. Lubuntu 19.04 is an interim release. It will be supported until January 2020. For most inexperienced users, I recommend 18.04, but you're free to use 19.04 if you wish.

If you wish to share files between Windows and Lubuntu, it's best to have a separate NTFS data partition. Using Lubuntu to directly access the Windows C partition may sometimes damage Windows. But if you don't wish to share any files, it's OK not to have one.

As CatKiller writes, you can simply delete all unwanted partitions and expand your sda2 containing Lubuntu, or delete that one too and use a fresh install. A fresh install can automatically use all continuous unallocated space.

---

### Post by navin2004 on 2019-05-31
> **CatKiller said:**
> You can't edit a partition that's in use. You have a swap partition that's in there.
I did not realize the 20 GB partition where previous v18 Lubuntu was installed was used as a swap partition.

> 
Partitions aren't arbitrary containers, they are specific locations on the disc. In your case, you are at your maximum of 4 primary partitions for an MBR disc. You have an NTFS partition, an extended partition with a swap logical partition somewhere in the middle, an ext4 partition, and another NTFS partition. It is your extended partition that's confused you, I think.
Yes pretty much, here is a picture from KDE Partition manager
[https://drive.google.com/open?id=1C6WVo_c7Uz6mzUhudijbWx-QLX2fuBJ2](https://drive.google.com/open?id=1C6WVo_c7Uz6mzUhudijbWx-QLX2fuBJ2)
[IMG]https://drive.google.com/open?id=1C6WVo_c7Uz6mzUhudijbWx-QLX2fuBJ2[/IMG]

> 
One way to do what you want would be to boot from the live installer and turn off swap: you can't edit a partition in use, and the installer will use a swap partition if it's there.
Ok, I will boot back from the live CD and see if I see this option anywhere. 

> 
 Then delete the swap partition and the extended partition that enclosed it, and move your ext4 partition to the left, and then finally extend the partition to the right. 


This is the part I want to understand correctly. How do I delete this swap partition which is /dev/sda6. In KDE Partition manager I only see an option to Deactivate Swap. I don't think I can delete the extended partitino that was enclosing the swap as the extended partition sda4 has sda7 which is of size 10gb and 5 gb is used and it has the / mount point and this is where I believe Lubuntu 19.04 is installed. I don't know where exactly Grub is installed, even that will go into rescue if I delete this enclosed partition. Also in partition manager when I right click /dev/sda4, I don't see an option to delete it, only Resize/Move. Maybe you meant the ext4 partition that is after the swap, sda8 to be moved to the left, after deleting swap partition, which will then add the space in sda8, sda6 into sda7 where Lubuntu is installed.

> 
Then mount and chroot into that ext4 partition so that you can configure GRUB to not look for the (now destroyed) swap partition. You don't actually need a swap partition: these days, a swap file is fine.
Sorry, you lost me here. I worked more on windows, so did not quite understand this part. So you are saying, if I was able to do the previous step, then I start Lubuntu normally and then mount the ext4 partition that is now a combination of sda2, sda8, sda6. I don't know how to chroot root into either, you mean type chroot in the terminal window. I read about this swap partition and it said something that Lubuntu creates it equal in size to your RAM. So looks like a file is all that was needed, instead of a logical partition.

Thank you again for taking time to read and explain. I will eventually learn Unix/Ubuntu/Lubuntu.

A slightly simpler, but more brutal, way would be to do the deletions above, but also delete your ext4 partition. That will give you a single contiguous space to do a fresh install into.[/QUOTE]

---

### Post by navin2004 on 2019-05-31
> **Impavidus said:**
> The second part of the Lubuntu version number is important. 18.10 is as different from 18.04 as it is from 19.04. Be specific. The third part is not so important. 18.04.1 or 18.04.2 doesn't matter too much after installing the regular upgrades (except that before *.2 you don't automatically get the HWE stack).

My appologies, I did not realize that. I believe it was 18.04 that I upgraded to after 13 to 16. And then when I saw more upgrade notification, it was going upto only 18.10 at which point got message that for 19, I need a 64 bit version.

> 
Did you install Lubuntu 13.something 2 years ago? It was already dead by then. But that doesn't matter now. Windows Vista is dead too, BTW.
Yes, you are right, it was more than 2 years ago. I was quickly jogging down my memory when I  got my new laptop and stopped using this HP one on which I am putting a new life into with Lubuntu. It was actually 4 years ago I think. I installed 13.x and gave it to my parents who were visiting that time to use it for internet serving as Vista was horribly slow. Yes, it is dead as well but as Lubuntu does not need a lot of space and I still have my legit copy of MS Office 2010 in Vista, I did not want to zap, but maybe I should and go full on with Lubuntu.

> 
Windows partition manager can't handle Linux partitions. Linux partitioning tools can handle Windows partitions, but not very reliably. Best to use Windows tools for Windows partitions and Linux tools for Linux partitions.
Got it will not touch sda1 and sda3 which are NTFS filesystem. Unfortunately, I think sd3 is gone case till I remove Vista completely as I see that at the bottom of my list of partitions in KDE Partition manager.

> 
Lubuntu 18.04 is a long term support release. It will be supported until April 2021. Lubuntu 19.04 is an interim release. It will be supported until January 2020. For most inexperienced users, I recommend 18.04, but you're free to use 19.04 if you wish.
Did not know that. I was just excited to see a new Lubuntu release after I started this laptop after 2 years. During the upgrade process, before I tried to go from 18.04 to 19.04, I briefly used 18.04 and now using 19,04, definitely like the new graphics interface in 19.04. On login screen as I well I see 3 different options for what look like graphical interfaces in 19.04.
I am a software engineer, but using windows mostly, so this is a machine for my RnD and to give to my son for his learning use as his gadget from school is a Chromebook.

> 
If you wish to share files between Windows and Lubuntu, it's best to have a separate NTFS data partition. Using Lubuntu to directly access the Windows C partition may sometimes damage Windows. But if you don't wish to share any files, it's OK not to have one.
Don't have any need for sharing files across the two O/S, but I do see the main windows vista partition and can mount it, but have not touched any files.

> 
As CatKiller writes, you can simply delete all unwanted partitions and expand your sda2 containing Lubuntu, or delete that one too and use a fresh install. A fresh install can automatically use all continuous unallocated space.
I hope these two screenshots will be viewable
[https://drive.google.com/open?id=1FvHko1tDaq0AcU6otrsNwtcrR99Krnen](https://drive.google.com/open?id=1FvHko1tDaq0AcU6otrsNwtcrR99Krnen)
[https://drive.google.com/open?id=1C6WVo_c7Uz6mzUhudijbWx-QLX2fuBJ2](https://drive.google.com/open?id=1C6WVo_c7Uz6mzUhudijbWx-QLX2fuBJ2)
I simply don't see an option to delete a partition in KDE. And I think Lubuntu is not in sda2, but in sda7. I can attempt a fresh install as well as I have no data in sda4 extended partition, which has these 4 sub-partitions. Unfortunately, when I was trying to install it in the first place, it did not let me reuse the partition where 18 was. The various partition options during installation where little confusing. I will grab a screenshot of what is shows for fresh install from the LiveCD before proceeding and paste back here. But looks like before I do it, I need to delete all these partitions using KDE except sda7 where Lubuntu OS is installed.

---

### Post by navin2004 on 2019-05-31
I booted from livecd and disabled the swap partition by going to terminal and issuing

sudo swapoff -a

I then tried to edit /etc/fstab using gedit as I read somewhere, but there was no entry for swap in it. So I then rebooted without Live cd and in KDE Partition manager it was showing the Deactivate Swap option, so I did that. And then when I right click on Swap, I see the delete option, but it gave me a warning and did not let me delete
[https://drive.google.com/open?id=1GoeuICoSjE7gbXQp0WqNuBrVUXm2jFrg](https://drive.google.com/open?id=1GoeuICoSjE7gbXQp0WqNuBrVUXm2jFrg)

It said to dismount partitions higher than this sda6 swap partition, but I don't think I can as that is where Linux is running. I tried and said target is busy/fileystem on partition /dev/sda7 could not be unmounted.
[https://drive.google.com/open?id=18otz6fXclerUQUOLpb_TS8qaovxM-TLQ](https://drive.google.com/open?id=18otz6fXclerUQUOLpb_TS8qaovxM-TLQ)

---

### Post by navin2004 on 2019-05-31
Apologies for the multiple updates. It finally clicked what you meant by brute install @CatKiller 
I booted in using LiveCD and deleted all those partitions, leaving just Vista and the Recovery partition and got back a single 47 GB Unused space. Fired up a new install into that free space and now I am all set to play with Ubuntu

[https://drive.google.com/open?id=11a25y2_r8HlpKsBqICA5CtzsQH4g0P4I](https://drive.google.com/open?id=11a25y2_r8HlpKsBqICA5CtzsQH4g0P4I)

---

### Post by CatKiller on 2019-05-31
> **navin2004 said:**
> This is the part I want to understand correctly. How do I delete this swap partition which is /dev/sda6. In KDE Partition manager I only see an option to Deactivate Swap. I don't think I can delete the extended partitino that was enclosing the swap as the extended partition sda4 has sda7 which is of size 10gb and 5 gb is used and it has the / mount point and this is where I believe Lubuntu 19.04 is installed. I don't know where exactly Grub is installed, even that will go into rescue if I delete this enclosed partition. Also in partition manager when I right click /dev/sda4, I don't see an option to delete it, only Resize/Move. Maybe you meant the ext4 partition that is after the swap, sda8 to be moved to the left, after deleting swap partition, which will then add the space in sda8, sda6 into sda7 where Lubuntu is installed.

OK, I was assuming that sda2 was your /. Should you wish to keep sda7, you'd need to (once you've deleted sda2) make the containing extended partition (sda4) bigger before you can use the space. It will be simpler to just get rid of all of them and install afresh in the empty space. You won't be able to delete the extended partition before you've deleted the logical partitions inside it.

Remember, you must do this from an install disc: you can't change a partition that's mounted, and you can't unmount it if you're running things from it.

> Sorry, you lost me here. I worked more on windows, so did not quite understand this part. So you are saying, if I was able to do the previous step, then I start Lubuntu normally and then mount the ext4 partition that is now a combination of sda2, sda8, sda6. I don't know how to chroot root into either, you mean type chroot in the terminal window. I read about this swap partition and it said something that Lubuntu creates it equal in size to your RAM. So looks like a file is all that was needed, instead of a logical partition.

chroot is a way of running the machine in one environment, but pretending that it's a different one. You can use the framework of running the live environment, but make changes to the hard drive as if you'd booted from that instead. It's really handy sometimes, particularly if your computer wouldn't be able to boot otherwise. You just *chroot /some/mounted/place/* and then subsequent commands would be run as it /some/mounted/place/ was actually /. Useful when you need to make changes to Grub, or do package management, and the like, to an otherwise non-booting computer. It's just a much nicer environment than trying to do the same thing in rescue mode or BusyBox.

So, if you did manage to (from the live cd) get rid of all the partitions other than the one you want to be /, your computer would still be looking for the old swap partition, and would fail to boot when it can't find it, as you found before. So you'd need to fix that, by editing Grub's configuration file, and then running update-grub as if you were already using that /. That's what the chroot would be for.

In this case, booting from the live cd, turning off swap, deleting 
[LIST]
[*]sda2 
[*]sda8 
[*]sda7 
[*]sda6 
[*]sda5 
[*]sda4 
[/LIST]
then installing into the one big empty space is probably the way to go.

---

### Post by CatKiller on 2019-05-31
> **navin2004 said:**
> Apologies for the multiple updates. It finally clicked what you meant by brute install @CatKiller 
I booted in using LiveCD and deleted all those partitions, leaving just Vista and the Recovery partition and got back a single 47 GB Unused space. Fired up a new install into that free space and now I am all set to play with Ubuntu

[https://drive.google.com/open?id=11a25y2_r8HlpKsBqICA5CtzsQH4g0P4I](https://drive.google.com/open?id=11a25y2_r8HlpKsBqICA5CtzsQH4g0P4I)

Awesome! Glad you got it sorted :)

---

