---
title: "Please help me someone"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by KStoney on 2007-10-28
Firstly, i love ubuntu i want to make that clear!! but i do need my XP installation for work related things.

i have two harddrives, one IDE with ubuntu on, and another SATA, with XP on.

I installed ubuntu today and no i can't get on XP, it doesn't appear on that Linux boot list.
So i've done some research and edited the list and added XP to it doing this:

> title Windows XP 1
root (hd1,0)
savedefault
makeactive
chainloade

All it does when i pick XP now is says "Starting up..." and just stays on that screen, doesn't do anything and its definatly not accessing the hdd (coz its a raptor i can hear it)

Heres my output from sudo fdisk -1
> Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06460646

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4499 36138186 7 HPFS/NTFS

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa23e4144

Device Boot Start End Blocks Id System
/dev/hda1 * 1 4787 38451546 83 Linux
/dev/hda2 4788 4998 1694857+ 5 Extended
/dev/hda5 4788 4998 1694826 82 Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b10b91a

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 30401 244196001 7 HPFS/NTFS

Disk /dev/sdc: 262 MB, 262144000 bytes
33 heads, 63 sectors/track, 246 cylinders
Units = cylinders of 2079 * 512 = 1064448 bytes
Disk identifier: 0x7e0d9f7d

Device Boot Start End Blocks Id System
/dev/sdc1 1 247 255984 6 FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
phys=(0, 1, 1) logical=(0, 0, 33)
Partition 1 has different physical/logica

someone please help me, i really do want to keep ubuntu so i dont wanna just wipe everything and put xp back on.

thanks in advance
Karl.

---

### Post by homeslice on 2007-10-28
Not sure if this is a typo or not from your above quote, but the last line of your Windows entry in menu.lst should read "chainloader +1", not "chainloade" as you have it. Maybe you accidentally erased a few chars?

---

### Post by KStoney on 2007-10-28
aye cut off, it says +1 in the file

---

### Post by logos34 on 2007-10-28
try this:

> title Windows XP 1
root (hd1,0)
savedefault
makeactive
[B]map        (hd0) (hd1)
map        (hd1) (hd0)[/B]
chainloader +1

or substitute (hd2,0) and (hd2)

also, add sda to /boot/grub/device.map so it corresponds to your menu.lst entry edits

---

### Post by KStoney on 2007-10-28
Thank you for the reply, i did a lot of reading and found out the following:

When using 1SATA and 1IDE and wanting to install XP to the SATA, it writes the boot information (including the nt boot loader) to the IDE drive, so when i installed ubuntu, it deleted all of this.

Even with the extra map commands i got a NTDLR missing message.

So i started again and it all worked perfecty following these steps:

1. unplug the IDE drive from the computer and then install windows XP (this forces the boot information onto the SATA drive also
2. plug the IDE drive back in and then install ubuntu onto this, it automatically detects XP on the other drive and sets up the multi boot for you.

Everything works perfectly now, ubunutu and xp up and running yey, shame i gotta start a fresh and install everything on XP again!!

worth it tho, ubuntu :D

karl.

---

### Post by logos34 on 2007-10-28
> **KStoney said:**
> Thank you for the reply, i did a lot of reading and found out the following:

When using 1SATA and 1IDE and wanting to install XP to the SATA, it writes the boot information (including the nt boot loader) to the IDE drive, so when i installed ubuntu, it deleted all of this.

Even with the extra map commands i got a NTDLR missing message.

So i started again and it all worked perfecty following these steps:

1. unplug the IDE drive from the computer and then install windows XP (this forces the boot information onto the SATA drive also
2. plug the IDE drive back in and then install ubuntu onto this, it automatically detects XP on the other drive and sets up the multi boot for you.

Everything works perfectly now, ubunutu and xp up and running yey, shame i gotta start a fresh and install everything on XP again!!

worth it tho, ubuntu :D

karl.

Could you post the link(s) where you read that?  I've installed xp numerous times on exactly the same setup and everytting always ends up on sata disk.

---

### Post by KStoney on 2007-10-28
there was no link, it was trial and error thats how i managed to get it working.

---

