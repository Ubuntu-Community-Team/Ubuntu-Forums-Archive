---
title: "Grub not showing, Windows 10"
date: 2016-10-20
forum: Installation &amp; Upgrades
---

### Post by loken92 on 2016-10-20
Hi,
I recently installed Ubuntu 16.04.1 on my laptop along with my W10. I am totally new to Linux.
The problem is that I am not able to login to Ubuntu. Every time I reboot it goes directly to Windows.
I have tried the boot repair in try Ubuntu mode. But still the only available boot in Bios is Windows.
Boot repair summary: [http://paste2.org/yU80yzcH](http://paste2.org/yU80yzcH)

I am running an Asus K55v. 

Does someone know how to fix this?
I appreciate any help that can be provided.

---

### Post by Bucky Ball on 2016-10-20
Welcome. Looks like you've installed Ubuntu in Legacy mode and Windows in in EFI. You need to start again and install Ubuntu in EFI mode.

---

### Post by westie457 on 2016-10-20
+1 to what Bucky Ball said.

This also means you should not use Wubi.exe to run the installation. [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by oldfred on 2016-10-20
Some other Asus UEFI installs:
   [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394) 
      
 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)


But the K55N is the only computer that I have seen that would not dual boot in UEFI mode. Not sure if newer UEFI from Asus or updates to Ubuntu have now resolved it.

 Asus K55N booting Ubuntu with secure boot
[http://askubuntu.com/questions/353390/having-windows-8-boot-from-ubuntu-menu-issues](http://askubuntu.com/questions/353390/having-windows-8-boot-from-ubuntu-menu-issues)
Asus K55N just does not boot Ubuntu in UEFI mode. Some things to try, but no solution
[http://ubuntuforums.org/showthread.php?t=2137233](http://ubuntuforums.org/showthread.php?t=2137233)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)
ASUS-K55N is just not able to boot an EFI linux, converted to BIOS with MBR partitioning - UEFI Windows 7

---

