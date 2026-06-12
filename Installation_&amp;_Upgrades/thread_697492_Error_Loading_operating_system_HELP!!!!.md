---
title: "Error Loading operating system HELP!!!!"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by Epicfatigue on 2008-02-15
First off what i was trying to do was to dual boot Windows Xp and Ubuntu

I Had Windows Xp loaded on my IDE 80gig HDD

And i tryed installing Ubuntu onto mu 500gig Sata HDD

after installing Ubuntu at the first restart i got Error loading operating system

Any ideas as to where i went wrong?

Thanks

---

### Post by jan quark on 2008-02-15
we have to know on which partitions is Grub installed

boot from the live cd

and run
```

 cat /boot/grub/device.map
```

to see how ubuntu is ordering your hdd's.

---

### Post by ESPOiG on 2008-02-15
Edit. Yeh Device mapping thats what im Getting at thx MAN :D

Ok please explain your problem first, do you see Grub Bootloader that gives you a choice of which OS to boot in, or is the error here and you cant boot into either.

If it is the error that you can choose Ubuntu but it errors when tryin to boot, the problem is probaly that you have your bios configured in a way that is different to your bootloader config, menu.lst in /boot/grub/menu.lst

What I mean by this, is that possibly by adding your 500gb HDD to your computer, the bios may boot them in a certain sequence such as

500GB 1st
80GB 2nd 
This could be just how to boot sequence is configured, and well Grub may see it as the hardware is installed, so it sees it as 80GB 1st and 500GB 2nd, which means, that as you select your OS to boot, if fails to find the the 500GB HDD because it is looking at your 80GB.

Now this is just a problem ive seen and if i explained it properly it makes sense, I had this problem awhile ago so I dont know if it still happens, but who knows.

The way I fixed it is by just adjusting my bios accordingly (the motherboard that i was using, was a MSI K9N SLi Plat). Or another way to fix this, is to boot livecd and do this (if it is the problem)

1. sudo fdisk -l (displays disks eg.
sda 80gb
sdb 500gb)

2. sudo mount /dev/sdb /mnt
3. sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
4. sudo nano /boot/grub/menu.lst
and edit your options accordingly, but try this only if this is the problem.

--

Hopes this helps, if not i hope someone else can answer your problem.

---

### Post by Epicfatigue on 2008-02-15
Yeah worked it out on the drive home in the car from a mates house to here, i didn't even think to see what HDD was loading first in the boot menu changed it to my HDD that had Grub installed and away she went Linux for me YAY!!!

---

### Post by ESPOiG on 2008-02-16
good to know it is fixed

---

