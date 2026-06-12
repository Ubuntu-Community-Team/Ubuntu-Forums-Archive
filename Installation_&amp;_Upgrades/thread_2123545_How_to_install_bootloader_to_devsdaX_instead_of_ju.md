---
title: "How to install bootloader to /dev/sdaX instead of just /dev/sda proper ?"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by white_eagle-mk on 2013-03-08
I already have the GRUB bootloader installed on my whole hard disk /dev/sda/ from a previous installation.

As I already have Windows and Ubuntu and because for my own purposes I need to have the bootloader replaced with a different one, I need to install another GRUB in /dev/sda4 whch is where I have Ubuntu installed so everything would work in the end after the new bootloader overwrites GRUB in /

How can I do this without starting completely from scratch (backing up, erasing whole hard disk, installing Windows, installing Ubuntu and specifying the boot device not to install in / but to install in the specific Ubuntu partition during installation and so on)?

thank you.

---

### Post by dino99 on 2013-03-08
As i know, grub2 always look for bootable partition(s) across the whole system. On systems with multiple OS (and multiple bootloaders), the active grub loader is choosen following the bios boot order choice. In case you want changing the default ubuntu settings, you can run:

sudo dpkg-reconfigure grub-pc

and set grub on the device (sdx, not sdxx) chosen into the bios (otherwise grub will fail to find a bootable image)

---

### Post by oldfred on 2013-03-08
Are you continuing to use grub2 or something else like EasyBCD.

You have to use the -force command to get grub to install to a partition. You compromise grub as it has to use Blocklists. Grub2 is larger and searches for the rest of grub in the Ubuntu partition. With blocklists it has to hard code the address to find those files and if the file moves it breaks grub. So if you have to have it in a partition have a liveDVD/Flash drive so you can reinstall grub after updates.

If booting with another copy of grub it does not matter.

Boot-Repair also can issue the force command as an option.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

If you can currently boot into your install you can do this also:

       #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not normally choose partitions

---

