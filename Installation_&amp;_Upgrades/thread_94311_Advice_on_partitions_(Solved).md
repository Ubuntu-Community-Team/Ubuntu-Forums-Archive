---
title: "Advice on partitions (Solved)"
date: 2005-11-23
forum: Installation &amp; Upgrades
---

### Post by bme56 on 2005-11-23
Hello. Thank you for clicking on my thread, even if just to flame me. I'm sure you have fools like me here to ask you questions all the time, so I apologize in advance. 

Now, I have 10 GB left on my hard drive. I've gto an Ubuntu 5.10 disc ready, and all my files backed up. I plan to dual boot, so gettting rid of all the Windows files is mostly out of the question. I can probably get rid of some stuff, but if possible, I'd prefer to stay a gig or two under the 10 limit anyway. I can't buy a bigger hard drive just yet. So, I'm wondering what sort of partition setup you guys think I should try with the little space I have left. Do you think I should stick with Ubuntu as planned or switch to DSL or something like that? Or should I give up on trying to even run Linux from the hard drive until I get a bigger one?

Any and all help is appreciated, and I think you for the time it took to read that.


EDIT: I'm sorry, I didn't see the beginner section below this. However, I think I'm just going to go ahead and give it a shot. This thread can be locked or deleted as needed.

---

### Post by SilentCacophony on 2005-11-23
Hi. For one, 10 GB is plenty for an ubuntu install (mine is taking up 46% of a 5 GB partition.)

Also, you can get as simple or complex as you like with a linux install. My personal preference is to keep it simple but flexible, and make a partiton for /, swap, and a FAT32 partiton to share data between Windows and Ubuntu. For reference, I'll post my partition setup:

```
brian@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20493656064 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2         312     2498107+   b  W95 FAT32
/dev/hda2             313         722     3293325   83  Linux
/dev/hda3             723        1338     4948020   83  Linux
/dev/hda4            1339        2491     9261472+   f  W95 Ext'd (LBA)
/dev/hda5            1339        1851     4120641   83  Linux
/dev/hda6            1852        2364     4120641   83  Linux
/dev/hda7            2365        2491     1020096   82  Linux swap / Solaris

Disk /dev/hdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1247    10016496    c  W95 FAT32 (LBA)
```

Works for me, though others may or may not detest such a setup ;) I've got a small Windows 98, two ubuntus, two ext3 storage partitions (for storage of large files, rather than having a separate /home partition, or for another linux installation if I like...), and a swap partiton. I use the second drive for media and such to be shared between OSes.

Also, here's a nice page that explains one way to setup a dual-boot windows/ubuntu setup:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by aysiu on 2005-11-23
My Ubuntu installation is on a 7.3 GB partition and uses only 4.1 GB of that.
Of course, my actual files (music, pictures, documents) are on a 100 GB FAT32 partition.

So 4.1 GB is the Ubuntu operating system, all the programs I have installed, and my configuration files.

---

### Post by mendieta on 2005-11-23
Unless you want to share with Windows back and forth, I would recommend:

1 partition for /home (size about 4 or 5 gig)- your personal files go there and you NEVER delete this one (even if you change to another distribution, or reinstall (k)ubuntu from scratch.

1 partition for / (size about 4 or 5 gig) - your system goes there. 

1 partition for swap (about 1 gig or so) (a separate partition for wap is always better)

Good luck!
-- mendieta

---

### Post by bme56 on 2005-11-25
Thanks guys, I got it to work fine. The biggest thing was realizing that 10 gb is plenty. Thanks again for your help.

---

