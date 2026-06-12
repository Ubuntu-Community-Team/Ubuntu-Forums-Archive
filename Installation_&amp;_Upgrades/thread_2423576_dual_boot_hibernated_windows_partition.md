---
title: "dual boot hibernated windows partition"
date: 2019-07-25
forum: Installation &amp; Upgrades
---

### Post by htondro on 2019-07-25
hello,
i can't repair my boot with boot repair tool,
log file: 
[https://pastebin.com/1qc9Uyef](https://pastebin.com/1qc9Uyef)

i hope to find a way to get access to my windows.

---

### Post by oldfred on 2019-07-25
While hibernation may be an issue with any Windows 10 install, it is more problematic with BIOS/MBR installs.
With BIOS, you have to boot from MBR and you can only have one boot loader in MBR. You still have Windows boot loader in MBR, so can from UEFI/BIOS directly boot Windows.

But you then also installed Ubuntu in UEFI boot mode. So you must have newer hardware and installed Windows yourself in the now very old BIOS/MBR configuration. Windows only boots in BIOS mode from MBR drives, but Ubuntu will (and maybe should not) let you install Ubuntu in UEFI boot mode to an old MBR drive. UEFI highly suggests that gpt be used and Windows only boots in UEFI mode from gpt.

You cannot dual boot Windows in BIOS and Ubuntu in UEFI from one drive. Windows requires boot flag on primary NTFS partition with boot files, your sda1.
But UEFI requires boot flag on the ESP, so UEFI knows which partition has UEFI based boot files. You cannot have two boot flagged partitions on one drive.

Move boot flag back to sda1 and Windows should boot in BIOS boot mode from your UEFI boot menu. You may have to turn on/off UEFI/BIOS boot settings in UEFI. BIOS mode may be called legacy or CSM.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

First make sure you have good backups of both Windows & Ubuntu.

You can either re-install Windows in UEFI boot mode, or convert Ubuntu to the 35 year old BIOS/MBR configuration.
Its just with Windows 8 or 10 they are not as friendly with BIOS mode for dual boot. Windows may turn fast start up with updates which you may not even see. Then grub will not boot Windows & you have to temporarily install a Windows boot loader, fix Windows and then restore grub to MBR.

With UEFI, you can always directly boot Windows from UEFI boot menu, if grub does not boot it. Unless you have major unrelated Windows issues. 
But should always have a Windows repair disk or installer with Windows repair console.

If you really want BIOS, boot Ubuntu in BIOS mode & add Boot-Repair. Then use it to install grub to MBR to dual boot. But be sure fast start up is off in Windows first.

Both Windows & Ubuntu install & run repairs in the boot mode you use to boot install or repair media. So always use UEFI or always use BIOS to boot flash drives and installed systems.

---

