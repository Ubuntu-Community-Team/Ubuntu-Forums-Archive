---
title: "Partition questions"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by joker535 on 2008-02-19
I have my machine set up with two 80G hard drives. The master has the whole thing NTFS for XP and was already there when I added ubuntu. I added another 80G drive and split it half as an NTFS data partition and half for ubuntu. I am going to use the gparted live cd to kill the NTFS half and expand the ubuntu half.

I have been considering killing the other 80G drive but I would guess that the boot info is on there. I don't use the windows load anymore but I don't want to mess up my ubuntu install It has taken me 5 months to get it perfect). 

Is there a simple way to kill the NTFS partition on that drive without killing my ununtu load on the second drive?

Thanks

Bob

---

### Post by kidders on 2008-02-20
Hi there,

It's likely that the only boot-related information (if any) stored on the "NTFS only" drive is your bootloader. You're the only one who can tell for sure if it's there, but even if it is, and you erased the contents of the drive anyway, there's no reason you couldn't put it back again ... or perhaps move it to the drive you've divided in two. There's certainly no question of losing your Ubuntu ... unless of course you erase it (or a critical part of it).

Bootloader installation is something all Linux users should really be familiar with, because they do get damaged (or need to be moved) from time to time, so I would suggest pulling out a live CD, and learning to play with yours. There's plenty of help here & in other forums. Once you feel like you've gotten the hang of it, format your disk, and (assuming you even need to), you should be able to get your bootloader back within a couple of minutes.

If your plans involve resizing any partitions though, I would strongly recommend a backup. It's a relatively rare occurrence, but if the operation were to go pear-shaped, you could easily lose quite a lot of stuff.

---

