---
title: "&quot;No Boot Device found&quot; error, Trying to Dual boot Ubuntu and Windows 10"
date: 2018-12-18
forum: Installation &amp; Upgrades
---

### Post by wrathod on 2018-12-18
I had Windows 10 running on my HP 15-R203tx laptop.
I recently installed ubuntu using "EFI only image" method succesfully.

**Problem**: After the ubuntu installation the laptop says "No Boot Device found" on startup


I am still able to access the installed OS (only ubuntu, windows is still missing) by pressing f9 key and then loading GRUBX86.EFI file after certain amount of navigation in boot menu.

I have tried boot repair, here is the report [http://paste.ubuntu.com/p/25bJ8wFj5Q/](http://paste.ubuntu.com/p/25bJ8wFj5Q/)

Sorry if I have used wrong terminology as i am a novice.

Need a solution to fix the problem. I have already spent more than 48 working hrs on this.

Thanks for the help
shivaram :)

---

### Post by jeremy31 on 2018-12-18
What happens if you try switching to Legacy boot in BIOS?

---

### Post by yancek on 2018-12-18
Your install of Ubuntu is a mix of Legacy/MBR and EFI.  You have Grub boot code in the MBR and grub.cfg shows the menuentries as msdos and fdisk also shows the partition type as dos so the suggestion above would be the best step, enable Legacy in the BIOS.  You should then run:  sudo update-grub from a terminal in Ubuntu as there is currently no entry for windows.  There are no windows files showing in the EFI partition which would be unusual for windows 10.

---

### Post by oldrocker99 on 2018-12-18
There is no real benefit using UEFI over legacy. My own experience is that UEFI installations will fail to install grub, which results in an unbootable system. Legacy installations, for me at least, have always worked.

---

### Post by oldfred on 2018-12-18
UEFI & Windows BIOS boot do not mix on one drive.

And Windows in BIOS mode must have its boot flag on its primary NTFS partition with boot files (your sda1). But UEFI requires boot flag/ESP flag on the FAT32 partition that has UEFI boot files. 
UEFI normally uses gpt partitioning and Windows only boots in UEFI mode from gpt. And Windows only boots in BIOS boot mode from MBR(msdos)

Since your system is UEFI, you must have manually reinstalled Windows in BIOS boot mode. Why? 

Windows 10 and BIOS boot mode are not dual boot friendly on one drive.
Windows has its fast boot setting which sets hibernation flag. And grub will not boot a hibernated Windows. And Windows will turn it back on with some updates. You then have to temporarily reinstall a Windows boot loader (boot flag on sda1) and fix Windows. Then restore grub so you can boot Ubuntu. 

Best to always have current version repair disks for all installs. Or Windows repair/recovery flash drive and Ubuntu live installer.

To oldrocker99's point, many have installed to UEFI systems, but some vendors make it difficult. And grub has not always correctly installed in UEFI mode. But often related to issues with ESP partition, corruption, locked(vendor), or missing from first drive (not install drive, if installing to second drive).

---

### Post by wrathod on 2018-12-19
I tried switching on the legacy boot option in bios, and it gives the same screen "No boot device found".
Interestingly the legacy boot option is automatically reverted back to switched off state.

---

### Post by oldfred on 2018-12-19
If you want to boot Windows again which is BIOS/MBR, you have to move boot flag back to sda1 and install a Windows type boot loader to MBR.

Then make sure Windows fast start up is off, and do a total reinstall of grub from Boot-Repair's advanced options when you have booted Ubuntu live installed in BIOS boot mode (purple screen, not grub menu on boot of live installer).

---

