---
title: "Unformatted free space become Unavailable after creating swap space or /boot"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by javanoob on 2012-06-04
Hi guys,

I am new to Ubuntu and this is my 1st time.
Appreciate if you guys can guide me along and thank you for the kind patience in reading through my problem.

1) I have a 100TB harddisk which is currently install with Window 7.

2) I went to disk management to shrink the volume giving me about 480G of freespace.

3) With this freespace available, i went on to put in the Ubuntu installation CD , restart my laptop and boot from the CD

4) in the installation portion, i saw the unformatted free space, that was make available earlier during the shrink operation at 2).

5) so i went on to click on the free space and choose the "Add"
Type -> Logical
New partition size -> 16000mb
Location -> Beginning
Use as : Swap
OK

6) The above is done and now i need to create a /boot partition
So again i click on NEW

**Q1) **why cant i choose the partition type anymore (there is no option for me to choose between Primary or Logical)

Size -> 100MB
Use as -> Ext4
Mount Point -> /boot

-------------------------------------------------------

You can see that i am creating the partitions in the following order
1) swap (logical) -> /boot (not choosable) -> / (not choosable)

However, if i turn the order around and create the / partition 1st

Add
Type for new partition -> Primary
New parition size -> 450000 (i have about 20000 left for swap and /boot)
Location for new partition -> Beginning
Use as -> Ext4
Mount Point -> /

**Q2)**  After creating this, the remaining 20000MB become unusable , why ?!

**Q3)** What is the difference between choosing beginning and end for the parameter -> Location of new partition

-----------

Hope to hear advices from the great guys in the ubuntu forum

Thanks!:(

---

### Post by oldfred on 2012-06-04
You can only have 4 primary partitions and only one primary may be converted to an extended partition which is a container for logical partitions.

I always use gparted to partition as it is easier to visualize the primary and the extended. If you end up creating a primary and use the last available primary then you cannot create the extended.

Post screenshot from gparted. Use paperclip in edit panel to add to message.

gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by darkod on 2012-06-04
Yeah, oldfred is right. It seems you already have 3 primary partitions existing.

So, if you create a fourth primary, it doesn't let you create any more partitions regardless how much unallocated space you've got, because the limit is 4.

On the other hand, if you create it as logical, you can continue creating partitions but only logical partitions, hence it's not asking you any more if you want to create primary or logical.

The difference between choosing beginning and end is where will it put the partition into the unallocated space you selected for creating it. For example, you have unallocated space of 100GB and you want to create a partition of only 20GB. By selecting beginning or end you select whether it will be the first 20GB of those 100GB, or the last 20GB.

This can be useful if you want (or need) to control which partitions border with which.

---

### Post by javanoob on 2012-06-05
Dear all,

Yes. You guys are right. 
I guess I have got 3 primary partitions already

--

--

Coming to that -> 
I understand that linux does not care about primary or extended partition.
Since I have 1 primary parition left only, i can only create it as extended and partitioned further from there.

However, my concern would be whether there will be any performance limitation or problem ?
I am actually going to run an OracleDB and some linux scriptings (for my own learning purpose) only.

Also, what good would it be to place a partition at the beginning or the end of a freespace.
like what darko have said [I]"This can be useful if you want (or need) to control which partitions border with which."

[/I]why would anyone need to do that ?

Regards,
Noob

---

### Post by SketchMan3 on 2012-06-05
Is it okay for me to ask this question here? Well, here goes:

Are "Logical partition" and "extended partition" the same thing?

---

### Post by fox hunter on 2012-06-05
A hard disk may contain only one extended partition; the extended partition can be subdivided into multiple logical partitions.

---

