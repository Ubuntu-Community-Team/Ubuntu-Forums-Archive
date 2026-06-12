---
title: "Clonezilla and Gparted: cloning to larger drive and resizing partitions advice"
date: 2015-10-29
forum: Installation &amp; Upgrades
---

### Post by dheianevans on 2015-10-29
Just bought a 2TB drive and want to move my system to it from the 500GB drive it's currently on.

I've got a dual boot system. A 50GB Win7 partition, a 50GB Ubuntu partition and then the rest is a NTFS data partition.

I understand that Clonezilla can clone the 500GB drive to the 2TB. I can then use Gparted to expand the partitions. Some questions:

[LIST]
[*]Do I have to do anything to "initialize" the empty 2TB drive before the cloning or does Clonezilla take care of that? 
[*]If I then remove the old 500GB and insert the 2TB, will Grub boot just fine or do I have to issue any commands from a Live CD to fix Grub now that it's on a larger disk? 
[*]Can Gparted "move" unallocated space? I'm assuming that when I boot, there'll be roughly 1.5TB of unallocated space after the 500GB of partitions that Clonezilla has cloned. I'll be using that space mostly for the NTFA data partition but I want to add 50 or so GB to the first partition (Win7). After I increase the size of the data partition to use all but 50GB of the new space, can I "move" the unallocated space to the "right" of the Win7 partition and increase it? Or do I need another tool? 
[*]Recommendations for a good live CD/USB that has both Clonezilla and Gparted and any other tools you think I might need in this operation (e.g. to fix Grub if need be)? I know there was a joint Live CD, but that seems to have stopped development. 
[/LIST]

Thanks for any advice.

---

### Post by sudodus on 2015-10-29
> **dheianevans said:**
> Just bought a 2TB drive and want to move my system to it from the 500GB drive it's currently on.

I've got a dual boot system. A 50GB Win7 partition, a 50GB Ubuntu partition and then the rest is a NTFS data partition.

I understand that Clonezilla can clone the 500GB drive to the 2TB. I can then use Gparted to expand the partitions. Some questions:


[*]Do I have to do anything to "initialize" the empty 2TB drive before the cloning or does Clonezilla take care of that? 

No
> 
[*]If I then remove the old 500GB and insert the 2TB, will Grub boot just fine or do I have to issue any commands from a Live CD to fix Grub now that it's on a larger disk?

If you clone the whole drive, grub should boot just fine.
> 
[*]Can Gparted "move" unallocated space? I'm assuming that when I boot, there'll be roughly 1.5TB of unallocated space after the 500GB of partitions that Clonezilla has cloned. I'll be using that space mostly for the NTFA data partition but I want to add 50 or so GB to the first partition (Win7). After I increase the size of the data partition to use all but 50GB of the new space, can I "move" the unallocated space to the "right" of the Win7 partition and increase it? Or do I need another tool? 

Gparted can move partitions and change size of partitions. This means that it can move unallocated space in an indirect way. If you move the head of the Ubuntu root partition, it will not be found by the bootloader. This means that you need to reinstall the bootloader. See this link

[Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
> 
[*]Recommendations for a good live CD/USB that has both Clonezilla and Gparted and any other tools you think I might need in this operation (e.g. to fix Grub if need be)? I know there was a joint Live CD, but that seems to have stopped development. 


Thanks for any advice.

I suggest that you download a Clonezilla iso file and use it from a CD or USB drive. Gparted comes with the Ubuntu (and Ubuntu flavour) iso file, and it can be used from a live session 'Try Ubuntu'.

---

### Post by dheianevans on 2015-11-03
Thanks for the advice!

---

