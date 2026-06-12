---
title: "Advice on dual boot setup"
date: 2008-03-04
forum: Installation &amp; Upgrades
---

### Post by VIPea on 2008-03-04
**Hi everyone**!:)

I'm new to Ubuntu and I'm hoping to install it on my computer without problems. I'm gonna be using the simple setup (not code or whatever). 

I have 3 hard drive partitions - **75GB** (NTFS Main), **32GB** (FAT32) & **5GB** (FAT32), 
I'd like to use the **32GB** for **Ubuntu** and then keep *Windows XP* on the *75GB* hard drive. Would this be possible? and should I reformat the 32GB hard drive to NTFS or keep it FAT32?

_My PC:_
Intel Pentium 4, 2.8GHz
768MB SDRAM
NVIDIA GeForce FX 5200
Windows XP

---

### Post by dstew on 2008-03-04
Do you want to keep the 5 Gb partition for some reason? If not, when you get to the partitioning step, delete the 32Gb and 5Gb partitions. Then, out of the unallocated space, make a 36 Gb partition for Ubuntu, with the ext3 format, mount point /. From the leftover 1 Gb, make a swap partition. After the installation is finished, install grub to (hd0) which is the default. It will probably detect your XP install and make a menu entry for it so you can boot it.

---

### Post by VIPea on 2008-03-04
Thank you very much for your reply!

I'll probably do what you advised, but how do I install grub? (I requested the live CD online and I'm currently waiting for it to be posted) Is it included on the disc?

---

### Post by VIPea on 2008-03-04
bump (sorry)

---

### Post by dstew on 2008-03-04
Yes, grub is included on the install disk. It is the last thing that happens during the install process. I think it asks you if you want to install grub, you  just say yes and it goes in.

---

### Post by VIPea on 2008-03-04
Awesome! 

**Thank you s0 much!!**

---

