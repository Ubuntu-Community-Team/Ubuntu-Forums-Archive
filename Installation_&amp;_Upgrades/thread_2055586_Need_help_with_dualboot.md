---
title: "Need help with dualboot"
date: 2012-09-09
forum: Installation &amp; Upgrades
---

### Post by gioortuno on 2012-09-09
I have two hard drives both of 500GB. I have windows 7 on it and the other one has two partitions one with 450gb and the other with 50gb. On the 50gb I installed the consumer preview of windows 8. I want to get rid of Windows 8 and install Ubuntu there instead. For some reason windows 7 won't let me format that partition and when I try to install Ubuntu it wants to delete both the 450 partition and 50 partition and merge it into a 500. I tried using the manual partitioning tool, but I kept getting a **no root file system is defined **message.

I would greatly appreciated if someone could help me out with this problem or point me towards some threads or solutions.

Thanks in advance!

ps. I read some stuff about creating ext4 ,ext2, swap, primary, and logical partitions. Any information about this would be greatly appreciated too!

---

### Post by lah7 on 2012-09-09
The GParted Live CD would be useful when seeing all partitions on your hard drives and managing them, since the Live CD/USB won't be mounting any of the partitions which may affect partitioning.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

My advise would be to put in the GParted Live CD/USB, delete the 50GB partition ( an NTFS partition containing Windows 8 ) and leave it unallocated (you could format it as ext4 at this point). When you next boot the Ubuntu installation CD, you should be able to specifically install to that empty 50GB of free space or alongside Windows 7.

---

### Post by darkod on 2012-09-09
There might be some error or issue with the disk, that's why win7 can't format the partition and ubuntu doesn't recognize the partitions properly.

Otherwise, the no root defined message when installing manually is because you never specified which partition you want to use as /.

If it's existing partition, after you select it click the Change button below the list, in the Use As field select ext4, tick the format box, and set mount point /.

The swap is used when the memory runs low, like the swap file in windows. Ubuntu can work without it, but usually it's installed with at least two partitions, / and swap.

However, you might need to detect if there is anything messed up with the partition table before you install anyway. Did you try printing the partitions from live mode?

Boot the ubuntu cd in live mode and in terminal try:
```
sudo fdisk -l
sudo parted -l
```

That should show all disks, partitions and filesystems.

---

### Post by Karlchen on 2012-09-09
> **lah7 said:**
> the Live CD/USB won't be mounting any of the partitionsQuite frankly speaking, your statement is not covered by what I see and do when running a Ubuntu live system.
The Ubuntu live systems (starting with 9.10 up to 12.04) have always allowed to mount any partitions on my (SATA / EIDE) harddisks.

In order to (re)partition a disk in the course of a Ubuntu installation the live CD alone has always been sufficient.

Karl

---

### Post by gioortuno on 2012-09-10
Thanks for all the help!

I think the main reason Windows 7 won't allow me to format the 50GB partition it's because it appears as a System Partition. Would it be OK if I format the 50GB partition with the partitioning tool during the ubuntu installation as a ext4 partition? Will that also eliminate the option for booting as Windows 8 that appears when I turn on my computer?

---

### Post by darkod on 2012-09-10
If that's the system partition, it's almost certain windows has boot files on it.

If you delete it, windows won't be able to boot. Whether there are only files from win8 or also from win7 depends on how you installed.

---

### Post by Mark Phelps on 2012-09-10
> **gioortuno said:**
> I have two hard drives both of 500GB. I have windows 7 on it and the other one has two partitions one with 450gb and the other with 50gb. On the 50gb I installed the consumer preview of windows 8. I want to get rid of Windows 8 and install Ubuntu there instead. ...

Then ... boot into Win8 and use the option to select Win7 as the default.

This will then use the Win7 boot loader to boot Windows.

After that, you can remove Win8 with no problems.

---

### Post by gioortuno on 2012-09-13
Thanks again for all the help! I have never seen such a helpful community!

So here is what I did, I put in a windows 8 cd completely deleted the 50gb with windows 8 and extended the 450gb partition to 500gb (lets call it partition b). I formatted the other 500gb partition (partition a) and installed windows 8 on it (For some reason it made partition b the system partition). After that i went into windows shrank the b to 450gb left the rest unallocated, and created two partititons an ext4 for ubuntu and a 1gb for swap.

EDIT: For some reason whenever I turn onf my computer it goes directly to windows 8. Is there a way for it to let me choose which system do I wanna go to?

---

### Post by darkod on 2012-09-14
You should have been careful with the boot flag because windows depends on it and puts the boot files there. That's why the partition b is the system partition even though you installed on partition a.

Now you need to remember this, because if you reformat or delete partition b windows will not boot even though you "think" it's installed on a and b shouldn't matter.

As for not booting, you said you have two disks. Maybe grub2 is on the other disk and you are booting from the one that has windows bootloader so it boots windows straight away. Try booting from the other disk.

---

