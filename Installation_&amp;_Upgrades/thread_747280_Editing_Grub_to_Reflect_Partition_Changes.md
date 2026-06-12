---
title: "Editing Grub to Reflect Partition Changes"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by LaneLester on 2008-04-06
The master drive on my system has these partitions:
sda1 6 GB FAT32 recovery that came with my HP box
sda2 120 GB NTFS Win XP
sda3 10 GB EXT3 Ubuntu Gutsy
sda4 16 GB EXT3 Ubuntu Hardy (my main OS)

I want to delete sda2 and repartition the space into several pieces without losing the ability to boot to Hardy. Is all I need to do is increment the number in grub's menu.lst?

In other words, change "root (hd0,3)" to "root (hd0,4) if I divide sda2 in two?

Lane

---

### Post by talsemgeest on 2008-04-06
Easier way to figure it out is to look on gparted. Look at the partition number for the partition you want to use.

For example, if it says (hd0,4) for the partition, in your menu.lst you would put (hd0,3), (hd0,6) would be (hd0,5) etc...

Hope this helps :)

---

### Post by logos34 on 2008-04-06
> **LaneLester said:**
> 
I want to delete sda2 and repartition the space into several pieces without losing the ability to boot to Hardy. Is all I need to do is increment the number in grub's menu.lst?

In other words, change "root (hd0,3)" to "root (hd0,4) if I divide sda2 in two?

Delete sda2 and create a new **extended** partition (which will also be called sda2) in its place, which you can subdivide up into logical partitions sda5, sda6, etc... It won't affect boot or the numbering of your other partitions.

---

### Post by LaneLester on 2008-04-06
> **logos34 said:**
> Delete sda2 and create a new **extended** partition (which will also be called sda2) in its place, which you can subdivide up into logical partitions sda5, sda6, etc... It won't affect boot or the numbering of your other partitions.

That does the trick! I just tried it with one logical partition, and indeed, it is sda5. Very nice solution.

Thank you, too, talsemgeest, for responding.

Lane

---

