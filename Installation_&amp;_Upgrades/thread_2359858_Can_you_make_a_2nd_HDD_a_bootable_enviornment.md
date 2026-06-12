---
title: "Can you make a 2nd HDD a bootable enviornment"
date: 2017-04-28
forum: Installation &amp; Upgrades
---

### Post by sonyboyj on 2017-04-28
I know people like to use DVD's or USBs and use tools like rufus or unetbootin. But i wanna know if its possible using Windows or a Linux Virtual Machine if you could make a 2nd HDD bootable so if i changed the boot order in the bios say to have this 2nd drive boot first it would load a linux live or install environment. How would you make the HDD bootable and then out Linux ISO contents on it to have this work. This is not a must thing i need to do or i would use a easier method. But i would like to know if this method would work or if it is possible.

---

### Post by sp40140 on 2017-04-28
I know that you can install two operating systems in two different drives and grub can read both os and give you option. Bios boot order might matter if you have windows in one hdd. Not sure though.

---

### Post by sonyboyj on 2017-04-28
Would it be possible to install grub on drive 2 then once booted into grub navigate to drive one and select the a Linux ISO and run it.

---

### Post by sp40140 on 2017-04-28
Let's clear up my confusion. Do you want to install os or have virtual os or just have iso file so that you can boot into live env?

---

### Post by sonyboyj on 2017-04-28
I want to setup a 2nd sata drive as a live ent so if i choose to install linux on HDD 1 i could

---

### Post by sonyboyj on 2017-04-28
I want to setup a 2nd sata drive as a live ent so if i choose to install linux on HDD 1 i could

---

### Post by sp40140 on 2017-04-28
Can you please explain a bit more about "live environment" on second HDD?

---

### Post by sonyboyj on 2017-04-28
I want to be able to boot into the 2nd drive and use it like a live cd use the OS or pick install.

---

### Post by sp40140 on 2017-04-28
I see. I am not sure I can help you with it. Interesting requirement though.

---

### Post by oldfred on 2017-04-29
I have ISO on just about every drive directly bootable using grub. Currently I use UEFI with new systems, but did it with BIOS on old system.

I copy all ISO to a separate partition, normally. A few cases with smaller flash drives I have just put the ISO in the same FAT32 UEFI ESP partition. 

I have found getting path & boot parameters correct to be the biggest issues. And part of path can even be correct drive. Boot drive in UEFI/BIOS and grub is always hd0, but if booting from first drive as hd0 and ISO on another drive, that drive can be hd1, hd2 and may change if just plugging in another flash drive.

 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

### Post by yancek on 2017-04-29
The ability to do this has been around for years with Grub2 and there are numerous sites explaining how to boot an iso from Grub2.   You don't need Grub2 on the drive with the iso.  As inidicated above, you need to get the exact path to where the iso is.  Some Linux systems are a little more difficult and all cannot be booted directly from an iso.  Most any Ubuntu derivative should work though.

---

