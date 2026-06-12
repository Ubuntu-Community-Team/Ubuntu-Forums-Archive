---
title: "Partition help!"
date: 2013-08-27
forum: Installation &amp; Upgrades
---

### Post by Nick_McKinnon on 2013-08-27
Hey everyone!

I'm trying to install Ubuntu as a dual boot along side Windows 7 Starter on my Asus EeePC.

I've created a Ubuntu Live USB that I can boot to, but I am not able to create a partition for a full install. When I try, GParted tells me "It is not possible to create more than 4 primary partitions."

My netbook has 1 HDD, and under Windows it shows it having 2 drives - one with Windows installed, & another with just data.

Here's what GParted comes up with:

sda1 - ntfs - 100GB - boot (this is the Windows partition)
sda2 - fat32 - 15GB - hidden
sda3 - ntfs - 95GB - (this is the data partition)
unallocated - 90GB (I created this in Windows Disk Management before booting to the LiveUSB so I could create a new partition here...)
sda4 - unknown - 16MB (According to Windows Disk Management this is an EFI System Partition, whatever that is)

Is the data partition meant to be a primary partition? I thought it would just be extended...

I know my EeePC has some fancy fast booting things that I assume account for one or two of those primary partitions.

Any ideas how I can create a primary partition for Ubuntu to jump into?

Thanks in advance!

---

### Post by TheFu on 2013-08-27
MBR partitioning only allows 4 primary partitions total.  Please read this [https://en.wikipedia.org/wiki/Master_boot_record](https://en.wikipedia.org/wiki/Master_boot_record).

There is a hack to support more partitions called "logical partitions", but those can only reside **inside** an "extended partition".
Extended partitions are a type of primary partition, so you need to find a way to create the extended partition - looks like you **must** delete one or more of the other primary partitions.

There aren't any real limits on the number of logical partitions - over 100 are possible.

Windows and MS-DOS OSes do not like to boot from non-primary partitions, but can read data from logical partitions just fine.

Linux can boot from and access data on Logical partitions.

Are you certain you have an MBR partition?  Many EFI systems come with GPT partitions which is the next gen partition table with all sorts of upgrades ... and it also removes the 4 primary partition limit. The wikipedia article on [GPT]("https://en.wikipedia.org/wiki/GUID_Partition_Table") has some important limits that you need to understand, but on a purely Linux box, it is a non-brainer - GPT is good.

BTW, the output from **sudo parted -l** would be helpful. Please use a "code" tag when you post it here.

Regardless, it looks like you'll be backing up some data, deleting at least 1 partition, creating an extended partition and 3 logical partitions inside, restoring data, to get to the point you can install Linux.  

I'd probably reduce the size for a few of the other partitions when you are there too.  Use the Windows tools to reduce partition sizes and be ready with a save-your-butt Windows restore disk. You'll probably need it.

---

### Post by oldfred on 2013-08-27
I do not think you get the primary partition error with gpt. gpt does not even have primary or logical as it just has one type (which are like primary). 
Also Windows only works from gpt with UEFI and then one of the first partitions is an efi partition.

Use Windows disk tools to shrink the Windows NTFS partition but not to create any new partitions. It may convert to dynamic partitions from basic and dynamic do not work with Linux.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by Nick_McKinnon on 2013-09-12
Thanks a million for the help folks! I ended up deleting the data partition, since I couldn't confidently delete any of the others. Ubuntu is successfully installed in its place & I'm enamoured with it so far - so much faster than Windows 7 on my netbook...

Time to start learning how to use this little baby...

Thanks again!

---

