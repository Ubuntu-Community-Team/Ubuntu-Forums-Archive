---
title: "Boot-Repair seems to succeed but still boot into Windows 10"
date: 2016-07-25
forum: MINT
---

### Post by hugh-ranalli on 2016-07-25
I applied some Windows 10 updates last week (I only use the Windows partition when necessary). Today I discovered the laptop would only boot directly to Windows.

1. I ran boot-repair and it asked me to disable SecureBoot and try again;
2. I disabled SecureBoot and ran boot-repair again - no success;
3. I tried the Boot Repair disk instead of the Live CD - no success 
4. I ran "bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi" as suggested and confirmed the setting with Visual BCDEdit - same result: system boots directly into Windows

Both Windows and Linux were installed using EFI and have been working.

Everything seems to have succeeded but without any change. My boot info summary is here: [http://paste.ubuntu.com/20878949/](http://paste.ubuntu.com/20878949/)

(And yes, this is Linux Mint, not stock Ubuntu, but the forums here seem much more active and as I use this for work, I need to find a solution).

Any assistance is appreciated. I've looked through the summary but nothing obvious jumps out...

Thanks!

---

### Post by SuperFreak on 2016-07-25
Boot Repair report suggests booting to different partition
> You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi


I don't know if it will work but you could try booting to Sdb in BIOS or if BIOS allows as in my PC there is a selection for Ubuntu under boot order options in UEFI (are you using UEFI or BIOS?)

EDIT:Looks like your using UEFI

---

### Post by ubfan1 on 2016-07-25
Forget legacy boot, you're UEFI.  Your order seems to have ubuntu first (0002), OK. The boot flag is on the EFI partition, OK. Nothing obviously wrong.  One thing to check, the /EFI/Boot/ directory -- the bootx64.efi should be a copy of shimx64.efi (check the size) and a copy of grubx64.efi should be present also in that directory.  This is a fallback, which might actually be tried after an initial failure.  Can you select ubuntu from the EFI boot menu (some function key at power-up)?

---

### Post by hugh-ranalli on 2016-07-25
> **SuperFreak said:**
> Boot Repair report suggests booting to different partition


I don't know if it will work but you could try booting to Sdb in BIOS or if BIOS allows as in my PC there is a selection for Ubuntu under boot order options in UEFI (are you using UEFI or BIOS?)

EDIT:Looks like your using UEFI

Unfortunately the BIOS does not have an option to manipulate boot order. So I tried the recommended bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi which had no effect.

And yes, this an EFI/UEFI system (I've been assuming they refer to the same thing). The reference to sdb is the USB stick I used to boot the Boot Repair Disk. The laptop has only one hard drive.

---

### Post by hugh-ranalli on 2016-07-25
> **ubfan1 said:**
> Forget legacy boot, you're UEFI.  Your order seems to have ubuntu first (0002), OK. The boot flag is on the EFI partition, OK. Nothing obviously wrong.  One thing to check, the /EFI/Boot/ directory -- the bootx64.efi should be a copy of shimx64.efi (check the size) and a copy of grubx64.efi should be present also in that directory.  This is a fallback, which might actually be tried after an initial failure.  Can you select ubuntu from the EFI boot menu (some function key at power-up)?

Thanks! Unfortunately, I've searched HP support and the BIOS only seems to allow setting the boot device, not the EFI image.

/boot/EFI contains the following directories and no files:[INDENT]
Boot
HP
Microsoft
ubuntu
[/INDENT]

The ubuntu directory contains the following files (all modified today):
[INDENT]
grub.cfg
grubx64.efi - 958,328 bytes
MokManager.efi - 1,271,672 bytes
shimx64.efi - 1,289,424 bytes
[/INDENT]

There is no bootx64.efi. Should I create a copy of shimx64.efi using that name in the ubuntu directory?
[INDENT]

[/INDENT]

---

### Post by ubfan1 on 2016-07-25
Look in the Boot directory (usually seen at /boot/efi/EFI/Boot).  The ...bkp file was the original one that boot-repair renamed (probably the Windows boot manager).  The bootx64.efi boot-repair created is either a copy of grubx64.efi or shimx64.efi (check the size against the originals).  If bootx64.efi is the same size as grubx64.efi, it should boot with secure-boot disabled, but if it a copy of shimx64.efi, it should boot either way --However, shimx64.efi requires that grubx64.efi be in the same directory, and I didn't see a grubx64.efi from what you posted.  The bootx64.efi only runs from .../Boot, so don't bother putting one in the ubuntu directory.  The grub.cfg file needs to be in the ubuntu directory.  grubx64.efi will find it there from wherever it's run.

---

### Post by ajgreeny on 2016-07-25
HP make life difficult for Linux users as their UEFI is not following the supposedly agreed configuration and only allows a system to boot to a Windows.efi

See post 6 of [https://ubuntuforums.org/showthread.php?t=2227889](https://ubuntuforums.org/showthread.php?t=2227889) for some info and possible workarounds for this.

---

### Post by oldfred on 2016-07-25
Moved to the Mint part of forum.

Latest versions of Boot-Repair will copy shimx64.efi to /EFI/Boot/bootx64.efi and backup current bootx64.efi which probably is really just a copy of Windows boot .efi file.             'Use the standard EFI file' in advanced options. 

 [URL="https://help.ubuntu.com/community/Boot-Repair"]https://help.ubuntu.com/community/Boot-Repair

      [/URL]
 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair](https://askubuntu.com/questions/597052/can-not-boot-anymore-after-a-boot-repair) 
    
But Boot-Repair sees all the hp .efi boot files in the ESP - efi system partition and creates a 25_custom grub to add all those as boot options. Most do not need nor want them. You can back up 25_custom and edit 25_custom at will, it is not part of standard grub.
      
 bootx64.efi Also edit of 25_custom
[http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705](http://askubuntu.com/questions/778663/what-is-the-difference-between-windows-uefi-bootmgfw-efi-and-windows-uefi-bkpboo/778705#778705)
# Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by yancek on 2016-07-25
>  So I tried the recommended bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi which had no effect.

Did you select to "run as administrator" from the windows powershell?  If not, it won't do anything and I don't know that there will be any error message.

---

### Post by hugh-ranalli on 2016-07-25
> **ajgreeny said:**
> HP make life difficult for Linux users as their UEFI is not following the supposedly agreed configuration and only allows a system to boot to a Windows.efi

See post 6 of [https://ubuntuforums.org/showthread.php?t=2227889](https://ubuntuforums.org/showthread.php?t=2227889) for some info and possible workarounds for this.

Difficult is an understatement!

I tried many of the recommended solutions. I finally discovered that F9 would let me select Ubuntu to boot.

What finally did the trick was:
[LIST]
[*]Re-enabling SecureBoot
[*]Running Boot-Repair with:
[LIST]
[*] Secure Boot checked
[*]Use Standard EFI file
[*]Backup and Rename EFI files
[/LIST]
[/LIST]

I had tried the backup and rename several times, with no effect (and the same running sudo efibootmgr -o). So either SecureBoot and/or Use Standard EFI file seems to have been what made the difference.

Thank you so much for the help, everyone!

---

