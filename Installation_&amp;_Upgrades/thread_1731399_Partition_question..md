---
title: "Partition question."
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2011-04-17
Please see the attached screenshot displaying the current partitions I have set up.

I tried to move the unallocated space to SDA1 NTFS, but GParted would not allow it. 

I intend to free up more space from SDA3 EXT3 and would like to combine all the unallocated space with the 5GB from SDA1 NTFS for a new partition so that none is going to waste, is this possible? 

Maybe if I delete SDA1 NTFS it will allow me bring that space down to the unallocated? I wanted to ask first before the deleting so the installation of a new secondary OS to accompany Ubuntu 10.10 will go as smoothly as possible.

---

### Post by Elfy on 2011-04-17
It wouldn't let you move it and _then_ add it to sda1? 

If you are intending to then add more unallocated space I'd be inclined to do the resize of sda3 and then do the moving and adding in one go.

If you're actually going to be installing a linux os in the new bigger sda1 then you'd need to delete it and make it a linux filesystem anyway.

Make sure you've got backups.

It's likely to take a while to do these operations. Don't assume it's hung.

---

### Post by coffeecat on 2011-04-17
The 5GB unallocated space is at the end of the drive, sda1 is at the beginning. I.e. they are not contiguous. You cannot combine non-contiguous space into one partition.

If you want to delete sda1 and use the freed 5GB together with the presently unallocated 5GB and anything you free from sda3 to create a new partition, you would need to bring all the freed space together. The only way of doing this is to move partitions, which takes a long time and is not without risk. In your case you would have to delete sda1 and then enlarge (not move) your extended sda4 partition backwards towards the beginning of the disk. Then you would be able to move sda5 backwards and then shrink sda4 down again. Then move sda2 backwards. Then move sda3 backwards after which you would have sda3 followed by 10GB free space. Whew! Not something I would want to do. It might be quicker for you to backup everything, create a new partition layout and reinstall.

**EDIT**: another thought. You said, "I tried to move the unallocated space to SDA1 NTFS, but GParted would not allow it." If you were doing this from the live CD, it would have mounted the swap partition and effectively prevented you from moving anything. You would need to right-click on the swap partition and "swapoff" first, although I see from your screenshot that the swap partition isn't actually mounted.

---

### Post by Dáire Fagan on 2011-04-17
> **forestpiskie said:**
> It wouldn't let you move it and _then_ add it to sda1? 
 
 
 Have not yet tried to move it, just resize it.
 
 > **coffeecat said:**
> The 5GB unallocated space is at the end of the  drive, sda1 is at the beginning. I.e. they are not contiguous. You  cannot combine non-contiguous space into one partition.

Suspected, and now understood, thanks for confirming.

> **coffeecat said:**
> 
 In your case you would have to delete  sda1 and then enlarge (not move) your extended sda4 partition backwards  towards the beginning of the disk. Then you would be able to move sda5  backwards and then shrink sda4 down again. Then move sda2 backwards.  Then move sda3 backwards after which you would have sda3 followed by  10GB free space. Whew! Not something I would want to do. It might be  quicker for you to backup everything, create a new partition layout and  reinstall.

Would this mean there would not be any SDA1 when finished, if so would  it not be *neater* to bring the space to the front of the disk?

> **coffeecat said:**
> It might be  quicker for you to backup everything, create a new partition layout and  reinstall.

> **forestpiskie said:**
> It's likely to take a while to do these operations. Don't assume it's hung.

Have you  any idea how long all this would take, and I won't expect you to be  exact, but 12 hours, 24 perhaps?

On the idea of backing up everything and reinstalling, I do not have another drive to  back up my / (SDA5) and /~ (SDA3) partitions on, but if it would speed  things up all I really need to keep is /~ and could reinstall everything else?

It may be too much work and risk just for 5GB, even though 5GB is worth  more to me than most considering the total size of my HDD. I hope to  upgrade to a much bigger drive over the next few months anyway...

What do you think? Maybe I could just abandon the 5GB SDA1 and free up  some stuff less essential than the rest from SDA3 to create 30GB or so  more room for the secondary OS?

