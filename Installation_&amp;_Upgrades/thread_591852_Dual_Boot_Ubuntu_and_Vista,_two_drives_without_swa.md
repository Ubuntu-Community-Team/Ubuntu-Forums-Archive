---
title: "Dual Boot: Ubuntu and Vista, two drives without swapping"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by anoweb on 2007-10-25
I have two hard drives installed in my computer.  The drives are currently partitioned as such

Disk 0:
   D: <music, pictures, etc> 80GB
   Unallocated: 32GB

Disk 1:
   C: <vista> 68GB
   E: <applications> 30GB
   F: <development> 30GB
   Free Space: 22GB

so I have two hard drives, disk 1 has Vista installed on the "C" drive.

Basically I'd like to install Ubuntu on Disk 0 if possible, or on the free space of Disk 1....**BUT** I don't want to have to disconnect the hard drive(s) to do this...is it possible, if so can someone help me :)

I haven't had much luck so far.

thanks

---

### Post by Em-Buntu on 2007-10-25
> **anoweb said:**
> I have two hard drives installed in my computer.  The drives are currently partitioned as such

Disk 0:
   D: <music, pictures, etc> 80GB
   Unallocated: 32GB

Disk 1:
   C: <vista> 68GB
   E: <applications> 30GB
   F: <development> 30GB
   Free Space: 22GB

so I have two hard drives, disk 1 has Vista installed on the "C" drive.

Basically I'd like to install Ubuntu on Disk 0 if possible, or on the free space of Disk 1....**BUT** I don't want to have to disconnect the hard drive(s) to do this...is it possible, if so can someone help me :)

I haven't had much luck so far.

thanks
Yes, it's possible, but you will need to;

1 Make the 32GB partition active.
2) Direct Ubuntu to this partition for the install.
3) Use a boot manager to select which OS to boot. I use Partition Magic's Boot Manager to avoid Ubuntu and Windows competing for the MBR and overwriting each other.
I have the same setup running as you are attempting, except my Windows XP-64 is installed on C:/, while Ubuntu is installed on the D:/ drive.

---

### Post by anoweb on 2007-10-25
thanks for the reply.

1. how do I make the 32GB active?
2. I was going to use EasyBCD...during my other attempts at this after I installed Ubuntu EasyBCD showed three drives, Swap, Extension and something else...basically two of the three linux drives were about 1 GB and the other was like 30GB....which one should I point EasyBCD to.

otherwise...how do I use the boot manager you mentioned?  or where can I get info on using it.

thanks again!

can't wait to get linux working so i can make the switch in the near future.

---

### Post by Computer Guru on 2007-10-26
It depends what version of EasyBCD you use. In [the latest (1.7)]("http://neosmart.net/dl.php?id=1"), there is an option that doesn't need you select a drive at all: "GRUB isn't installed to the bootsector" will search for and load Ubuntu on its own.

---

### Post by anoweb on 2007-10-26
I am using EasyBCD 1.7 and see the option you mention.

So the last question is how do I make the 32 GB of "Unallocated" space on Disk 0 "active"?

---

### Post by Computer Guru on 2007-10-26
You don't.....

"Active" is the main partition on the disk - you *definitely* don't want an unallocted (no filesystem, no partition) section of the drive set as the active partition[!]

This is, of course, assuming you've *already* installed Ubuntu?

---

### Post by anoweb on 2007-10-26
so would I want to perhaps reformat my disk 0..

Disk 0:
D: <music, pictures, etc> 80GB
Unallocated: 32GB

...basically what should I do with disk 0...i have no problem wiping it out, i have already backed up the data on the "D:" drive.

thanks

---

