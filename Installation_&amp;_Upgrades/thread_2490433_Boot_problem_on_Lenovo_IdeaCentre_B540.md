---
title: "Boot problem on Lenovo IdeaCentre B540"
date: 2023-09-04
forum: Installation &amp; Upgrades
---

### Post by Ptitphysik on 2023-09-04
Hello, 
I just installed Ubuntu 23.04 on Lenovo Ideacentre B540.

In Bios : UEFI Only, Quick Boot Disabled. 

Install OK but at boot :
Error 1962: No operating system found. Press any key to repeat boot sequence.

I made a Boot report on [https://pastebin.ubuntu.com/p/D8RCCbGxTZ/](https://pastebin.ubuntu.com/p/D8RCCbGxTZ/)

Thx in advance

Arnaud

---

### Post by tea for one on 2023-09-04
> **Ptitphysik said:**
> In Bios : UEFI Only, SecureBoot Disabled. 
Install OK but at boot :
Error 1962: No operating system found. Press any key to repeat boot sequence.
In your UEFI settings, do you have other Security options e.g.

Disable TPM (Trusted Platform Module)
Disable PTT (Platform Trust Technology)
Disable FTPM (Firmware Trusted Platform Module)
Disable TPT (Trust Platform Technology)
Disable Device Guard 
Disable OS Optimised Defaults

---

### Post by Ptitphysik on 2023-09-04
None.
Only Quick Boot (Disabled).
It's a 2014 model.

---

### Post by tea for one on 2023-09-04
> **Ptitphysik said:**
> Install OK but at boot :
Error 1962: No operating system found. Press any key to repeat boot sequence.

Error 1962 seems to be concerned with UEFI settings.
I suggest that you remove all peripheral devices (if any are attached) and investigate all the UEFI settings.
For example, the error could be Boot Order if another Disk was attached.

---

### Post by yancek on 2023-09-04
Line 83 and 88 show your /etc/fstab file has a bad efi and has fstab without boot.  Did you modify that file?  I'm using 20.04 and my lines in the fstab file begin with UUID= for both entries.  I don't know if 23.04 made a change to this file or if that is not correct.

---

### Post by oldfred on 2023-09-04
The fstab disk by UUID is ok. I have not seen it before, my old lunar install used the UUID=.

Another Lenovo with 1962 error.
[https://ubuntuforums.org/showthread.php?t=2243715](https://ubuntuforums.org/showthread.php?t=2243715)
Not sure if solution was adding the Microsoft folder & files in ESP or just creating a fallback boot entry.
The fallback entry is like booting the external drive, UEFI uses /EFI/Boot/bootx64.efi which you do not have.
Copy grubx64.efi from /EFI/ubuntu to /EFI/Boot and rename to bootx64.efi. 

Running Boot-Repair may do that as it does replace a Windows version of bootx64.efi with a grub version. Not sure if it would add file also? I might try running Boot-Repair first and see if files updated in ESP.

You may need new UEFI boot entries. Either once booting fallback or one booting a Windows description one, but really boots grub.
Windows description:

    sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\grubx64.efi"

You can add your hard drive entry to boot fallback file after copying grubx64.efi to /EFI/Boot:
sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sdX -p Y
sdX is drive, Y is efi partition

Did you install restricted extras during install, so nVidia driver installed? You may need to boot recovery mode or second line in grub menu that has nomodeset as default parameter. If only Ubuntu, you have to press escape just after vendor logo & before grub menu would normally appear to get grub menu.

---

### Post by Ptitphysik on 2023-09-05
Txh oldfred.

In BIOS : UEFI Only
Install Ubuntu in safe fraphics
type :      sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\grubx64.efi"
type : sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sdX -p Y   (with X=a and Y=2 at home)
reboot.

Function well.

Thx !

---

### Post by oldfred on 2023-09-05
The "Windows" UEFI entry should have worked as it uses all defaults or sda1.
Your ESP is sda1, so for second entry you need 
-d /dev/sdX -p Y   (with X=a and Y=1)
or
-d /dev/sda -p 1
See also this for details of commands.
man efibootmgr

To confirm entries:
sudo efibootmgr -v

---

