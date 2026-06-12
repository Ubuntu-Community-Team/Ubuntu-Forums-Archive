---
title: "Boot issues after installing Ubuntu 23.04 on Windows 10 Machine"
date: 2023-10-16
forum: Installation &amp; Upgrades
---

### Post by joetruitt on 2023-10-16
Boot issues after installing Ubuntu 23.04 on Windows 10 Machine

it only boots to Ubuntu, i found the Boot Repair tool and ran the diagnostic tool and it shows the following 
```

[COLOR=#666666]==============================[/COLOR] Boot Info [COLOR=#B8860B]Summary[/COLOR] [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Windows [COLOR=#666666]7[/COLOR]/8/10/11/2012 is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows [COLOR=#666666]8[/COLOR]/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr

nvme0n1p2: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows [COLOR=#666666]8[/COLOR]/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows [COLOR=#666666]10[/COLOR] or [COLOR=#666666]11[/COLOR]
    Boot files:        /Windows/System32/winload.exe

nvme0n1p3: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu [COLOR=#666666]23[/COLOR].04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

nvme0n1p4: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg


[COLOR=#666666]================================[/COLOR] [COLOR=#666666]2[/COLOR] OS [COLOR=#B8860B]detected[/COLOR] [COLOR=#666666]=================================[/COLOR]

OS#1:   Ubuntu [COLOR=#666666]23[/COLOR].04 on nvme0n1p3
OS#2:   Windows [COLOR=#666666]10[/COLOR] or [COLOR=#666666]11[/COLOR] on [COLOR=#B8860B]nvme0n1p2[/COLOR]
[COLOR=#B8860B]Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge [COLOR=#666666]([/COLOR]in order to remove grub-efi[COLOR=#666666])[/COLOR] and reinstall the grub2 of
nvme0n1p3 into the MBR of nvme0n1.
Grub-efi would not be selected by default because legacy Windows detected.
Additional repair would be performed: unhide-bootmenu-10s win-legacy-basic-fix

Confirmation request before suggested repair: __________________________________

LegacyWindows detected. The boot of your PC is in EFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.
Are you sure you want to [COLOR=#AA22FF]**continue**[/COLOR] anyway?

Final advice in [COLOR=#AA22FF]**case**[/COLOR] of suggested repair: ______________________________________

The boot of your PC is in UEFI mode. You may want to retry after changing it to BIOS-compatibility/CSM/Legacy mode.[/COLOR]
it looks like something happened to the windows boot, i was able to change the boot order in Bios, but windows complained that boot needed to be repaired. 
```

thank you

---

### Post by joetruitt on 2023-10-16
i did not see grub.

---

### Post by yancek on 2023-10-17
Is windows 10 an upgrade from 7?  In any case, if you look at the top of the boot repair output, it shows windows installed in the MBR of the device.  That makes it a Legacy install and you would need to configure the windows boot loader to boot Ubuntu.  A simpler solution would be to install the Ubuntu Grub bootloader to the MBR and use it to boot windows.  Windows bootloader requires either a convoluted process to boot Linux or third party software.  That being said, if you look at the output under nvme0n1p4:, it shows EFI files for Ubuntu.  You need to install both in Legacy mode or both in UEFI mode if they are on the same drive.  Probably the simplest solution would be to reboot the Ubuntu installer and make certain you boot in Legacy mode and NOT in UEFI mode and reinstall Ubuntu.  You need to check the options in the BIOS of whatever computer type you are using to enable Legacy mode, probably good idea to turn off Secure Boot also.

---

### Post by tea for one on 2023-10-17
> The boot of your PC is in UEFI mode
Your PC boots Ubuntu in UEFI mode, therefore, in your position, I would seriously consider a more drastic (yet modern) approach.

Back up your Windows and Ubuntu data.
Install both systems in UEFI mode with GPT

There are numerous internet sites explaining the benefits of UEFI and GPT.
Take a bit of time and conduct some research and see if it is suitable for you.

---