> **coffeecat said:**
> **EDIT**: another thought. You said, "I tried to move the unallocated  space to SDA1 NTFS, but GParted would not allow it." If you were doing  this from the live CD, it would have mounted the swap partition and  effectively prevented you from moving anything. You would need to  right-click on the swap partition and "swapoff" first, although I see  from your screenshot that the swap partition isn't actually  mounted.

Swap would have been how it is in screenshot, but good to know, thanks :)

Also to clarify, I tried to resize SDA1 NTFS after creating the unallocated 5GB, and I tried doing this without moving it first, bad choice of words on my part.

May be able to get a lend of an external HDD for backing up.

> **baliromavilas said:**
> Is this possible to run window xp and ubuntu os at a time, at one pc ?? Is it ok for trying..

Yes it is possible, that is what I do at the moment. Well that is to say I dual boot Ubuntu 10.10 and Windows XP for when I really *have* to use Windows for something, they do not run at the same time but I think you meant is it possible to choose which one when booting the computer.

---

### Post by Elfy on 2011-04-17
> **dusf said:**
> Yes it is possible, that is what I do at the moment. Well that is to say I dual boot Ubuntu 10.10 and Windows XP for when I really *have* to use Windows for something, they do not run at the same time but I think you meant is it possible to choose which one when booting the computer.

You got spammed.

---

### Post by Dáire Fagan on 2011-04-17
> **forestpiskie said:**
> You got spammed.

Link?

---

### Post by coffeecat on 2011-04-17
> **dusf said:**
> Would this mean there would not be any SDA1 when finished, if so would  it not be *neater* to bring the space to the front of the disk?

It would be peculiar, but not impossible, to have no sda1. Equally it would be unusual, but not impossible, to have an extended partition first. You may be right about bringing the space to the front. However, the reason I suggested thinking about completely redoing the partition layout is that you have only one logical partition (sda5) in your extended partition. Because of the 4 primary partition (or 3 primary and one extended) limitation in the mbr partition table scheme, I prefer to make as many partitions into logicals as possible. This allows more flexibility. Since the only type of partition that **must** be a primary partition is a Windows partition with Windows boot files, practically everything else can be a logical partition. In your case it would perhaps be neater to have the swap partition as a logical partition.

Something to think about, anyway. :)

---

### Post by Elfy on 2011-04-17
> **dusf said:**
> Link?

It was in the sig of the post you replied to - it's gone now.

If you see odd posts - look at the sig - if it looks like spam please report it with the Report Abuse button

---

### Post by srs5694 on 2011-04-17
> **dusf said:**
> On the idea of backing up everything and reinstalling, I do not have another drive to  back up my / (SDA5) and /~ (SDA3) partitions on, but if it would speed  things up all I really need to keep is /~ and could reinstall everything else?

If you're running without backups, you're playing with fire. Hard disks can and do fail suddenly and without warning. Bugs and user errors can and do wipe out whole disks in a moment. Partition resizing and moving operations are particularly risky, but they aren't the only risks. So: Go buy appropriate backup tools (an external hard disk, a tape unit, a stack of recordable DVDs, or whatever) and make that backup happen. If you lack the funds to do so now, make this a budget priority.

On a more general note about your configuration, one way to make use of scattered disk space is to employ an [LVM](http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/) configuration. This is an extra layer that enables you to easily combine free space from all over the disk for use in a filesystem, to resize filesystems without moving them, etc. One cost is added complexity; it takes some effort to figure it all out and implement it. Recovery tools like TestDisk might also be less likely to be able to recover filesystems in case of serious damage. In your case, you couldn't easily add the LVM space to your big block in /dev/sda3, but you could mount it as a subdirectory within that space until you can do a more thorough reorganization. (If you were to add LVM to your current setup, you'd do so by creating new LVM space and using it in addition to the partitions you've got now; you can't easily convert existing partitions into LVM volumes.)

