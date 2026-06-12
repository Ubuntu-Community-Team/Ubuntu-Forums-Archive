---
title: "Just installed Ubuntu, want to delete Windows XP"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by Lacho on 2006-09-29
As the title suggests, I just recently installed Ubuntu, latest v, took two attempts, but came out great.

I have been using computers for almost 30 years now, so I am no newbie, but this is my first Linux experience.

I thought that upon insertion of the install disk, and choosing the  hard disk upon which to install Ubuntu, Win XP would be obliterated, but now I got a dual boot. I am just tired of Microsoft, so wanna erase all of Win XP.

How do I accomplish this?

---

### Post by jpkotta on 2006-09-29
> **Lacho said:**
> As the title suggests, I just recently installed Ubuntu, latest v, took two attempts, but came out great.

I have been using computers for almost 30 years now, so I am no newbie, but this is my first Linux experience.

I thought that upon insertion of the install disk, and choosing the  hard disk upon which to install Ubuntu, Win XP would be obliterated, but now I got a dual boot. I am just tired of Microsoft, so wanna erase all of Win XP.

How do I accomplish this?

Use gparted or cfdisk to reformat your Windows partition.  Then edit out the Windows entry in /boot/grub/menu.lst and update the bootloader with ```
sudo update-grub
```  That's it.

---

### Post by Magnetizer on 2006-10-22
Lacho, can you confirm the solution?

I've got the same problem. My harddisk is split up in two partitions. I've got Windows XP on the first partition (the bootable one) and Ubuntu on the second partition. I do not use Windows XP anymore and want to delete it. 

I can format it with GParted and add the empty space to my Ubuntu partition. But I'm a little afraid of doing so as the Windows partition is the only partition with a boot flag.

So, how do I add the boot flag to my Ubuntu partition without installing everything from scratch?

---

