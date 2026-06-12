---
title: "copying/moving mbr and grub to pendrive - UEFI"
date: 2020-12-18
forum: Installation &amp; Upgrades
---

### Post by linerman on 2020-12-18
Hi,

I have an Legacy/UEFI motherboard with 3 disks. 
1. SSD with Windows 10 boot manager and windows 10 system
2. HDD with NTFS data
3. External Seagate HDD drive with Ubuntu 20.04 mbr/grub boot manager and Ubuntu system

If boot options are:
1. UEFI - SDD /Windows 10 boot manager/
2. Legacy HDD /ubuntu grub/

then Windows 10 starts. It is ok.

If boot options are:
1.  UEFI - disabled
2. Legacy HDD /ubuntu grub/
3. Legacy SDD

then Ubuntu starts. It is also ok.

The problem is that I do not want to hassle with bios boot settings every time when I want to switch system.
The best option for me (no, not the dual boot) would be to have a boot options like:
1. UEFI - USB(pendrive) with MBR/Grub (to start Ubuntu)
2. UEFI - SDD (with windows 10 boot manager) 
3. Legacy HDD

So, the key thing is that if I put in my pendrive, Ubuntu would start. If there will be no pendrive, then Windows 10 would start.

Is there a possibility to do that, and how to make such MBR/GRUB (UEFI??) pendrive?

Regards
Martin

---

### Post by tea for one on 2020-12-18
> **linerman said:**
> 

The problem is that I do not want to hassle with bios boot settings every time when I want to switch system.

> So, the key thing is that if I put in my pendrive, Ubuntu would start. If there will be no pendrive, then Windows 10 would start.

Dual booting is complicated enough without the introduction of using a pendrive as a type of lock/unlock access to an operating system.
The best option is to follow the normal procedure for dual boot systems and use [COLOR="#0000FF"]Boot Mode Matching
[/COLOR]
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

In effect, back up your Ubuntu data and reinstall in UEFI mode with GPT.

---

### Post by yancek on 2020-12-18
>  The problem is that I do not want to hassle with bios boot settings every time when I want to switch system. 

Simplest method would be to reinstall Ubuntu UEFI as suggested above and all the details you need are in the Ubuntu documentation in the link in post 2.
Grub installed in Legacy mode as is your will not boot an EFI install of windows.
Grub installed in EFI mode will not boot a Legacy install of windows.

The lin posted above has a section on 'boot mode matching' which explains this.

---

### Post by linerman on 2020-12-18
I did it before. This external disk had problems with installing Grub uefi on it.
There were errors, and bios did not recognize that disk as uefi boot.
Second thing, in the end of the day, I would like to remove mbr/grub from this external drive. I have some other partitions on it and would like to encrypt them with VeraCrypt. I guess VeraCrypt will overwrite mbr sector of the disk. 
Anyway, prefer to use usb stick.

---

### Post by tea for one on 2020-12-18
You can install Ubuntu to an external HDD and allow grub to control the booting of Ubuntu **only**.

You will have to isolate your Windows drive during the installation process by physical removal or de-activation via UEFI set up.

With only one drive available, grub should install OK.

After you have installed Ubuntu, you will have to choose either OS via the PC boot menu dedicated key.

Ensure your backups are in good order and use UEFI mode with GPT.

---

### Post by linerman on 2020-12-22
I did not know the trick with boot menu dedicated key. 
It did the thing. I guess, I do not need to boot from pendrive anymore.
Thank you.

---

