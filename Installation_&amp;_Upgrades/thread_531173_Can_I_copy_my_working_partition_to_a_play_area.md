---
title: "Can I copy my working partition to a play area?"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by PeggySue on 2007-08-21
I have two large hard drives One has my clean, up to date Ubuntu Feisty partition and a working Windows XP partition.  The other has an old version of XP, a KUbuntu partition and a play partition where I try out things without risking my up to date partition.  

I would like to be able to clone my tidy partition into my play partition or Kubuntu partition but I can't imagine that it is as simple as copying the file structure (inc. hidden files).  The play partition was the last to be installed and has the active menu.list in /boot/grub so I guess that this is the partition that GRUB stage 2 runs from.  Also I'm not sure the disk UUIDs will match the fstab if I just copy the files.

Anyone know an established method of doing this?

Many thanks.

---

### Post by Chymera on 2007-08-23
yes, you can do that, its pretty straightforward

just type ```
sudo gparted
``` and voila a partition editor which can copy everything

you should be careful though, you cant have more than 4 partitions on a single drive (swap and copied partitions count as partitions too)

---

### Post by PeggySue on 2007-08-24
Chymera:  Great thanks.  I had heard of Gparted but didn't realise in copied data; and so easily.

I tried it on a USB memory stick first and found it copies EVERYTHING including partition names so I created a stick with two partions with the same name!  No problem as I'm going to wipe it in any case.

While waiting for a reply to this post I copied the data from partition sda2 to sdb3 using cp -a.  This was OK but when I booted into sdb3 it didn't mount sda2.  I fixed it by creating a directory  /media/sda2 and adding a line to /etc/fstab.  I will use Gparted next time but I assume it will have the same issue.

I guess I can't copy to the partition that GRUB boots into because the configuration data will be lost.  When I feel brave I will copy a partition into the GRUB boot partition and just relace the copied /boot/grub directory with the original to see what happens. 
It's fun having just enough knowledge to be dangerous!

---

