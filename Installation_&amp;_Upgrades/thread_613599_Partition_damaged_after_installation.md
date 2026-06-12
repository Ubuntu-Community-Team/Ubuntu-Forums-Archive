---
title: "Partition damaged after installation"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by cheaptrick on 2007-11-15
hi there, i'm pretty new here.

so here it goes

/dev/hda1   *           1        2327    18691596   83  Linux
/dev/hda2            2328        4865    20386485    f  W95 Ext'd (LBA)
/dev/hda5            3117        4865    14048842+   b  W95 FAT32
/dev/hda6            2328        2434      859414+  82  Linux swap / Solaris

before installation, i place all my stuff in an extended partition (hda5), leaving no free space
i use guided (use free space) during installation.
After the installation, i found that hda5 is nolonger accessible. I ran Pmagic live cd, and discovered that the linux swap(hda6) was created from within the extended partition. This is strange because the extended partition was previously occupied fully, its as though hda6 is created out of no where.

so help anyone?

---

### Post by Sef on 2007-11-15
1) Partition Magic and GNU/Linux do not get along real well.

2) Use [Gparted]("http://gparted.sourceforge.net"), it is the what Ubuntu uses.

3) Are you dual booting?

4) How big is hda5?

---

### Post by cheaptrick on 2007-11-15
no i'm not dual booting
hda 5 is approx 13gb

---

### Post by bulldog on 2007-11-15
Can you boot the live cd and open a terminal?
Post the output of```
sudo fdisk -l
``` small L not a one

---

### Post by cheaptrick on 2007-11-15
ok i've installed gparted.
hope this will give u a clearer picture
heres how it looks like 
[IMG]http://i6.photobucket.com/albums/y237/the_cheaptrick/Screenshot.jpg[/IMG]

previously when the hda6 wasnt created, hda2 was made up of hda5 and the unallocated only, which totals to approx 18.6 gb
after hda6 was created it seems that the total harddisk space for hda2 has increased to 19.44gb, while hda1 remains constant.
As a result of that, hda5 becomes inaccessible

---

### Post by cheaptrick on 2007-11-15
i boot the live cd and open the terminal
and i got this

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbacebace

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2327    18691596   83  Linux
/dev/hda2            2328        4865    20386485    f  W95 Ext'd (LBA)
/dev/hda5            3117        4865    14048842+   b  W95 FAT32
/dev/hda6            2328        2434      859414+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by bulldog on 2007-11-15
Why is there so much unallocated space unused?
The swap could be easely created from that,why it didn't,beats me.
I think it has to do with  something you did with  PMagic.
It's known PM and linux are not the best friends.

But I have no solution on hand,how to recover your data,and that's the most important thing,I guess.

---

### Post by cheaptrick on 2007-11-15
well actually previously the unallocated wasnt there, it was fully occupied too. But it was accesible, so i copied everything from it into hda1, then delete that partition so it becomes unallocatied. is it possible to delete the swap, and create a new swap from unallocated?

---

### Post by bulldog on 2007-11-15
> **cheaptrick said:**
> well actually previously the unallocated wasnt there, it was fully occupied too. But it was accesible, so i copied everything from it into hda1, then delete that partition,. so is it possible to delete the swap, and create a new swap from unallocated?
that shouldn't be a problem,you can delete what you want and create new partitions,as long as you don't touch your data partition.

---

### Post by cheaptrick on 2007-11-15
it didnt work out, deleted the linux swap, the unallocated increases accordingly, overall size of hda2 remains constant.
it seems that hda2 is inflated artificially somehow, i need to get it back to its original size

---

### Post by bulldog on 2007-11-15
> **cheaptrick said:**
> it didnt work out, deleted the linux swap, the unallocated increases accordingly, overall size of hda2 remains constant.
i need to get hda2 back to its original size.,

Yes I could have told you that,sry.
I have no solution for you,maybe someone comes around who have,just wait a while.

---

### Post by Sef on 2007-11-15
Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").  Maybe that can resolve your problem.

---

### Post by cheaptrick on 2007-11-15
i have that.
how exactly do i use it?
change geometry?

---

### Post by cheaptrick on 2007-11-15
whoa it worked! i dunno what i did with testdisk, but it worked! i got back my partition .
thanks

---

