---
title: "install prob"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by thudar666 on 2008-07-01
I'm installing on a dell dimension 4600 for someone who wants something to just browse the internet and is tired of viruses, but can't even get it to load as a live cd the message i get is 


busybox v1.1.3 (debian 1:1.1.3-5ubuntu7) Built in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)

any help would be appreciated

---

### Post by overdrank on 2008-07-01
> **thudar666 said:**
> I'm installing on a dell dimension 4600 for someone who wants something to just browse the internet and is tired of viruses, but can't even get it to load as a live cd the message i get is 


busybox v1.1.3 (debian 1:1.1.3-5ubuntu7) Built in shell (ash)
Enter 'help' for a list of built in commands.

(initramfs)

any help would be appreciated

HI and welcome, as Pumalite suggested earlier today 
> I'd burn a new >CD after md5sum
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
, at 4x or less. Beyond that; you might need some boot parameters:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
Try the most common ones first:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off all_generic_ide vga=0x317 vga=788 vga=789 vga=791
To be tried alone or in different combinations until you hit the right one.
[http://ubuntuforums.org/showthread.php?p=5297318#post5297318](http://ubuntuforums.org/showthread.php?p=5297318#post5297318)

---

