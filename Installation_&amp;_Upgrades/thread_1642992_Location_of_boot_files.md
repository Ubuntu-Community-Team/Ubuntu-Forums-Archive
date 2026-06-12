---
title: "Location of boot files??"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2010-12-11
When considering installing Ubuntu into a (removable) usb stick, as a full install, not live, I realise I do not fully understand the significance of the decision of where to point the installer for the boot stuff when using the advanced install options in the live CD (Ubuntu 10.10)

I am aware that grub2 files get installed into a directory usually in the main root partition, and that usually the mbr is used to point to the grub2 files.

I do not yet understand other, more exotic methods of installing and then using the boot files. For example, the installer advanced options include offering the usb main partition (the one being used for / ) (is /dev/sdc1) and also the drive itself, sdc.

If I chose sdc1, would the pointer which would normally go into the mbr, then be situated actually inside the partition? If so what method would be used to subsequently boot from it?

If I chose just sdc, then I guess if the drive was active (?) it would have an mbr written during the install. Is this correct?
My understanding includes that an mbr is at the start of a drive, but with the exotoc options, can it effectively be situated inside a partition? And further, can it be at the start of say, a removable usb stick when at the same time the existing hard drive in the machine has an active mbr?

I would be grateful for comments to help further my understanding here. tia.

---

### Post by lemming465 on 2010-12-12
The food chain is usually something like:
1) BIOS
2) first sector of some disk ("master boot record")
3) secondary boot loader (on sectors 2-63)
4) boot menu and other files from some disk partition (/boot)
5) kernel + initial ram disk
6) live system on root filesystem (/sbin/init)

The critical step in the boot process is #3, the secondary boot loader, as that is the one that is specific to the filesystems and kernel loader.  Most multiboot
strategies (LILO, Grub1, Grub2, EasyBCD on windows, ...) pick up there.

By default Ubuntu will write 2 & 3 to the first partition on the first hard drive; if you pick the "advanced" button you can direct them elsewhere.  In your case, with an external USB drive, you want to put them there instead.

---

### Post by candtalan on 2010-12-12
Thanks, that gets me started nicely.

---

### Post by oldfred on 2010-12-12
While it primarily is discussing windows at the end it also mentions Linux. You do not have to read the whole thing as it is very detailed, but just review the pictures to understand the boot process. Windows has one additional step in that it also puts code into the windows partition's boot sector. Grub does not (normally).

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Computers can only boot from the MBR. Old IDE computers would only boot from the MBR of the primary master. But new motherboard's BIOS with SATA systems let you choose what drive to boot in BIOS or one time boot key.

---

