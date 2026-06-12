---
title: "Dual boot install from Ubuntu."
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by Douten on 2008-10-03
Hello!

I've already installed Ubuntu and I'm running on it but I would like to make a partition for dual boot xp. How would I do this? can someone link me to a guide of making a partition, checking where the MBR is, and installing xp onto that partition correctly? I'm pretty sure my MBR isn't where it's suppose to be for dual boot, and I don't know how to move it.

Thanks : )

---

### Post by sayakb on 2008-10-03
To begin with, you need to create a partition of appropriate size for Windows:
[http://manual.sidux.com/en/part-gparted-en.htm](http://manual.sidux.com/en/part-gparted-en.htm)

After you're done creating the partition, insert the Windows CD and install it on the free partition.

After you have installed Windows, you should lose your bootloader (GRUB) and you'll boot in straight to windows. To restore GRUB, download SuperGrubDisk ([http://supergrubdisk.org/](http://supergrubdisk.org/)) and burn the ISO on a CD. Now reboot and boot into the Super Grub Disk. There shall be an option to restore GRUB. Restore it and reboot you computer.

---

### Post by Douten on 2008-10-03
Thanks, but when I run gparted I'm unable to make another partition for my hdd, every option is grey out except unmount, but I can't unmount it.

---

### Post by caljohnsmith on 2008-10-03
> **Douten said:**
> Thanks, but when I run gparted I'm unable to make another partition for my hdd, every option is grey out except unmount, but I can't unmount it.
Are you running gparted from a Live CD? You can't run it while you are in your Ubuntu install on your HDD, because then your HDD is in use. 

Also, just a small tip, but I would highly recommended that you install Win XP to a primary partition, not a logical one, unless you want to go through some trouble getting XP to boot; booting XP from a logical partition can be done, but it is more ideal if you can give XP a primary partition. Let us know how it goes or if you run into problems. :)

---

### Post by Sef on 2008-10-03
> Also, just a small tip, but I would highly recommended that you install Win XP to a primary partition, not a logical one, unless you want to go through some trouble getting XP to boot; booting XP from a logical partition can be done, but it is more ideal if you can give XP a primary partition. Let us know how it goes or if you run into problems

Windows oses like to be on the first primary partition.

---

