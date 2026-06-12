---
title: "Kubuntu/Windows 7 No Boot"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by gus_zernial on 2011-04-07
I have Kubuntu 10.10 with GRUB2, dual boot with a Windows 7 partition. This worked fine until recently, when Windows 7 stopped booting. Now when I try booting the Windows 7 partition, it starts to boot and then reboots before fully booting into Windows. 

Kubuntu boots fine, and the Windows 7 boot option appears to be correct in the GRUB boot menu. I have tried ... 

-reinstalling GRUB, grub-install to the disks, update-grub. 

-Running the Windows 7 Startup Repair option - it it unable to fix the problem and its log says only that the problem is due to "unspacified changes to the system" - which changes I am not aware of.

-Restoring Windows to a previous checkpoint - there was one previous automatic checkpoint, at a date when I knew it booted successfully, but the restore didn't solve the problem.

-Doing chkdsk /F on the Windows filesystem - it did fix some errors but that didn't help.

-Running bootsect /FixBoot and /FixMbr. The latter blew away GRUB, which I subsequently repaired, but neither fixed the Windows boot.

I can "see" Windows by looking at the Windows partition from Linux, and the Windows directories seem to be there. Plus I can see Windows it I boot into the Windows command prompt. However, when I run bootsect /ScanOs from the Windows command prompt it says it cannot find any Windows installations. Would appreciate further ideas as to how to repair.

Thx, Gus

---

### Post by Hedgehog1 on 2011-04-08
It looks like you have done the obvious and logical things.

A shot in the dark - is the boot flag still set on the windows partition? You can see it (and set it) in gparted:

[IMG]http://img855.imageshack.us/img855/6408/bootflaggparted.png[/IMG]

Right click on the Windows partition, select 'manage flags'. You will want a check mark in this box...


***The Hedge***

:KS

---

