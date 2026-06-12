---
title: "Win7 / Ubuntu 18.04 Dualboot only boots into Windows"
date: 2019-06-20
forum: Installation &amp; Upgrades
---

### Post by lukas34 on 2019-06-20
Hi,
I installed Windows 7 and Ubuntu 18.04 straigth after it. I set up seperate partitions for both OS on the same SSD. Installation went fine.
However when starting my computer, I directly boot into Windows without having the chance to choose. 
When entering boot menu I can chose between the Windows bootloader and the SSD where both are installed.
When chosing the latter, I get into Ubuntu but I'd prefer to have the option to chose without going into boot menu.
Any suggestions?
luggie

---

### Post by oldfred on 2019-06-20
Are both installed in same boot mode? Or both BIOS or both UEFI?
Once you start booting in one mode you cannot switch. Or grub can only boots systems installed in same boot mode as Ubuntu is installed.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by lukas34 on 2019-06-20
Thanks!
Boot Info:   [http://paste.ubuntu.com/p/HDF9gsv4SB/](http://paste.ubuntu.com/p/HDF9gsv4SB/)

---

### Post by oldfred on 2019-06-20
You have Windows installed in UEFI boot mode, but Ubuntu in BIOS boot mode.
You can just Boot-Repair to reinstall grub in UEFI mode to convert install to UEFI mode.
You will still then have an old grub in MBR for BIOS boot, but never should use it as you never should boot in BIOS boot mode.
Your UEFI should offer to boot Ubuntu live installer in two modes. One UEFI:flash and other just flash which then is the BIOS boot.

Boot-Repair said this:
> The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to continue?


Also shows screens you first see when booting:
       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The error message on sda2 can be ignored. The Microsoft system reserved must be unformatted, so then it shows error as unformatted.
But other NTFS partitions may need chkdsk.
Make sure Windows fast start up is off, Windows may turn it back on with updates.

---

