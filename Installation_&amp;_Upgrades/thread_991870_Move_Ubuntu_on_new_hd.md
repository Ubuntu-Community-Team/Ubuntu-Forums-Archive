---
title: "Move Ubuntu on new hd"
date: 2008-11-24
forum: Installation &amp; Upgrades
---

### Post by SteMMo on 2008-11-24
Hi all,
how can i move an installed Ubuntu (8.04) into a newer and larger hd?
I'd like to avoid to lost my actual settings ..

Thanks

---

### Post by Sef on 2008-11-24
Check out [clonezilla]("http://clonezilla.org") or [partimage]("http://partimage.org/Main_Page").

---

### Post by SteMMo on 2008-11-24
Thanks,
but my guess was:
- connect the new hd (hdd)
- run a live distribution
- create the new partition (hdd1 + hdd2) by fdisk
- copy the content of hda1 to hdd1 by dd if=/dev/hda1 of=/dev/hdd1 bs=1M
- chroot in hdd1
- run grub to install the boot manager

Is it correct as procedure?

---

### Post by caljohnsmith on 2008-11-24
> **SteMMo said:**
> Thanks,
but my guess was:
- connect the new hd (hdd)
- run a live distribution
- create the new partition (hdd1 + hdd2) by fdisk
- copy the content of hda1 to hdd1 by dd if=/dev/hda1 of=/dev/hdd1 bs=1M
- chroot in hdd1
- run grub to install the boot manager

Is it correct as procedure?
Doing the above procedure is really tricky because the partition that you create on your new HDD must be exactly the same size as the Ubuntu partition you are copying from. Also, you would have to use the "conv=notrunc" option with the dd command since the partition size you are copying from/to will most likely not be an exact multiple of 1 MB, or the block size you specified above for the dd command. Those programs that Sef linked to do all that hard work for you, so there is less chance of a mistake.

Another really easy way to copy your Ubuntu partition over is to use Ubuntu's partition editor gparted; you can simply do a copy/paste of the original partition to the destination drive with gparted. I would give that shot if I were you. You would want to use gparted from the Live CD, and it can be found under System > Admin > Partition Editor. Let us know what you decide to do and how it goes. :)

---

### Post by SteMMo on 2008-11-25
Thanks,
- I'm trying with gparted but i have only the 'copy' command, not the 'paste' one.
- using dd i receive an Input/output error reading the source partition. Maybe there are some disk errors .. how can i solve this problem? With 'conv=noerror' the dd retries a number of times but it seems to be in a loop trying to read the same bytes.

Thanks again

---

### Post by caljohnsmith on 2008-11-25
After doing the "copy" command with gparted to copy the partition, you then have to select the other drive, and then select unallocated space on the drive where gparted can copy the partition to. Have you tried that? How about also posting:
```
sudo fdisk -lu
```
And please identify which partition you are trying to copy, and where you want to put it.

---

### Post by SteMMo on 2008-11-25
Maybe when i tried that the destination partition was allocated ... how can i unallocate it?
Now i'm on office, when i will be at home i will return the result of the command.
Thanks

---

### Post by SteMMo on 2008-11-26
Well, i was able to copy/paste the partition by gparted: the dest partition was not unallocated then gparted did not allow me to paste.
But after 791Megs I receive an IO error on the source partition .. even if I run e2fsck the problem still there ...
So I decided to install from the cd and then retrieve my old home directory.

Thanks a lot !

---

