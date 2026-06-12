---
title: "Partitions"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by flipflipsen on 2010-05-04
Hello,

I have a computer, where I installed Ubuntu 9.10.

Now I installed also Ubuntu 10.04.

10.04 is installed in a extended partition.

I like to delete 9.10 and only leave 10.04 on my system.

If I do so, I have a system with an empty primairy partition of about 200GB, and a extended partition of about 300GB with ubuntu 10.04 installled.

How can I move the extended partition 10.04 to the primairy partition, then grow the partition to the total size of the harddisk so that only 10.04 is installed with only a swap partition.

with regards, Flip

---

### Post by dabl on 2010-05-04
> **flipflipsen said:**
> 

I like to delete 9.10 and only leave 10.04 on my system.



Deleting the files and folders on the partition where 9.10 is, is easy -- just use your file manager, or you could unmount the partition, run GParted, and "format" it.  But of course, that does not fix the grub boot menu.

> 

If I do so, I have a system with an empty primairy partition of about 200GB, and a extended partition of about 300GB with ubuntu 10.04 installled.



Right.  And a Grub boot menu that still shows 9.10.  After you have deleted the files or reformatted the 9.10 partition, in 10.04 you need to run sudo update-grub to make a new boot menu that does not show 9.10.

> 

How can I move the extended partition 10.04 to the primairy partition, then grow the partition to the total size of the harddisk so that only 10.04 is installed with only a swap partition.


I don't know that there exists a means of converting an extended partition type into a primary partition type -- if there is, it's not for inexperienced users.  If you want to boot a Parted Magic Live CD, and see what you can do with it, you can get the ISO image here:  [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

But, back up everything you value first -- you might render your system unbootable.

If I were you, I would just back up my data, re-partition the hard drive the way you really want it, then install the OS again.

---

### Post by oldfred on 2010-05-04
Do you have /home in a separate partition. If not now may be a good time to do it. Just use the partition that you open up.

I used this to move /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by Bobhuber on 2010-05-04
> **flipflipsen said:**
> Hello,

I have a computer, where I installed Ubuntu 9.10.

Now I installed also Ubuntu 10.04.

10.04 is installed in a extended partition.

I like to delete 9.10 and only leave 10.04 on my system.

If I do so, I have a system with an empty primairy partition of about 200GB, and a extended partition of about 300GB with ubuntu 10.04 installled.

How can I move the extended partition 10.04 to the primairy partition, then grow the partition to the total size of the harddisk so that only 10.04 is installed with only a swap partition.

with regards, Flip
BACKUP THE PARTITION FIRST NO MATTER WHAT YOU DECIDE TO DO.
You have several options depending on your level of expertise with the command line.
The easiest (or safest way might be a better term) will be to download  and create a bootable CD using System Rescue CD.You will also need a copy of the Live 10.04 Ubuntu CD to restore Grub when you are finished.Backup the partition using Fsarchiver found on the System Rescue CD (this is a command line program only). Make sure your backup is archived into several files that will fit on the storage media that you are using to store the backup (CD/DVD). Resize and reformat the drive using Gparted found on the System Rescue CD. Restore to the new partion using fsarchiver.Boot with the 10.04 Ubuntu live CD and reinstall grub on the new partition.Fsarchiver may scare you at first but print out the Documentation on it before you start and it will be a lot easier.
Hope this helps.

---

### Post by srs5694 on 2010-05-04
Please post the output of the following command:

```

sudo fdisk -l

```

Chances are you won't need to convert your Ubuntu installation from logical to primary form; you should be able to just expand the extended partition and expand/move the existing 10.04 to cover the extra space. (It's perfectly OK to have a disk with nothing but logical partitions and their associated extended partition.) Another option is to leave your partitions as-is and re-purpose your 9.04 installation's partition(s) in some way. For instance, you might empty the partition, move your /home directory's contents onto it, and then mount it at /home to make it a separate /home partition. Such an action might or might not be worth the effort, depending on how your partitions are currently laid out (hence my request for the fdisk output; that'll show us all precisely what you've got).

---

### Post by flipflipsen on 2010-05-05
Hi,

I shrunk the Ubuntu partition.
I made a /home partition, and moved the extended partition to the right.
I deleted the Ubuntu partition.
I installed Ubuntu 10.04.

Now I have Ubuntu 10.04 on the primary partition, Linux Swap and the Home on the Extended Partition.

Everything is oke now.

Thank you all for your support.

---

