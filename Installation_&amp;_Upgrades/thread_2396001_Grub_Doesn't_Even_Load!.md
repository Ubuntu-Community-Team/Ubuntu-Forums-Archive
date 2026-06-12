---
title: "Grub Doesn't Even Load!"
date: 2018-07-09
forum: Installation &amp; Upgrades
---

### Post by DeadlyOats on 2018-07-09
Windows7 installed successfully, via Windows 7 Install modified to install on NVMe M.2 SSD drive on USB.  Later, attempted to install Kubuntu 18.04.  Installation went well, but when completed, upon reboot, I didn't even get the grub menu...

Instead, I got a screen that said:

GNU GRUB Version 2.02

Minimal BASH-like line editing is supported.....

grub> _

I tried different UEFI settings, but no joy.

I tried installing Kubuntu 18.04 via DvD, since I don't know how to make a Kubuntu USB install stick.

Well, ever since, now Windows 7 will not start.  It gets up to the Windows logo, then freezes.

Any advice?

---

### Post by powerjas on 2018-07-10
There a at least 2 other threads on this - 

[https://ubuntuforums.org/showthread.php?t=2395999](https://ubuntuforums.org/showthread.php?t=2395999)

[https://ubuntuforums.org/showthread.php?t=2395995](https://ubuntuforums.org/showthread.php?t=2395995)

---

### Post by oldfred on 2018-07-10
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Report will show, but did you install Windows 7 in BIOS or UEFI boot mode.
The DVD is BIOS only by default, but you can copy to flash drive & move/rename a couple of files to make it UEFI bootable.
Someone mentioned that NVMe drives are so new, that Windows 7 in BIOS mode may not work with them? Did your Windows boot before you tried installing Ubuntu?

Best if all systems are UEFI or all are BIOS. But BIOS/MBR is now a 35 years old configuration with many kluges to make it work with newer systems.

[https://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](https://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
       
 How to Clean Install Windows 10 in UEFI mode
[https://www.tenforums.com/tutorials/1950-clean-install-windows-10-a.html](https://www.tenforums.com/tutorials/1950-clean-install-windows-10-a.html)

---

### Post by DeadlyOats on 2018-07-10
Yeah.  I messed up with Win7 repair.  I tried using the Win7 install DVD instead of the modified Win7 USB stick.  I'll retry Win7 repair with modified Win7 USB stick.

I installed Win7 using UEFI.  I thing it's GPTD, not MBR...  I'll have a look at your links to see about Kubuntu...

---

### Post by oldfred on 2018-07-10
Windows will only install in BIOS boot mode to MBR. If drive was gpt, then it erases drive, but leaves backup gpt partition table. Then Linux typically has issues as it does see the MBR, but then also sees the backup gpt.
And then if you installed Windows in UEFI mode it converted drive from MBR to gpt again erasing drive.

Actual data may still be on drive. Not sure testdisk can even find partitions when drive is converted. Photorec may find data, but real hassle to use it. Much better to just restore from good backups.

---