As to the primary/logical thing, you can sometimes convert between types with my [FixParts](http://www.rodsbooks.com/fixparts/) program; however, the only change I can guarantee you could easily make with your current setup would be to convert /dev/sda5 into a primary partition, and that's not the way you want to go. If you were to delete your swap partition, though, you could convert your big /dev/sda3 into a logical partition and create a new swap partition. You might be able to convert /dev/sda3 into a logical even without deleting your swap space, but I can't guarantee that; it depends on the sector-precise start and end points of your existing partitions. If you do some partition juggling, converting some partitions to logicals might simplify some things you might want to do with your current layout, but it depends on what you want to do. If you're not booting Windows on the disk, you could also convert from the Master Boot Record (MBR) format you're using to GUID Partition Table (GPT) using [GPT fdisk (gdisk or sgdisk)](http://www.rodsbooks.com/gdisk/). GPT lacks the primary/extended/logical distinction of MBR and supports up to 128 partitions by default, so you could add more partitions to your heart's content. That won't help you with the need to resize and/or move partitions to consolidate your free space, though.

---

### Post by Dáire Fagan on 2011-04-24
> **srs5694 said:**
> If you're running without backups, you're playing with fire. Hard disks can and do fail suddenly and without warning. Bugs and user errors can and do wipe out whole disks in a moment. Partition resizing and moving operations are particularly risky, but they aren't the only risks. So: Go buy appropriate backup tools (an external hard disk, a tape unit, a stack of recordable DVDs, or whatever) and make that backup happen. If you lack the funds to do so now, make this a budget priority.

On a more general note about your configuration, one way to make use of scattered disk space is to employ an [LVM]("http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/") configuration. This is an extra layer that enables you to easily combine free space from all over the disk for use in a filesystem, to resize filesystems without moving them, etc. One cost is added complexity; it takes some effort to figure it all out and implement it. Recovery tools like TestDisk might also be less likely to be able to recover filesystems in case of serious damage. In your case, you couldn't easily add the LVM space to your big block in /dev/sda3, but you could mount it as a subdirectory within that space until you can do a more thorough reorganization. (If you were to add LVM to your current setup, you'd do so by creating new LVM space and using it in addition to the partitions you've got now; you can't easily convert existing partitions into LVM volumes.)

As to the primary/logical thing, you can sometimes convert between types with my [FixParts]("http://www.rodsbooks.com/fixparts/") program; however, the only change I can guarantee you could easily make with your current setup would be to convert /dev/sda5 into a primary partition, and that's not the way you want to go. If you were to delete your swap partition, though, you could convert your big /dev/sda3 into a logical partition and create a new swap partition. You might be able to convert /dev/sda3 into a logical even without deleting your swap space, but I can't guarantee that; it depends on the sector-precise start and end points of your existing partitions. If you do some partition juggling, converting some partitions to logicals might simplify some things you might want to do with your current layout, but it depends on what you want to do. If you're not booting Windows on the disk, you could also convert from the Master Boot Record (MBR) format you're using to GUID Partition Table (GPT) using [GPT fdisk (gdisk or sgdisk)]("http://www.rodsbooks.com/gdisk/"). GPT lacks the primary/extended/logical distinction of MBR and supports up to 128 partitions by default, so you could add more partitions to your heart's content. That won't help you with the need to resize and/or move partitions to consolidate your free space, though.

Thanks, and thanks to all :)

Managed to get it set up like this:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
/dev/sda1               1        1305    10482381    7  HPFS/NTFS
/dev/sda2   *        1306        3263    15727635    7  HPFS/NTFS
/dev/sda3            3264       12805    76646084+   5  Extended
/dev/sda4           12806       38913   209712510   83  Linux
/dev/sda5            3264        3295      257008+  83  Linux
/dev/sda6            3296        3426     1052226   83  Linux
/dev/sda7            3427        3948     4192933+  82  Linux swap / Solaris
/dev/sda8            3949        5906    15727603+  83  Linux
/dev/sda9            5907       12805    55416186    7  HPFS/NTFS

Disk /dev/sdb: 1015 MB, 1015021568 bytes
/dev/sdb1   ?      398636      983425  2283019262   72  Unknown
/dev/sdb2   ?       86419     1078237  3872056480   65  Novell Netware 386
/dev/sdb3   ?      957932     1949749  3872056384   79  Unknown
/dev/sdb4   ?     1478321     1478349      110998    d  Unknown

```

Win XP, Win7, /boot, /opt, SWAP, /, Storage, /Home.

---

