---
title: "[SOLVED] Boot: Error18 selected cylinder exceeds BIOS"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by ubix on 2008-11-22
After changing my ASUS motherboard for "FXF nFORXE 610i" motherboard and reinstalling my dual-boot system I started to experience a weird boot problem. After selecting the OS in GRUB I get the following error message:```
Error 18 selected cylinder exceeds maximum supported by BIOS.
``` I regain my WinXP OS by running "FDISK /mbr" however, as anybody knows  Ubuntu is lost when one does that.

---

### Post by ubix on 2008-11-23
In another thread I started out by saying *"There must be something wrong with dual bootsystems in [color=navy]**Hardy**[/color]. However, things point to a hardware and/or driver problems on some HW platforms. After changing my ASUS motherboard for "FXF nFORXE 610i" motherboard and reinstalling my dual-boot system I started to experience a weird boot problem. After selecting the OS in GRUB I get the following error message:"*```
Error 18 selected cylinder exceeds maximum supported by BIOS.
```

_My suspicions that the new releases of Ubuntu  since the release of [color=navy]*Hardy*[/color] were to be blamed for my problems, indeed, were incorrect_. At first I thought there could have been any number of problems starting with the motherboard's BIOS, the large size of the swap I defined, the disk partitioning system and of course the GRUB system. I narrowed down the problem to the issues revolving around disk partitioning and the way M$ Widows work. Beside the above mentioned **Error 18**, my first hint of where to look was the fact that Windows XP installation CD didn't like to see the Extended partition. It immediately clicked that the ***"Extended DOS partition"*** concept may be foreign to NTFS, which I was using this time around for my WinXP partition. When I removed the Extended partition, my WinXP installation CD started to work again. Pointing to DOS/FAT/NTFS screwup, I first tried to install WinXP into FAT32 partition, only to find out that Extended partition again rendered my M$ WinXP installation CD useless. However, after removing the offending Extended partition, as you may by now already anticipate, I was able to installing WinXP into FAT32, just like I did earlier into NTFS. This time I had hoped however, that installing WinXP into FAT32, recreating the Extended partition with GParted, and then  starting Ubuntu installation by creating all my 15 Ubuntu partitions as always would not give me the notorious **Error 18**. Indeed, the final gratification and confirmation of the theory came after a successful boot via GRUB into either OS.

I did two things differently this time, however. This prevents me to claim with absolute certainty that ***FAT32*** rather than ***NTFS*** is the solution, namely I changed my swap size to now 4 GiB since I realized I only use 2 GiB of RAM, and also before I created / (root) as well as swap partitions into the Extended area, but are now sitting right after FAT32, and before the Extended partition.

---

