---
title: "Dual booting with windows 8.1"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Thomas_J_Marshall on 2014-04-18
Recently got a new pc.  My old pc dual booted w7 and ubuntu 13.1, new pc has w8.  It has uefi and looking at a few posts it appears tricky to set up dual boot, at least to me!  My old system had the 2 os on separate drives so my question is if I load the drive into the new pc how do I configure boot menu?  :)

---

### Post by oldfred on 2014-04-18
Old PC was probably BIOS boot.
If just moving old hard drive with Ubuntu, you can boot in BIOS mode. But only from UEFI/BIOS menu and you may have to turn on/off UEFI or turn on/off BIOS/CSM/Legacy boot modes. Some systems will auto switch.
BIOS mode has no secure boot so to even enable BIOS mode you have to have secure boot off.
Also you must turn off fast boot or the always on hibernation if dual booting. That leads to issues, otherwise.

But long term or if totally reinstalling you will want all new drives as gpt partitioned. And best to have Ubuntu in UEFI boot mode, so you can dual boot from grub menu.

Either way a full image backup of Windows and a Windows repair flash drive should be made before doing anything. 

If installing Ubuntu on Windows drive only use Windows to shrink the NTFS partition and immediate reboot so it can run chkdsk and make repairs for its new size. Do not create partitions with Windows.

Lots more details and links in the link in my signature.

---

### Post by Thomas_J_Marshall on 2014-04-21
> **oldfred said:**
> Old PC was probably BIOS boot.
If just moving old hard drive with Ubuntu, you can boot in BIOS mode. But only from UEFI/BIOS menu and you may have to turn on/off UEFI or turn on/off BIOS/CSM/Legacy boot modes. Some systems will auto switch.
BIOS mode has no secure boot so to even enable BIOS mode you have to have secure boot off.
Also you must turn off fast boot or the always on hibernation if dual booting. That leads to issues, otherwise.

But long term or if totally reinstalling you will want all new drives as gpt partitioned. And best to have Ubuntu in UEFI boot mode, so you can dual boot from grub menu.

Either way a full image backup of Windows and a Windows repair flash drive should be made before doing anything. 

If installing Ubuntu on Windows drive only use Windows to shrink the NTFS partition and immediate reboot so it can run chkdsk and make repairs for its new size. Do not create partitions with Windows.

Lots more details and links in the link in my signature.Thanks.  I may just do a fresh install on the same drive, may as well make use of uefi.  I've read that you can install ubuntu 13.1 and above without disabling secure boot.  Do you know if that is so?

---

### Post by oldfred on 2014-04-21
I would leave secure boot off for now. Sometime in the future you may want it.
Right now it is marketing for Microsoft. It has had so much issues with secuity (but very few with booting) it had to do something to convince users that it is better.

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

