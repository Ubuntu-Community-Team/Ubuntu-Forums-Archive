---
title: "After boot repair impossible to start Ubuntu"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by paglia96 on 2013-08-23
I had Ubuntu installed alongside Windows 8. All was OK. Then i messed up my Ubuntu installation and decided to reinstall it keeping my home partition.

I reinstalled but as always Windows wasn't bootable from grub the first time (but Ubuntu started correctly!). 

I ran grub-repair directly from my Ubuntu installation and at the end it said something about my boot files (efi partition) being too far from my system (Ubuntu). It never said anything like that the previous times, but I the previous times I ran it from a live cd of either Ubuntu or Boot Repair Disk.
The next time I started the PC only Windows started without grub, anything, directly.


I tried all: reinstalling Ubuntu three times, running boot repair, reinstalling grub on the right partition from the livecd but nothing: Windows always start without showing  grub.


A first boot info from Boot Repair showed some error mounting ntfs partitions [http://paste.ubuntu.com/6015718](http://paste.ubuntu.com/6015718)

I read that it may be caused by Windows being suspended or fast startup enabled. Fast startup is not enabled and I did shutdown my pc not suspended it.

Anyway windows seems to startup very quickly like when fast startup is enabled (but it isn't!).


This is a new bootinfo [http://paste.ubuntu.com/6016671](http://paste.ubuntu.com/6016671) which doesn't seem to have any problem about ntfs partitions like before.

But nothing.

I'm out of solutions.

---

### Post by oldfred on 2013-08-23
If you turn secure boot off, and choose ubuntu in UEFI menu does it boot, or do you get a black screen (video issue)?

Boot-Repair dumps UEFI info and it shows as a boot option in you UEFI.
 Boot0003* ubuntu	HD(2,e1800,82000,0a543b96-7861-11e2-8d38-d60b12dec0bc)File(EFIubuntugrubx64.efi)



It looks like an Ultrabook which has Intel SRT to use SSD as cache. You have to turn Intel SRT and fast boot off to get Ubuntu to install correctly.
The report of files far on drive was for BIOS boot system primarily USB boot from BIOS. I have not seen the issue with any UEFI boot systems, but Boot-Repair posts the warning. I do not think that is related to any boot issues.
With Ultrabooks you also usually have dual video which can cause issues.

---

### Post by paglia96 on 2013-08-23
thanks but it's not an Ultrabook, a plain toshiba notebook, no ssd. Actually i tired to manage the boot from Windows, installed an app called EasyBCD but while it wasn't able to boot ubuntu it allowed me to access grub. So from my Ubuntu installation i reinstalled grub and now it seems to work, I don't understand why but anyway actually it works.

---

### Post by oldfred on 2013-08-23
EasyBCD can fix some Windows issues, and some with BIOS and primarily Windows users have used it to boot Windows & Ubuntu. But you should not need it to boot with UEFI as each system has its own bootloader in the efi partition.

---

