---
title: "Move Resizing Partition &amp; Restoring GRUB 2"
date: 2012-11-24
forum: Installation &amp; Upgrades
---

### Post by just_ken_here on 2012-11-24
Hi

I have partition : [http://imgur.com/Gbx9l](http://imgur.com/Gbx9l)

SDA1 = W7
SDA3 = Ubuntu
SDA2 = just for BACK UP

I would like to Shrink the Beginning of the Ubuntu Partition ( SDA3 ).
So that the SDA1 ( W7 ) can grow... as you can see it is fattening up the space.

I know that moving the partition can damage the boot thing in GRUB for the Ubuntu - SDA3.. (beginning moved)
Enlarging W7 end should no effect on Windows boot.

Right ?

So how would I be able to fix the GRUB entry later, after this operation using GParted on LiveCD ?

I think I will need to boot from LiveCD to do it.

Much Thanks for ur help.

---

### Post by Mr_JMM on 2012-11-25
Shrinking the partition shouldn't effect grub but as you will be shrinking the beginning of the partition and moving data on the drive, back up as if expecting to lose all the data.

---

### Post by ibjsb4 on 2012-11-25
> **Mr_JMM said:**
> Shrinking the partition shouldn't effect grub but as you will be shrinking the beginning of the partition and moving data on the drive, back up as if expecting to lose all the data.

Yep, and expect it to take a while.

---

### Post by oldfred on 2012-11-25
All Windows NTFS partitions have the start & size inside the PBR or partition boot sector. This is why we normally suggest using Windows to resize Windows partitions and Windows has to run chkdsk to update those parameters. Sometimes other repairs also required.

If you do not have have a Windows repairCD, be sure to make one first in case it does not repair itself and you have to run the repairs separately.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

    
Another option is just to create a shared NTFS data partition from the free space you create. Then that data can easily be used by both Windows & Ubuntu. It generally is best not to write into the Windows system partition as Windows may complain. And just set Windows system partition as read-only in Ubuntu.

---

