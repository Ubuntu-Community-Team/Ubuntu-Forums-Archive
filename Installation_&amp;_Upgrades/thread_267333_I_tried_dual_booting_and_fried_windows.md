---
title: "I tried dual booting and fried windows"
date: 2006-09-28
forum: Installation &amp; Upgrades
---

### Post by bugsbunny on 2006-09-28
I tried to dual boot wndows xp and ubuntu and i ended up wiping windows off. I have 2 harddisk, master for windows and slave for linux. On the linux partition, i have a fat32 patition that i use to transfer data between the two partitions. I come from Archlinux background. Anyway i have reinstalled windows now and will want to try to reinstall again. 

The problem for me was the partition. I chose the manual partition to partion hdb (the slave). The partition software still displayed the hda and hdb partitions with some /media/**** stuff. 

Anyway how do i properly set my partitions up. I intend to have fat32, / , swap, /home on the the slave(hdb) with the whole of master(hda) for windows.

Also where should i install the grub boot loader?

Thanks.

---

### Post by _teo_ on 2006-09-28
> **bugsbunny said:**
> The problem for me was the partition. I chose the manual partition to partion hdb (the slave). The partition software still displayed the hda and hdb partitions with some /media/**** stuff.
These are the mount points. Usually I name them as I like.

> **bugsbunny said:**
> Anyway how do i properly set my partitions up. I intend to have fat32, / , swap, /home on the the slave(hdb) with the whole of master(hda) for windows.
I do following:
1) installer shows on the screen with graphics current partitions (while manually partitioning) - I remember their names (hdb1, hdb5, etc.) or write them down
2) on next screen I have to tell installer how to use partitions - so I can look at my notes from previous screen and make selections accordingly

Example:
your slave drive is called hdb

- say you want to use hdb1 as root, so select in left column the "/" and in right one find hdb1 (it is a good idea to reformat it)
- then suppose you want to use hdb5 for swap - select in left column swap and in right one find hdb5 (again it is good idea to reformat it)
- let your fat32 partition be at hdb6 - you can write in left column something like "/windows" and select in right column hdb6
- similar for /home

> **bugsbunny said:**
> Also where should i install the grub boot loader?
Don't worry about it. It will be installed in your root partition.

Hope above helps

---

### Post by Fatjoint on 2006-09-28
> **bugsbunny said:**
> I tried to dual boot wndows xp and ubuntu and i ended up wiping windows off. I have 2 harddisk, master for windows and slave for linux. On the linux partition, i have a fat32 patition that i use to transfer data between the two partitions. I come from Archlinux background. Anyway i have reinstalled windows now and will want to try to reinstall again. 

The problem for me was the partition. I chose the manual partition to partion hdb (the slave). The partition software still displayed the hda and hdb partitions with some /media/**** stuff. 

Anyway how do i properly set my partitions up. I intend to have fat32, / , swap, /home on the the slave(hdb) with the whole of master(hda) for windows.

Also where should i install the grub boot loader?

Thanks.


Just to add to what was stated above -

Partioniing wise I like the following:


```
/ - I've found that I'm most comfortable with setting to 10GB
/swap - 2x physical memory size
/home - the remaining drive size (minus what you want to allocate for Fat32)
/fat32 - remainder after allocating /home.  Also, I like to mount this to /home, so it looks like /home/fat32.
```

---

