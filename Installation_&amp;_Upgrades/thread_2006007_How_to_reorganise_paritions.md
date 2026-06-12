---
title: "How to reorganise paritions"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by 1976saint on 2012-06-18
Hi All

I have a dual boot (win7/Ubuntu 12.10) laptop. I have shrunk the windows 7 ntfs partition by 10GB so have a free area between NTFS and the first ubuntu partition. 

How can I stretch the ubuntu partition to use the freed space, this is a default install so paritions for ubuntu have not been changed. 


I have tried to use the partition manager gparted with both the live CD and on the installation but I cannot do anything with the 10gb free space (apart from creating something) or moving the partition boundary of the first ubuntu partition to use the free space.

Eventually I want to do away with the win7 partition altogether so trying this 10gb will be a good test.

Is there another tool available (I'd use Acronis disk directory etc to do this in windows)..If not I guess I could still use this but I want to start using linux tools if possible.

Best Regards
1976saint.):)

---

### Post by cmont899 on 2012-06-18
Some details please:

> 
sudo fdisk -l
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay

---

### Post by darkod on 2012-06-18
First, I hope the Ubuntu 12.10 is a typo. The 12.10 is still in early development, the last released version is 12.04 LTS.

If you really have 12.10 installed, don't count on it being stable, it will break frequently as they develop it day by day. If you only want to test it, that's fine.

But I can't imagine why the partition size would be so important if this is only a test for 12.10.

Back to your question. To manipulate the partitions, you have to work from live mode. Open Gparted, you will see a key symbol next to the swap partition, and probably next to the extended partition if swap is inside it. That means it's mounted because swap gets mounted in live mode too.
Right-click the partition in the list, select Swapoff. That should turn off the key symbol on all partitions. Now you can manipulate them.

If the root partition is inside the extended, you will have to move the border of the extended partition first, to include the unallocated 10GB space. After the unallocated space is inside the extended, and next to the root partition, you can move the border of the root partition to include it (expand it).

That should be it.

---

### Post by darkod on 2012-06-18
> **cmont899 said:**
> Some details please:

The OP never mentioned we are talking about LVM setup. Except the first, those are LVM commands.

---

### Post by papibe on 2012-06-18
Hi 1976saint.

I think you are on the right track (LiveCD -> gparted).

I don't think you can't stretch a partition to the left, but you can do this:
[LIST]
[*]First move Ubuntu the partition to the left, so there's no waste between partitions, and then
[*]Increase the partition size using the free space on the right.
[/LIST]
Hope that helps, and tell us how it goes.
Regards.

IMPORTANT NOTE: After that, you may need to update grub, or do a [boot repair]("https://help.ubuntu.com/community/Boot-Repair") because you move the Ubuntu boot partition.

---

### Post by 1976saint on 2012-06-18
> **cmont899 said:**
> Some details please:

Sorry 12.04 ;)

FDISK

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff89bb11

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    64870399    32435168+   7  HPFS/NTFS/exFAT
/dev/sda2        87898110   117229567    14665729    5  Extended
/dev/sda5        87898112   113055743    12578816   83  Linux
/dev/sda6       113057792   117229567     2085888   82  Linux swap / Solaris


I can't run the other commands, unknown command..

---

### Post by darkod on 2012-06-18
What I said in post #3 still applies.

Boot live mode, open Gparted, unmount swap.

Expand sda2 to the left to include the unallocated space. After that it should be inside sda2.
Expand sda5 to the left to include the unallocated space.

---

### Post by 1976saint on 2012-06-18
> **darkod said:**
> What I said in post #3 still applies.

Boot live mode, open Gparted, unmount swap.

Expand sda2 to the left to include the unallocated space. After that it should be inside sda2.
Expand sda5 to the left to include the unallocated space.

Many Thanks
I will try this tomorrow and let you know how it went..

Best Regards.

---

### Post by 1976saint on 2012-06-19
Many thanks to you all - 

I managed to use the free space using the method suggested above using gparted, and installed the boot-repair utility using the live cd to check that it would boot afterwards!

Great Stuff 

Cheers to you all again...:p
1976saint!

---

### Post by papibe on 2012-06-19
:D Great!

Please mark this thread solved (see [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")), when you have the chance.

Regards.

---

