---
title: "Ubuntu install problems"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by encephatalis on 2010-09-02
Hello.

I'm having troubles installing Ubuntu 10.04.1 and would greatly appreciate some guidance to get this working on my PC.

My System:
Motherboard:  ASUS X58 P6T Deluxe Ver 2
CPU: Intel i7-950
Memory: 12GB
Video: NVIDIA GTX 295
Drives: RAID 1 (mirror) for Windows 7 and separate WD Cavair Black 1TB devoted for Ubuntu

Downloaded both 64 and 32-bit Ubuntu 10.04 ISO and burned them to discs.

-------------------------------------------------------------------------------------------------

First, tried to install the 32-bit version as a dual boot directly from the disc.  Note that I want a dual boot for Ubuntu to be installed on the separate drive not partitioned within the Windows 7 RAID 1.

Going through the Ubuntu setup for Time Zone, Keyboard layout, Prepare disk space (erase and use entire disk), Why are you? and Ready to install.  The Installing System screen would appear, not processes further than 5% then bring up the error message:

"The attempt to mount a file system with type swap in SCSI1(0,1,0), partition #5 (sda) at none failed."  (see pic)

When disconnecting the Windows 7 RAID 1 (mirror) and changing the BIOS to IDE for a single HDD installation, it gives me the same error message.

I've attached pictures from Gparted of the before and after if that offers any clues. (see pics)

-------------------------------------------------------------------------------------------------

Since I have a 64-bit machine, I also tried installing the 64-bit version of Ubuntu 10.04.  Trying the installation both with the Windows 7 RAID connected or as a single IDE drive.  With the 64-bit disc, I don't get any Ubuntu setup, but the following message:

"BusyBox v1.13.3 (Ubuntu 1:1.13.3 _ (ubuntu11) built-in shell (ash)
Enter 'help' for list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on filesystem.squashfs."

-------------------------------------------------------------------------------------------------

When I install the same 32-bit Ubuntu 10.04 version on a Dell Inspirion 1520, it works just fine without a single hiccup or error message.  Please help offer some advise or guidance to resolve this issue for the dual boot of Windows 7 on RAID 1 and Ubuntu on a separate dedicated (non-partitioned) drive.

Mark

---

