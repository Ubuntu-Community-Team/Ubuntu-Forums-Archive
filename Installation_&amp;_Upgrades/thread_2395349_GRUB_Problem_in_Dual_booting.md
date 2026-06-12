---
title: "GRUB Problem in Dual booting"
date: 2018-06-30
forum: Installation &amp; Upgrades
---

### Post by chandramauli2 on 2018-06-30
When I installed Kubuntu 18.04 alongside Windows7, I was directly logged onto Kubuntu without grub, but when I install boot-repair using the terminal and run it. At one place it showed to choose the disk where should I install the grub, but I need to hit space button to select, instead I just entered and there was a window saying something about it and there was 2 options of Continue without the install of grub and I, the donkey by mistake clicked yes, then it continued as usual. When I restarted my computer, It showed option Ubuntu with one asterisk, then advance option, show setup -(this 3 options) and not windows7, please help me to install that grub. Then I again tried boot-repair, but with no result, and also tried other stuff like update-grub, os probe...etc. but with not result.
Boot-info: [http://paste.ubuntu.com/p/GvpwfPsXsx/](http://paste.ubuntu.com/p/GvpwfPsXsx/)

---

### Post by oldfred on 2018-06-30
You have new UEFI hardware and then installed Windows in the now 35 year old BIOS/MBR configuration. Windows only boots from MBR(msdos) with BIOS.
And Windows only boots in UEFI mode from gpt partitioned drives.

Even though you have newer hardware, since Windows is difficult or impossible to convert to UEFI/gpt you need to always boot in BIOS boot mode. May be called CSM or legacy.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Since Windows is BIOS, you need to move boot flag back to sda1. Use gparted or other tools or your Windows installer or repair disk to make sda1 "active".

Boot the Ubuntu live installer in BIOS mode, add Boot-Repair and in its advanced mode run the full uninstall and reinstall of grub. It should reinstall grub to MBR & update settings for BIOS boot.

If you have newer Windows 8 or 10 you must have fast start up off, which is really just hibernation. And in all copies of Windows must have hibernation off.  Windows will turn fast start up on with updates. And if you upgrade Windows in place it will erase from partition table your Linux partition(s). So back up partition table and all data.

Other choice with newer UEFI hardware is full backup and total reinstall in UEFI boot mode for all systems. How you boot install media UEFI or BIOS is then how it installs. And you must always be consistent.

---

