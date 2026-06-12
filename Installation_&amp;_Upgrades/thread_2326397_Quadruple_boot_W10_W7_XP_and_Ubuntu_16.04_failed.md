---
title: "Quadruple boot W10 W7 XP and Ubuntu 16.04 failed"
date: 2016-05-31
forum: Installation &amp; Upgrades
---

### Post by serkam on 2016-05-31
Hi

I have a software development PC ( AMD Athlon64 X2, ASUS M2N-e SLI motherboard, 4Gbytes RAM, NVIDIA GT210 video board ) already with W10 (x64), W7 (x64) and XP (x32) Windows, each in a separate Hard Disk ( 1T each ), all operating normally. 

I tried to install Ubuntu 16.04LTS in the first HD ( with W10 ), shrinking the W10 partition to half and installing it in the last half. Apparently the installation run to completion successfully.

But, when the computer restarted, the W10 doesn't boot anymore and linux doesn't appear in the boot menu ( windows boot menu, as grub menu doesn't appear ). If I try W7 or XP, both boots normally.

I tried to use bcdedit to create a new boot reference to linux, but, I don't know how to define the path to bootsector. The examples in the google ( bcdedit /set {id} path \linux.bin ) doesn't work.

Any help will be appreciated.

Sergio Kamakura

---

### Post by oldfred on 2016-05-31
Is Windows 10 fast start up still on.
That has to be off.
       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)

If running XP, that has to be a BIOS boot with MBR partitioning. But AHCI must be off, unless when installing you added the drivers. Almost impossible to add after the fact with XP. But all newer versions support AHCI and better to have AHCI on.

       
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by jonny3010 on 2016-06-01
Try EasyBCD, see if you can add the boot record with that. Does most of the hardwork for you. 

Maybe the grub boot loader got installed to another disk with W7 or W10. Try booting on each drive and see which one has it. Normally installs to the first drive it sees.

---

### Post by grahammechanical on 2016-06-01
> linux doesn't appear in the boot menu ( windows boot menu, as grub menu doesn't appear ).

Did you, by any chance, install Ubuntu using wubi.exe? I ask because if the Windows 10 drive was the first drive (Windows C: or Linux sda) then the Ubuntu installer would have installed Grub by default on to sda and in the process over-written the windows boot loader.

Unless we direct the installer otherwise it will default to installing Grub onto sda even if we are installing Ubuntu on sdb (Windows D: ) The point about wubi.exe is that it is not compatible with Windows 8 - 10 and is no longer being developed. 

Regards.

---

### Post by serkam on 2016-06-03
Thanks for all.

Due time limitation, I am using only one driver for Ubuntu for now ( all other disconnected temporarily ) and proceeding forward.

After finishing my actual work, I will resume the quadruple boot.

Thanks for now.

Sergio

---

