---
title: "Installation of ubuntu-8.04.1-desktop-i386"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by Seismic1 on 2008-10-16
Hi

I've looked through the forums for similar problems, but without luck. When I try to install from the CD, the installation splash seems to refuse to run commands.

The options are:
* Try ubuntu without install..
* Install
* Check CD for errors
* Check memory
* Start from HDD

The only option acctually working amongs these is the last one, that boots the ancient version of ubuntu I want to replace. The system is:
* Celeron 2.53GHz
* RAM 1224MB
* Lots of space on HDD

I downloaded from:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Ubuntu 8.04 LTS Desktop Edition - Supported to 2011
Standard personal computer (x86 architecture, Pentium™, Celeron™, Athlon™, Sempron™)

Regards,
Seismic1

---

### Post by Pumalite on 2008-10-16
Burn a new CD. Download and install ImgBurn:
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Once installed; go to Mode>ISO>Burn
Select 1x as the speed of burn. Clean the lens in your burner.
Do md5sum on the iso. Do not use CD-RW

---

### Post by Seismic1 on 2008-10-16
Hi.
I've tried burning another CD at a lower speed before. Now i just tried with your proposed method and software. No change. I still can't get past the splash.

Regards,
Seismic

---

### Post by Pumalite on 2008-10-16
Try some boot parameters:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html) 
Try the most common ones first:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off all_generic_ide vga=0x317
To be tried alone or in different combinations.

---

### Post by Seismic1 on 2008-10-16
Hi

I suppose I need to save the boot parameters in the old ubuntu first? The only way I can enter Grub otherwise is to by-pass the install with the last option (start from HDD)

Regards,
Seismic1

---

### Post by Seismic1 on 2008-10-16
My bad on that one. Grub preceds the installtion.

Regards,
Seismic1

---

### Post by Seismic1 on 2008-10-16
Ok, here's the next newbie question then.
According to the guild you linked the reccomendation is to edit the kernel line. However, this will get me to the current installed version, wont it? Atleast that is the result I keep ending up with.

Regards,
Seismic1

---

### Post by Pumalite on 2008-10-16
Follow the guidelines for adding boot parameters while trying to boot a Live CD, which was your initial question.

---

### Post by Seismic1 on 2008-10-16
Then I must have been unclear on the issue. I'm not trying to run the live version. I'm trying to "upgrade" to the new version by using the install option (permanently).

---

### Post by Pumalite on 2008-10-16
For un upgrade you need the Alternate CD

---

