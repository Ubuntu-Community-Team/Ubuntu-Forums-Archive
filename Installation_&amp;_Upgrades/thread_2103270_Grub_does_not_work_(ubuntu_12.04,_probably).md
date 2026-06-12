---
title: "Grub does not work (ubuntu 12.04, probably)"
date: 2013-01-09
forum: Installation &amp; Upgrades
---

### Post by ActiveFly on 2013-01-09
Hi :D
 
on my Dell-laptop I installed ubuntu (most likely 12.04) in parallel to Win XP several months ago.
 
Today when booting a second time I received only a promt: 
GNU GRUB version 1.99-21ubuntu3.7
Minimal BASH-like line editing is supported. For the first word, ...
grub>
 
While working earlier today an ubuntu update was conducted - I had to restart Firefox but not the ubuntu system. I do not think that it has to do with the grub problem - but perhaps it is relevant.
 
I tried to start grub manually, but it did not work (I do not go into detail since I am not sure if it is of interest). However:
ls & Enter resutls in -> (hd0) (hd0,msdos6) (hd0,msdos5) (hd0,msdos1)
ls (hd0, & TAB results in -> 3 partitions ntfs, unknown and ext2
 
I tried to start grub manually becaus I would like to backup my data prior to change/repair grub (a have a backup made some days ago, however a recent one would be better). I tried a liveCD but I have no access to the relevant folder.
 
I would appreciate help related two the topics:
- backup of data
- getting grub working again
 
Please advice which information you require (and how to get it ;)).
 
Thanks
 
Ulrich

---

### Post by darkod on 2013-01-09
If you used the auto installer, the root partition is probably (hd0,msdos5). You can try booting from the grub rescue prompt with something like:
```
insmod part_msdos
insmod ext2
set root=(hd0,msdos5)
linux /vmlinuz root=/dev/sda5
initrd /initrd.img
boot
```

See if that can boot the system.

---

### Post by ActiveFly on 2013-01-10
> **darkod said:**
> See if that can boot the system.

Positive! Thanks! I was able to backup my system.

Just for Info: I had to use *6 instead of *5, since the msdos6-partition is ext2 (linux).

Please could someone advice for the next step to repair grub - thanks.

Ulrich

---

### Post by darkod on 2013-01-10
Once you have it booted, simply try:
sudo grub-install /dev/sda

That should reinstall it on the MBR of the disk. After that try if it works.

The problem might be if the grub2 boot files are too far from the start of the disk. Some older machines have a limitation not to be able to read boot files beyond 137GB on the disk. You might be affected by this.

---

### Post by ActiveFly on 2013-01-10
> **darkod said:**
> 
sudo grub-install /dev/sda

Negativ - unfortunately.

The reinstallation process prompts: Installation finished, no error reported - however grub still does not work when rebooting the laptop. It ends up in the same manner as mentioned above.

Further ideas would be appreciated - thanks :D

Ulrich

---

### Post by darkod on 2013-01-10
You have the further idea. :)

It might be related to the distance of the boot files from the start of the disk. The bootinfo reported by boot-repair can help you see where the boot files are exactly.

Unfortunately, I don't know of a fix for that problem except creating 200MB-500MB /boot partition at the start of the disk. And since usually you wouldn't have this unpartitioned space at the front of the disk, it means you have to repartition a bit.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ActiveFly on 2013-03-18
Finally I just reinstalled Ubuntu incl. Grub - now it works again.

So bit late but better than never: Darko, thanks a lot for your help getting a backup of my latest data after the crash in January!!

Ulrich :)

---

