---
title: "Partition table out of wack"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by AndrewTheArt on 2007-07-24
Can anybody determine what the heck is going on with my partition table?
Here's a dump of it using fdisk in Knoppix...

```
Disk /dev/hda1: 55.5 GB, 55545283584 bytes
16 heads, 63 sectors/track, 107625 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

	 Device Boot	  Start		 End	  Blocks   Id  System
/dev/hda1p1   ?	  216399	 1904881   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/hda1p2   ?	  723265	 1262922   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/hda1p3   ?	  167316	  167316		   0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/hda1p4		 2671568	 2671619	   25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```
Here's some background - I originally had Windows XP installed on around 50-ish GB as the first partition, and the next partition (for openSUSE) was an extended partition split ito three logical drives... Linux root (/), a Home partition, and of course a swap partition. It was 30gb. (Yes, my HDD is 80gb, even though Knoppix can only see 55.5gb of them. This would be one of my issues, I suppose.)

However, the GParted liveCD was trying to resize the swap when an error occured, and it erased my partition table. So I restored the WIndows partition table using a recovery disk.

Here's some more info running fdisk's "Verify partition" command...

```
Partition 1 does not end on cylinder boundary.
Partition 1: head 102 greater than maximum 16
Partition 2 does not end on cylinder boundary.
Partition 2: head 115 greater than maximum 16
Warning: partition 1 overlaps partition 2.
Partition 3 does not end on cylinder boundary.
Partition 3: head 116 greater than maximum 16
Total allocated sectors 1701990412 greater than the maximum 108486882
```
Can anybody read between the very confusing lines here and tell me how to delete the three screwed up logical partitions saftely? (Without destroying the working Windows partition?) This is going to require a true expert )=

(Posted this on the Ubuntu forums to pool the collective knowledge of all Linux users)

---

### Post by Circuit99 on 2007-07-26
Best advice is to BACKUP all your data.

Knoppix will only see what it can mount. (Generally) 

You can use Parted Magic  partition tool if your not comfortable with Knoppix:

[http://partedmagic.com/](http://partedmagic.com/)

got the info from here, a good source for OS or other repair boot disk:

[http://distrowatch.com/table.php?distribution=partedmagic](http://distrowatch.com/table.php?distribution=partedmagic)

[http://distrowatch.com/](http://distrowatch.com/)

I would keep all partitions with fat32 or ntfs as seen by gparted, look at screen shots of gparted @ Parted Magic web site.

Basically anything  with fat or ntfs filesystem is windows partitions. 

Windows is always setup as the primary partition and Linux sets up behind it in the logical extension or whats left unformatted.  

Next step is delete  all the other partitions. 

Basically anything like ext2, ext3 or swap.

What I think you have are 4 partitions, in this order 

(1) Windows
(2) Extended logical Partition
(3) Swap
(4) Linux Home

You can delete 2,3,4 with no trouble to windows.(This is an educated guess)

You don't state if you can boot into windows or not or how many window partitions there are?

If you can boot into windows I would label then such as>  Mydrive1.

This way you easily identify under>   Mountpoint  in gparted as >  /media/Mydrive1



Good Luck :popcorn:

PS: Be prepared to lose everything so you don't have to.

---

