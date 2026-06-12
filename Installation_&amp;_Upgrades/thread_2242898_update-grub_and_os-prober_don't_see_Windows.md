---
title: "update-grub and os-prober don't see Windows"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by lolzlolz2 on 2014-09-04
I haven't used Ubuntu in a longtime. I decided to install it again and wanted to use GRUB as my bootloader. I installed it with next to no problems and have it booting just fine with OS X; however, GRUB doesn't see Windows 7 installed on this machine. No problem, I thought...I'll just edit the grub config file. Well, things have changed since my last time with Ubuntu. I did some reading and discovered os-prober isn't seeing windows.

I've attached the relevant results of the bootinfoscript:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 40.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi /efi/ubuntu/MokManager.efi 
                       /efi/ubuntu/shimx64.efi

sda2: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe
```

Why bootinfoscript clearly sees Windows on sda5 but doesn't see OS X and os-prober sees OS X fine but doesn't see Windows is beyond me...
Help anyone? :)

---

### Post by lolzlolz2 on 2014-09-04
I've decided to resolve this by using rEFInd.
It appears I was approaching the problem from the wrong direction in that, while it may be possible to use GRUB to boot into Windows this is adding an extra step (EFI to GRUB then to OS choice), whereas if I use rEFInd it will simply be EFI to OS Choice.

I'm still curious as to why os-prober wasn't seeing Windows; but, this will at least make things workable.

---

### Post by yancek on 2014-09-04
That's a very incomplete output of the bootinfoscript, did you edit it?  It does clearly show windows code in the master boot record, not Grub.  It also shows that you seem to have Ubuntu installed as UEFI and sda1 is an EFI partition and the correct files are there.  I don't use EFI but from everything I've read mixing an mbr install (windows) with your EFI install of Ubuntu causes problems.  The bootinfoscript shows two Mac partitions hfs on sda2 and sda3.

---

