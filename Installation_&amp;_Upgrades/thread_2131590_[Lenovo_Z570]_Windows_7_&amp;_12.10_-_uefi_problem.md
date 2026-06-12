---
title: "[Lenovo Z570] Windows 7 &amp; 12.10 - uefi problem (no grub, only windows starts)"
date: 2013-04-02
forum: Installation &amp; Upgrades
---

### Post by enigma20 on 2013-04-02
Hi,

I have notebook Lenovo Z570. I bought new hard drive and now I want to have dual boot - Windows 7 and Ubuntu 12.10 (64bit).
I installed both OS, but all the time only Windows 7 boot, I don't have GRUB. So thats what I did:

1. I installed Windows 7 64bit
2. After boot from Ubuntu LiveCD, installer didn't saw installed windows, so I used gdisk to something with that
3. Then I created ext4 partition and swap (on extended), and installed Ububtu
4. After reboot I used Boot-repair (with different settings) but all the time only windows boot

From boot-repair I got this message:
> Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/5669924/](http://paste.ubuntu.com/5669924/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file!

Why this doesn't work out of the box? I don't know what to do with this efi file. Coul;d anybody help?

---

### Post by oldfred on 2013-04-02
Your first install was a BIOS install? But you installed grub to the efi partition, which put it into the FAT32 partitions boot sector. Not sure if that has a backup like NTFS or not. I know with NTFS it cannot have grub in the PBR - partition boot sector. Not sure about the FAT32, but you probably should try to repair it with testdisk.

Then it looks like Boot-Repair converted to UEFI install, by uninstalling grub-pc (BIOS) and installing grub-efi(UEFI).
But to change the default boot, you have to go into the UEFI menu and change the boot order.

>  sda1: __________________________________________________________________________

       File system:       vfat
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda1 and looks at sector 939448992 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/grubx64.efi 
                       /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi

  >  BootOrder: 0004,0002,0003,0005,0006,0007
Boot0000  Setup
Boot0001  Boot Menu
Boot0002* USB FDD:
Boot0003* ATA HDD: WDC WD5000BPVT-22HXZT3
Boot0004* ATAPI CD: HL-DT-STDVDRAM GT33N
Boot0005* USB HDD:
Boot0006* USB CD:
Boot0007* PCI LAN: Realtek PXE B03 D00
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0008,0004,0002,0003,0005,0006,0007
Boot0000  Setup
Boot0001  Boot Menu
Boot0002* USB FDD:
Boot0003* ATA HDD: WDC WD5000BPVT-22HXZT3
Boot0004* ATAPI CD: HL-DT-STDVDRAM GT33N
Boot0005* USB HDD:
Boot0006* USB CD:
Boot0007* PCI LAN: Realtek PXE B03 D00
Boot0008* [COLOR=#ff0000]ubuntu[/COLOR]



Above is extracted from what UEFI writes, so you have an ubuntu entry somewhere in your UEFI/BIOS settings.

---

### Post by enigma20 on 2013-04-02
**@oldfred** - I'm not sure what you mean by BIOS install but first was with Windows 7 so with EFI partition.

> Above is extracted from what UEFI writes, so you have an ubuntu entry somewhere in your UEFI/BIOS settings. 
In BIOS in Boot I see only CD, HDD and USB devices. Nothing with ubuntu.

I'm angry because of that. Why I cannot just install Windows 7, then Ubuntu as it was in the past?
I can give one more try but it's hard to find proper way of making dual boot.
Solution described here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) (1st paragraph) doesn't work for me.

---

### Post by oldfred on 2013-04-02
I only have BIOS, but every motherboard has two selections. One is device like hard drive, DVD, network etc, and the other is which hard drive. With UEFI then it is which entry in the efi partition. That may be a sub-menu or even on a different page where you specify boot order.
You also should from a reboot be able to get to a one time boot key that will also show those same entries, but just as a one time change. That should also show Ubuntu.

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

Other Lenovo's - probably similar UEFI.
      
 Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See last post on removing battery to get it to totally reset to boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
 lenovo u310  - install to SSD
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

---

