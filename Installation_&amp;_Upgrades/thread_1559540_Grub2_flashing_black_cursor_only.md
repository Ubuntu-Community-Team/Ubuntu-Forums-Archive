---
title: "Grub2 flashing black cursor only"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by ranyardm on 2010-08-23
Hi all,

  I have an intel atom board (D410PT) and I can run livecds, liveusbs and even boot a grub4dos stick without issue, but install any 10.4 ubuntu variant and all I get is a black flashing cursor.

  It appears as if there is a grub2 incompatibility with this board, which is currently preventing me running a full ubuntu on it.

  I tried struggling on with a liveusb system with a rw partition but it's just not feasable for a home server as the lack of swap just bogs the machine down all the time.

  Grub-legacy no longer appears to be in the repos and neither does lilo (yeah, I really am that old-school that I could cope with lilo if necessary).

  What can be done about a system that doesn't like grub2? (syslinux is fine, but requires fat32, grub4dos works but doesn't like ext3/4, isolinux works but I don't want livecd, I want full install!)

Cheers
--
Martyn

---

### Post by oldfred on 2010-08-23
Welcome to the forums.

Are you sure it is grub2? If you hold shift from BIOS until menu do you get a menu? If you only have Ubuntu installed it does not normally show a menu.

With 10.04 they are using new video systems and many are having issues.

if you've got an i8xx Intel chipset, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by virtuousfox on 2010-09-10
in my case
(Asus P4P800-VM motherboard with 1016 bios, WD Green Caviar Green 1TB EARS-series HDD with 4K sectors and 512b emulation)
installing grub2 (from ubuntu 10.4 dvd, chrooted installed ubuntu 10.4 or System Rescue CD) on aforementioned drive
(partitioned with *sda1=512MB boot, sda2=20G root, sda3=50G ntfs, sda5=4G swap, sda6=all the rest for home* via fdisk with dos compatibility disabled) results in white underscore blinking infinitly as if it just decided to do nothing instead of executing bootloader. 

installing grub(1)_legacy from any place and configuring it to boot ubuntu kernel with its initrd results in succesfull boot.
unless there is some strange graphical stuff in ubuntu grub2 configuration i do not believe that there is a relation beetwen KMS and grub2 (with ubuntu, windows and memtest options autoconfigured) not even showing a menu, or error, or anything.

i thought that half-assed SATA support (even ms/free dos freak out and failes if it not completely disabled) in this board/its bios could confuse it but this is just a speculation.
i thinking about chainloading extlinux or grub(1)_legacy on boot partition to grub2 there but afraid if ubuntu would do `grub-install` on grub update and break ittself.

---

### Post by oldfred on 2010-09-10
I thought grub legacy is still available.

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

---

