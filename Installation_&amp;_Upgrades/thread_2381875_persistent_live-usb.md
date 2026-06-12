---
title: "persistent live-usb"
date: 2018-01-06
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2018-01-06
Hey. For a couple of years ago, it was possible to make a persistent file in start up disk creator, with a slide you chould reserve memoryspace for that. That option is nog longer there, it think? I tried to use unetbootin, but after tried upgrade the system, it get broken. The upgrade stoped, and after reboot the system froze, dit not work. Is there a simple way to make a persistent boot usb, that are up to date and hopfully even save wifi-config?

Used, 16.04.3 64 bit Ubuuntu desktop image.

/Cheers

PS. By the way.. I notice that if I have an ubuntu install on an harddisk, it is quite easy to pop in the disk in an another hardware and it work more or less, before you do an upgrade. After the upgrade, it works fine. That was not possible with w7. Have it on a Asrock Ion with an Atom-processor, that W10 did not support, so I move the hdd to a more capable hardware (intel core 2 duo), and it refuse to booth, even in failsafe mode :( The problem maybe to make an install on usb-stick is that normally system write a lot to the system, and the usb-stick are not made for that?  /Edit: Change little, because it was bad language.

---

### Post by sudodus on 2018-01-06
You can try mkusb. It can create persistent live drives with a **partition** for persistence. It means that the size is not límited to 4 GB, as it is in systems with a file for persistence in a FAT32 file system.

See the following links,

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

Persistent live systems are sensitive, so it is a good idea to take frequent backups. There is a tool for backup in the persistent live systems created by mkusb,

[Backup and restore of persistent overlay data](https://help.ubuntu.com/community/mkusb/persistent#Backup_and_restore_of_persistent_overlay_data)

---

### Post by sudodus on 2018-01-06
You may want to look at installing a full system to a USB drive (pendrive, HDD, SSD), like it were into an internal drive. If a pendrive, you should tweak the system to decrease wear of the memory cells. See this link (and links from it),

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

Edit: Tweaks according to [Final_system_tweaks](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks)

---

### Post by grahammechanical on 2018-01-06
When switching hard drives to other hardware we should make sure that Ubuntu is using an open source video driver. The other hardware may have a different graphic adapter. And Ubuntu may have a proprietary video driver that is incompatible with the graphic adapter in the other machine.

Regards

---

### Post by C.S.Cameron on 2018-01-06
You should never ever do an update on a persistent USB, and it is not easily possible to do a kernel upgrade.

If you need the latest updates you must do a Full install to the USB.

This should work on most machines as long as you do not install proprietary drivers.

If you do not need the latest updates mkusb is a great choice for installer.

I often mix the methods, I do a mkusb install, then delete the ISO9660 and casper-rw partitions and then do a full install to the empty space.
This allows the drive to work on both BIOS and UEFI boots.

---

### Post by Azyx on 2018-01-06
Yes. it is impossible to do a kernel upgrade, because in need reboot? Yes! take away propetarian drivers before you shall switch machine for a harddrive. It can really **** up, even with same brand gfx, for instance nvidia.

---

### Post by sudodus on 2018-01-07
In a persistent live system, the kernel is started before the overlay system for persistence is activated. So the kernel will be fetched from the original system (that comes from the iso file). This is different from an installed system.

---

### Post by Azyx on 2018-01-13
Thanks for all responses :)

It have taken time, because I had problem with Unity on a dual pentium laptop (Among the first Intel dualcore-processors) and normaly there are no problems :) Unity/compiz-sigfaultx get broken because a bugg coming the 4-jan this year, but gnome3 works, even on older cpu :) There are no problems with AMD or Core-2-duo and newer I think :)


 I have now made two FAT32-partitions on an USB-stick, approx 4GB and 10GB, I flagged boot on the 4GB-partition and with Unetbootin made a persistent file. The other partition mount fine under live-session and I can use that as a normal penndrive. Ubuntus Startup disk creator, do not support to install on a partition (only hole pendrives) AND do not support persistent files any more, I think? I wonder if  I can make the boot-partition hidden, so when I use the penndrive on a computer the boot-partion are not visible?

Thanks again for all knowledge :)

---

### Post by sudodus on 2018-01-13
> **Azyx said:**
> Ubuntus Startup disk creator, do not support to install on a partition (only hole pendrives) AND do not support persistent files any more, I think?

That's correct.
> 
I wonder if  I can make the boot-partition hidden, so when I use the penndrive on a computer the boot-partion are not visible?


Do you mean hidden or not automounted when connected to Ubuntu or Windows or both? (I don't know, but someone else might know.)

---

### Post by Azyx on 2018-01-13
I mean to flag the partition bootable AND hidden in gparted. In gparteds manual it only say that some OS don't see the partition but I wonder if BIOS see it? Does boot-flag override hidden? But the most important is that it does not automount ether if it is windows or Ubuntu.  Anyway I test tomorrow :) Little tipsy and tired now ;) /Cheers

---

### Post by C.S.Cameron on 2018-01-14
Windows 10 can see the FAT32 and NTFS partitions on a flash drive but not ext partitions.
A mkusb install uses ISO9660 and ext2 partitions which should not be visible.
It will also create a NTFS partition that should be visible to Linux and windows.

If you do a Full install to USB leaving the first partition as FAT32 or NTFS the OS will install to an ext partition which will not be seen by Windows.

---

### Post by Azyx on 2018-01-18
Thanks. It was possible to check booth bootable and hidden, but there be something wrong on the disk, so it are probably not a good way. /Cheers

---

### Post by sudodus on 2018-01-18
You can try mkusb - let it make a persistent live drive in your USB drive. It should work without any manual tweaks afterwards.

---

