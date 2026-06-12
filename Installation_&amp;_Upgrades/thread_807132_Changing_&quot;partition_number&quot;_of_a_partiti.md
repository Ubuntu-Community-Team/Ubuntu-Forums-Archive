---
title: "Changing &quot;partition number&quot; of a partition"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by BattlePanic on 2008-05-25
I have started preparing my hard disk for a new linux installation by using gparted to resize, copy, and move my three existing partitions such that I now have unallocated space at the end of my drive.  gparted now shows my drive's physical layout to be as follows:

```

-------------------------------------------------------------------------
| /dev/sda1 (NTFS)  | /dev/sda4 (NTFS) | /dev/sda2 (ext3) | Unallocated |
-------------------------------------------------------------------------
```

Due to all the moving, deleting, and reshuffling, the partition numbers are now out of order.  Is there are way to manually change the partition numbers to something that matches their physical ordering?

Also, I realize my swap space isn't shown here.  I deleted it in the shuffle and haven't created a new one yet.  It's on my to-do list.

---

### Post by dstew on 2008-05-25
I think if you move partitions around, they keep their same numbers. The only way I know of to change their numbers is to delete and re-create them. Maybe some partition management program, like TestDisk, can do that, but I have no experience with it.

---

### Post by Devport on 2008-05-25
Get SystemRescueCD and at the CD boot prompt type "ranish". With it you can change the partition numbers as you like ( on the left side of the partitions are the partition numbers ).

- Ranish is a pretty old piece of software so be careful.
- Windows cant cope with a different partition number so Windows has to have the partition number it had when it got installed ( at least the booting Windows partition - tested with XP, dont know if Vista is able to manage it ). I dont know about a hack to make Windows realize that it is now on a different partition.
- Make sure you edit the correct disk
- Note that maybe you will have to change grub boot manager entries / fstab ( absolute device references, e.g. /dev/sda1 or (hd0,0) ).
- Dont forget to give every partition a unique number otherwise you will loose partitions
- Make sure that every partition is listed in the bottom left partition list.

You do it at your own risk !
( I never had a problem yet I know what I do ... )

After all partition numbers are not too important anyways.

Edit : a tool called fdisk ( which should also be available with SystemRescueCD ) seems to be able to change partition numbers as well in expert mode.

You probably should not try to change partition numbers from within a system on the disk itself ( e.g. by running fdisk from your linux partition ) because it may corrupt everything...

---

### Post by BattlePanic on 2008-05-25
Thanks for the detailed info.  The process does sound a little dicey.  Perhaps I can live with partition numbers that are out of order.

Incidentally, the Windows install on /dev/sda4 was previously located at /dev/sda5.  I made a post, which can be found [here]("http://ubuntuforums.org/showthread.php?t=647954"), that describes my troubles booting into the second Windows install.  I eventually had to modify the Windows boot.ini and change "partition(2)" to partition(3).

After moving this Windows install to a new partition (from /dev/sda5 to /dev/sda4) I can still boot into it by referring to it as partition(3) in the boot.ini.  If gparted is telling me the partition was /dev/sda5 and is now /dev/sda4, why on earth do I need to tell the Windows boot loader that it's partition(3)?  This is very confusing.

---

### Post by meierfra. on 2008-05-25
> If gparted is telling me the partition was /dev/sda5 and is now /dev/sda4, why on earth do I need to tell the Windows boot loader that it's partition(3)?

Windows does not count an "extended partition" as a partition. So if one of sda1, sda2 or sda3 is an extended partition, it would make /dev/sda4   the third partition. But I'm not sure that this applies in your case. I'm also not sure whether windows uses the physical order or the order in the partition table,


> Is there are way to manually change the partition numbers to something that matches their physical ordering?

testdisk (see my signature for more information) does that quite  easily.


Install testdisk

```
sudo apt-get install testdisk
```

run testdisk

```
sudo testdisk /dev/sda
```


Press "enter" a few times to accept the defaults. (Maybe once you have to type "y" instead of "enter")


Do  this until you see 

[QUIT]  [SEARCH!] [Write]
         Search deeper, try to find more partitions.

at the bootom of the screen. Use the arrow key to select "Write" and press "Enter". Then follow instructions on the screen to quit testdisk.

But be aware that changing the partition order might mean that you have to edit "boot.ini" (and if you have ubuntu:  edit "menu.lst" and reinstall grub)

---

### Post by Devport on 2008-05-25
Thank you for the info on boot.ini !

---

### Post by BattlePanic on 2008-05-25
> **meierfra. said:**
> Windows does not count an "extended partition" as a partition. So if one of sda1, sda2 or sda3 is an extended partition, it would make /dev/sda4   the third partition. But I'm not sure that this applies in your case. I'm also not sure whether windows uses the physical order or the order in the partition table,

In my case the extended partition is encapsulating the unallocated space at the end of my disk so I wouldn't think it would be a factor.  Any way I look at the physical ordering or numbering, I can't figure out why Windows would interpret that partition as being the third one.  Moreover, I would have thought that changing the partition number as well as it's physical ordering would require an edit of boot.ini but apparently it did not.

---

### Post by meierfra. on 2008-05-25
> In my case the extended partition is encapsulating the unallocated space at the end of my disk so I wouldn't think it would be a factor.

Yes it does. The extended partition is /dev/sda3. So your partition table looks like this

/dev/sda1 NTFS
/dev/sda2 ext3
/dev/sda3 Extended 
/dev/sda4 XP

So it seems that Windows counts  the partition in the order of the partition table, but ignores the extended partition. This makes  your XP partition  the third partition.

---

