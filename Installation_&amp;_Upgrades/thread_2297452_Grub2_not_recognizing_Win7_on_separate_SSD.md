---
title: "Grub2 not recognizing Win7 on separate SSD"
date: 2015-10-03
forum: Installation &amp; Upgrades
---

### Post by anqi_fu on 2015-10-03
Hi, I'm a new user trying to get Ubuntu 14.04 to dual boot with Windows 7 on separate drives. I first installed Windows on sda and then Ubuntu (UEFI) on sdc. (My sdb drive is purely for storage). During installation, I manually partitioned sdc with a /boot/efi on sdc1 and had the boot loader install to that partition. Now, I boot up from sdc and the Grub2 menu does not show Windows 7 at all, only Ubuntu. I tried running sudo update-grub and it does not find Windows, even though my Windows volume is available (I can browse through it from the sidebar). I also tried running boot-repair from liveUSB, setting sdc1 as the /boot/efi partition and boot flag to sdc1 in Advanced Options, but this did not change anything. The boot-repair utility gave me the following output: [http://paste.ubuntu.com/12658611/](http://paste.ubuntu.com/12658611/)

I am concerned by the note at the top that says Grub2 cannot find core.img, could that be contributing to this issue? I've tried re-installing Ubuntu multiple times, running boot-repair multiple times, and I'm generally out of ideas.

---

### Post by yancek on 2015-10-03
I don't use UEFI so can't give you a solution.  However, from everything I have read, you will always have problems when you install a bootloader to the MBR on a drive that you are using UEFI which is what you have.  Also, you can see that the core.img on sdc cannot be found.  Not sure how this affects UEFI.  You do have the EFI partition for both Ubuntu and windows but on the Ubuntu hard drive.  That might be a problem as windows is on a different drive.  I'd suggest waiting for someone with more knowledge on UEFI.

---

### Post by oldfred on 2015-10-03
Not sure how you got Windows efi boot files in the ESP - efi system partition on sdc.

UEFI and BIOS are not compatible. Once you start booting in one mode you cannot change, or once you are booted into grub, grub can only boot systems installed in the same boot mode. You can use UEFI or one time boot key, often f10 or f12 to to boot systems installed in different boot modes.

Your Windows is on a MBR(msdos) partitioned drive, so Windows can only boot in BIOS/CSM boot mode. Windows also only boots from gpt partitioned drives with UEFI.

Best, but not required, if on different drives, to have all systems installed in same boot mode, all UEFI or all BIOS.

---

### Post by anqi_fu on 2015-10-03
Thanks all, I re-installed Ubuntu with MBR and dual boot works fine now. I had assumed Windows 7 was UEFI, but apparently that only became the default with Windows 8.1 and up.

---

### Post by oldfred on 2015-10-03
You can install Windows 7 in UEFI boot mode, but standard installer is BIOS. You have to copy to flash drive in a FAT32 partition and move around some files so you have the /Boot/bootx64.efi that UEFI expects to boot from on a flash drive.

---

