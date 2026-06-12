---
title: "Grub does not detect windows 10"
date: 2019-01-28
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2019-01-28
I got a brand new Dell M6800 - It has an installed windows 10 system - I got an SSD disk and installed Ubuntu 18.04 on it. I had to set the boot in Legacy mode in the BIOS otherwise the SSD wouldn't be seen. After completion, the grub boot window does not show the windows 10 system. Running update-grub on the 18.04 running system didn't help. On the other hand, in order to boot windows I have to change the boot mode in the BIOS from Legacy to UEFI. Following an advice from another forum I edited the /etc/grub.d/40_custom as follows:
```
#!/bin/shexec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Windows 10" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set e2dce404-ec40-4a20-b28c-adea47b3c721
    chainloader + 1
}
```
where the blkid is of course that of the windows disk. This didn't work either.

Any ideas?

---

### Post by oldfred on 2019-01-28
UEFI & BIOS are not compatible.
And then you cannot use grub to boot another install that is in a different boot mode.
If you want to dual boot using grub, you must install Ubuntu in UEFI mode.

Many Dell systems have some updates & settings that you need to do.
Update Dell's UEFI and SSD's firmware.
Change Dell UEFI settings from RAID or Intel SRT to AHCI, but install AHCI driver into Windows first.
If it has nVidia, you will need nomodeset to boot installer & first boot or until you install the nVidia driver from Ubuntu repository.
Best to turn off Windows drive in UEFI or physically disconnect it, so entire install is on SSD. Otherwise you need to partition in advance and include an ESP as first partition.  I prefer to partition in advance anyway.

Dell UEFI is very similar across many models.

       Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en) 
            Dell update UEFI/BIOS from Linux
[https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en](https://www.dell.com/support/article/us/en/19/sln171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=en) 
            XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/) 
            Dell XPS 8920 desktop GTX 1060, needed UEFI/BIOS update
[https://ubuntuforums.org/showthread.php?t=2370434](https://ubuntuforums.org/showthread.php?t=2370434)
Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929)

---

### Post by danielsender on 2019-01-29
> **oldfred said:**
> UEFI & BIOS are not compatible.
And then you cannot use grub to boot another install that is in a different boot mode.
If you want to dual boot using grub, you must install Ubuntu in UEFI mode.



Since I already did the install of Ubuntu in Legacy mode, is it possible to modify it so it will be UEFI boot? I wouldn't like to do it from scratch.

Thanks

---

### Post by oldfred on 2019-01-29
Not easily.
Normally default install will be MBR and just / (root) partition.
UEFI wants ESP & / on gpt partitioned drive.

Just reinstall and restore from your backups. (you do have backups?)
Backup procedure should let you reinstall & restore & be back to normal very quickly.
My install to SSD takes 10 min or less, restoring apps list & relinking data and some manual changes takes a total of an hour for a new install.

You can convert drive to gpt, add ESP - efi system partition (recommended to be first, but can be anywhere on smaller drives). Then do a total uninstall/reinstall of grub. You want to uninstall grub-pc (BIOS boot) and install grub-efi-amd64.efi (UEFI boot). May be easier with Boot-Repair.

See link in my signature for more info on UEFI.

---

### Post by danielsender on 2019-01-29
OK - I'm rolling up my sleeves.

Thanks

---

