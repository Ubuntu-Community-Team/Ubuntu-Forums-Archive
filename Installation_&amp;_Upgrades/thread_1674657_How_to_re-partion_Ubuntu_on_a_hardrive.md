---
title: "How to re-partion Ubuntu on a hardrive?"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by wavesailor on 2011-01-24
[FONT="Verdana"][SIZE="4"]Hi all,

I have a notebook with dual boot window$ and Ubuntu 10.10 on a 80 Gig hard drive. The windows XP partition was initially installed and took up the whole drive (dev/sda1). I then freed up some space and created and installed Ubuntu (/dev/sda6) and swap (/dev/sda5) on an extended partition (/dev/sda2).

Initially I only freed up 3.6 Gig which I thought would be more than enough but not any more. I cannot even install the updates as there is only 100 Meg left which is not enough. I then freed up more space (8 gig) from the windows partition to allocate to Ubuntu.

My problem is that I can't seem to find to now allocate this "freed-up" space to Ubuntu?? I realise that I have to boot-up from a the Ubuntu live disk so that the hard drive is not mounted to allow changes but I'm still unable to change the partitions. I'm using GParted.

The drive looks like this currently:
[...NTFS] [...Unallocated] [...Extended{(ext4),(linux-swap)}]

Any help would be most appreciated as I would hate having to install Ubuntu again.

Thanks :-)
[/SIZE][/FONT]

---

### Post by oldfred on 2011-01-24
You have to slide the extended partition left into the unallocated space. Then you can move/expand the Linux partition. 

Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Unless you have limited room on your drive I suggest 10 to 20GB for the / (root) partition. I also usually suggest a separate /shared NTFS partition for windows data, so you do not write directly into the windows system partition. Some windows users suggest the same thing, so when you reinstall windows you do not lose all your data.

---

### Post by wavesailor on 2011-01-24
Thanks Oldfred

> **oldfred said:**
> ...
Resizing an Ubuntu System Partition
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)


In the link I found my problem: The live-CD uses the swap space and you have to manually turn it off: Select the swap partition, and the Right-Click and select Swapoff to unmount it.

All good now - Thanks again :D

---

