---
title: "partman option: copy data... safe?"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by eeried on 2005-07-25
Hello,

I've been impressed by partman as I installed Ubuntu a few days ago (both on a laptop, dual-boot with winxp, and on its own on a desktop.

I didn't dare  use the option: "copy data from a partition"

What exactly does this option do?

Is it reasonably safe?

Thanks :)

---

### Post by az on 2005-07-25
It is very safe.  It will refuse to do something if it does not think it is safe.

Copy data will do just that.  It will take all the data on one partition and copy it to another partition.  If you have three partitions on a drive, but need to change things around and you can resize, create, delete and copy data from partitions.

If, when installing, you assign your windows partition a label and tell the partitioner to keep existing data, it will add an entry into your fstab so that your windows partition will be mounted in linux, something that you would have to do by hand yourself.

It would be really nice if it autodetected these partitions (just like it autodetects other OSes and adds them to a grub menu.list file and added the appropriate entries into fstab as part of the guided partitioning step...

I think that feature request has already been made.

---

### Post by eeried on 2005-07-26
Many thanks azz for all the details. I've been reading your posts helping people with those darned winmodems!!

Well even if I don't mind mounting a partition the old way, partman is a great tool then! Don't make Ubuntu too sophisticated or there'll be nothing left for us Linux users to confgiure and no use at all for an xterm -- which I'd miss sorely... though I'm still no expert, rather more like an advance newbie ;-) 

My other question is : would it be safe to copy and therefore move  the data from an IBM rescue partition which is hidden in Windows but seen by Ubuntu as hda2. (laptop with stupid winxp preinstalled, as this isn't my laptop I can't run the risk of destroying anything!).

I can post some of its content if that's of any help.

At the moment hda2 is at the end of the HDD because I resized hda1 (C) to make room for Ubuntu, so Ubuntu with its several partitions is in-between hda1 and hda2.
I resized hda1 with qtparted from Kaella (based on knoppix) CDlive because I didn't know if partman was able to do that.
cfdisk complains the partition table is disorderly (partitions not in the right order) and some partitions don't stop at the right cylinders. True I dind't check the cylinders with partman, again because I didn't dare to venture too far for my first install of Ubuntu.

I've been told a disorderly partition table doesn't matter at all. Ubuntu seems all right. I'd like to install now Kaella or Knoppix just to expreriment with triple boot (dual boot was a such a piece of cake with Ubuntu!).

Cheers,

---

