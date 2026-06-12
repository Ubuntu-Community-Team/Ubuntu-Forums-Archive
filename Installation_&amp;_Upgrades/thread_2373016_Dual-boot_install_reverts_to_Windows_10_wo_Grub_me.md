---
title: "Dual-boot install reverts to Windows 10 w/o Grub menu."
date: 2017-10-01
forum: Installation &amp; Upgrades
---

### Post by Bupkus on 2017-10-01
First, thank you for reading this post. My problem is with a dual boot of Windows 10 and Ubuntu MATE 17.04.
I'm familiar with pre-UEFI conifigurations but I can't seem to get a dual-boot with 2 solid state drives to work for longer than a day. 
Attached below are some pics of my installations after the fact. I first installed Windows 10 on an Intel 730 240gb SSD and followed that with Ubuntu-MATE 17.04 on a Samsung 830 128GB SSD.
The installations are still rather new so a redo is possible. I will see if I am allowed to enter more pics that could be useful.
A 32GB USB with a live installation of Ubuntu-MATE has been inserted for attempted boot into Ubuntu. I won't work when appearing with USB: TS RDF5 SD TRANSCEND TS37, but did once with what was either AHCI or possibly UEFI..???
[ATTACH=CONFIG]276923[/ATTACH][ATTACH=CONFIG]276924[/ATTACH][ATTACH=CONFIG]276925[/ATTACH][ATTACH=CONFIG]276926[/ATTACH][ATTACH=CONFIG]276927[/ATTACH]

---

### Post by yancek on 2017-10-01
Clicking on your 'Attachment' links gives an Invalid Attachment message.  Might try doing them again.  The link below explains dual booting windows/Ubuntu in UEFI.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by wheatpenny2 on 2017-10-01
Go into UEFI settings and make sure Ubuntu is at the top of the boot order. If Windows boot manager is at the top then the grub menu won't appear and it will always boot into windows, but with Ubuntu on top then you get the Grub menu with a choice of which OS to boot into. (I had to figure this out by trial and error, because none of my Ubuntu books saw fit to mention it).

---

### Post by oldfred on 2017-10-01
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If you disconnect a drive, UEFI's NVRAM loses that UEFI entry. It can be added again manually.

You do need to have AHCI on.

What brand/model system?

---

