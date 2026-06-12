---
title: "upgrading to Ubuntu 12.04 LTS, grub rescue prompt"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by lamborg on 2012-06-12
Hello, 

I followed message in Xubuntu for upgrading to Ubuntu 12.04 and after automatic process is done, the rebooting shows only grub rescue prompt. 

I found many similar cases posted in internet so I picked frequently seen suggestion to install boot-repair. I started xubuntu from a liveCD (v11) and then installed boot-repair by apt-get. Boot-repair does start up and do the processing, but this does not solve the problem. Below is the boot info. 

[http://paste.ubuntu.com/1037403/](http://paste.ubuntu.com/1037403/)

I then found that the second hard disk I installed xubuntu via wubi is 300Gb that might be causing the problem, so I tried "advanced options" in the boot-repar GUI but the tab "GRUB options" is empty and no option is available. 

Machine is dual-boot of XP or Xubuntu (Wubi). 

If someone could give me an advice for geting out from this, I would be very much helped...

Sincerely, 
lamborg

---

### Post by darkod on 2012-06-12
It seems to me you shouldn't run boot-repair when running wubi. Boot-repair installs grub2 on MBR of all disks like you would expect in a dual boot when ubuntu is on its own partition. With wubi, that's not the case because you keep using windows bootloader on the MBR.

Right now windows bootloader has been overwritten by grub2.

You need to use your windows install media to repair the windows bootloader.

Also, are you running raid? You seem to be.

Don't forget that wubi is a virtual file inside windows, so not all commands and procedures that apply to standard ubuntu work on wubi. In fact, for long term use it's not recommended to use wubi at all because it can break during upgrades or updates sometimes. Wubi is designed only for a short try, not to be run as a main system.

Repair your windows bootloader first, then see if windows boots fine, and if wubi still doesn't work post the new results of the boot info script.

---

### Post by lamborg on 2012-06-12
Hi Darkod, 

thanks a lot. 
I will follow your advice. 

lamborg

---

### Post by YannBuntu on 2012-06-14
Hello

> **darkod said:**
> It seems to me you shouldn't run boot-repair when running wubi. Boot-repair installs grub2 on MBR of all disks like you would expect in a dual boot when ubuntu is on its own partition.

Boot-Repair should not install GRUB in the MBR of a Windows+Wubi system. (if you have seen a case were it did, please [report the bug here]("https://bugs.launchpad.net/boot-repair")).

In the log in post #1, you can see:
```
=================== Recommended repair
recommendedrepair
This setting will restore the [(generic mbr)] MBR in sdc, and make it boot on mapper/asr_HostRAID-A1.
Additional repair will be performed: unhide-bootmenu  repair-wubi fix-windows-boot
```

As it is a Windows+Wubi system, it has not installed GRUB in the MBR. It has:
- made sure the MBR was booting Windows.
- made sure the Windows bootloader is not 0s
- opened a file browser to allow the user to backup its Wubi documents
- proposed a fsck of the Wubi filesystem

**@lamborg:** please could you run Boot-Repair, click "Advanced options", click the "Backup partition tables.." button, save the ZIP file somewhere, then send it by email (yannubuntu ATT gmail DOTT com), or attach it to your reply in this thread.

---

