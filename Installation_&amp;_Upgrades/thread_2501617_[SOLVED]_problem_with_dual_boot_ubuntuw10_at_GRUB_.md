---
title: "[SOLVED] problem with dual boot ubuntu/w10 at GRUB: cannot load image"
date: 2024-10-15
forum: Installation &amp; Upgrades
---

### Post by pfelelep on 2024-10-15
*[EDIT: problem has been solved, It was due to an issue in GRUB2 being non-compatible with non-NX shim which includes Windows 10, to fix it:*
*[COLOR=#0C0D0E][FONT=-apple-system]Follow the instructions at [/FONT][/COLOR][https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)[COLOR=#0C0D0E][FONT=-apple-system] then in a console [/FONT][/COLOR]sudo apt install -t oracular-proposed grub-common grub-efi-amd64-bin grub-efi-amd64-signed grub-efi-amd64-unsigned grub-pc grub-pc-bin grub2-common]*


first of all, I would like to thank you as I am a new comer on the ubuntu forums


I have an issue at the moment with my dual boot ubuntu/w10. I am not sure if it's because of the upgrade, but just in case, if I may describe the problem? 
I updated to the last ubuntu version (Ubuntu 24.10) and since, I cannot load windows from grub. when I choose windows, it shows an 
*"error*
*cannot load image"*
black screen.


I have tried using boot.repair and here is the report:
[https://paste.ubuntu.com/p/7k6GxdSYC3/](https://paste.ubuntu.com/p/7k6GxdSYC3/)


I have tried rescue-ing from a win installation usb media using terminal (and, yes, I deleted the hibernation file), but I cannot locate the issue.


I have searched the forum for a similar threat, but this cannot  load image don't seems to be.

If someone pass by and could advice me?

Thank you.

---

### Post by ubfan1 on 2024-10-15
What model machine?  A pre-2012 UEFI without secure boot (so maybe delivered with Win7 in legacy), but both disks are gpt (implying UEFI for Windows). Confusing to me is sda has the legacy MBR boot, but sdb has the BIOS boot partition -- I guess it could still be booting in legacy, hence Windows wont run. What machine settings do you have for legacy (csm) vs UEFI?

---

### Post by pfelelep on 2024-10-15
Hello, thank you for helping me :)

it's a Dell Inspiron 7559 bought in 2016, I disabled the secure boot but it's supposed to be UEFI. I will double check in the bios and confirm.

---

### Post by oldfred on 2024-10-15
It looks like both are UEFI as Windows is only UEFI from gpt and you also have mount of esp in fstab.
And ESP shows both Microsoft & Ubuntu folders for UEFI boot.

Probably not related to Windows issues, but should be resolved.
> GPT PMBR size mismatch (1953525167 != 3907029167) will be corrected by write.
Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html) & 


Can you directly boot Windows from UEFI boot menu?
Grub only boots working Windows, but that also means Windows fast startup, hibernation must be off. If bitlocker it must be off. And NTFS must not need chkdsk. If you can boot Windows check those settings. Windows is known to turn fast startup back on with updates, so you may have to redo turning it off.

---

### Post by pfelelep on 2024-10-15
@[COLOR=#000000]ubfan1
[/COLOR]I confirm it's UEFI (but with legacy oprom? (pict 3) would that be the problem? should I disable the legacy option rom? (in pict2))
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294366&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294365&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294363&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294364&stc=1[/IMG]



[COLOR=#000000]
[/COLOR]
[COLOR=#000000]@oldfred:
no, I can't directly boot Windows from UEFI boot menu, the windows boot manager (in pict 3) bring me back to Grub (pict 4)

I can't check the fast startup from here, but I deleted the hibernation file before.
How can I use gdisk? sorry I am confused.

[/COLOR]

---

### Post by yancek on 2024-10-15
> should I disable the legacy option rom? (in pict2)) 

I would try that and reboot to test.  Make sure when you are making changes to keep detailed notes of exactly what you do an the results.

Your UEFI information in boot repair beginning on line 206 shows an entry for Ubuntu and for the Hard Drive but does not show the standard entry:  Windows Boot Manager
but it does show in the BIOS setting and the Grub menu which seems a bit odd to me but probably not related.

What did you do with the windows repair usb?  Did you run chkdsk with options and if so, what options did you use?i

---

### Post by oldfred on 2024-10-15
You show a Windows boot loader in MBR, but Windows in UEFI will not boot from that.
And you do not have a Windows entry in UEFI.

This should create a new entry, if ESP is sda1, uses defaults:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

see also
man efibootmgr

---

### Post by pfelelep on 2024-10-16
@oldfred:
> [COLOR=#000000]This should create a new entry, if ESP is sda1, uses defaults:[/COLOR]
[COLOR=#000000]sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"[/COLOR]
Bingo! I rebooted, and windows loaded automatically.

Now, to bring back the dual  boot... should I sudo update-grub  or use bootrepair?
I wonder what made the UEFI windows entry disappear?

---

### Post by pfelelep on 2024-10-16
now, as I rebooted with the boot option (f12 key), I see that there is no more ubuntu option.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294370&stc=1[/IMG]

and choosing the 4th UEFI option (the "2nd" windows boot manager), brings me back to the GRUB dual-boot.

BUT


choosing from there, the windows boot manager (on /dev/sda1), gives me the "old" error cannot load image I was running into from the beginning... :/
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294369&stc=1[/IMG]

---

### Post by pfelelep on 2024-10-16
@yancek
> [COLOR=#000000]What did you do with the windows repair usb? Did you run chkdsk with options and if so, what options did you use?i[/COLOR]

[URL="https://www.lifewire.com/how-to-rebuild-the-bcd-in-windows-2624508"]https://www.lifewire.com/how-to-rebuild-the-bcd-in-windows-2624508
[/URL]I was trying to rebuild the BCD

the chkdsk command returned no error.

---

### Post by oldfred on 2024-10-16
One old fix for some systems that only booted "Windows Boot Entry" was to create a Windows entry that booted Ubuntu.
It only partially worked as next Windows update fixed entry and booted Windows. 

Post this from live installer:
sudo efibootmgr -v #if from 24.04 do not use -v as it then includes too much data.

If issues is a Windows issue with BCD, no idea how to fix that.

---

### Post by pfelelep on 2024-10-16
> [COLOR=#000000]Post this from live installer:[/COLOR]
[COLOR=#000000]sudo efibootmgr -v #if from 24.04 do not use -v as it then includes too much data.[/COLOR]

pfelelep@pfelelep-Inspiron-7559:~$ efibootmgr No BootOrder is set; firmware will attempt recovery
Boot0003* Hard Drive    BBS(Floppy,,0x0)0000474f00004e4f97000000010000006f00480061007200640020004400720069007600650000000501090001000000007fff040002010c00d041030a0000000001010600001703120a000000ffff00007fff040001043e00ef47642dc93ba041ac194d51d01b4ce6340053003400310042004e004d00300030003400340032003100350020005400200020002000200000007fff04000000424f



here is the boot info summary from boot repair:

```

============================== Boot Info Summary ===============================


 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/Manjaro/grubx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/SecureBootRecovery.efi /bootmgr


sda2: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /bootmgr /Windows/System32/winload.exe


sda4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 1618642944. But according to the info from 
                       fdisk, sda4 starts at sector 504604672.
    Operating System:  
    Boot files:        


sda5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 1927069696. But according to the info from 
                       fdisk, sda5 starts at sector 924035072.
    Operating System:  
    Boot files:        


sda6: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 1928742912. But according to the info from 
                       fdisk, sda6 starts at sector 925708288.
    Operating System:  
    Boot files:        


sda7: __________________________________________________________________________


    File system:       btrfs
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb2: __________________________________________________________________________


    File system:       BIOS Boot partition
    Boot sector type:  Unknown
    Boot sector info: 


sdb3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        




================================ 2 OS detected =================================


OS#1 (linux):   The OS now in use - Ubuntu 24.10 on sda7
OS#2 (windows):   Windows 10 or 11 on sda3


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: GM107M [GeForce GTX 960M] HD Graphics 530 from NVIDIA Corporation Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.11.0-8-generic root=UUID=d9350585-506b-4b2a-b402-eba8497ffdaf ro quiet splash crashkernel=2G-4G:320M,4G-32G:512M,32G-64G:1024M,64G-128G:2048M,128G-:4096M vt.handoff=7
df -Th / : /dev/sda7      btrfs   40G   22G   17G  57% /


===================================== UEFI =====================================


BIOS/UEFI firmware: 1.3.1(1.3) from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
No EFI in dmseg.
SecureBoot disabled - This system doesn't support Secure Boot.
No BootOrder is set; firmware will attempt recovery
Boot0003* Hard Drive    BBS(Floppy,,0x0)0000474f00004e4f97000000010000006f00480061007200640020004400720069007600650000000501090001000000007fff040002010c00d041030a0000000001010600001703120a000000ffff00007fff040001043e00ef47642dc93ba041ac194d51d01b4ce6340053003400310042004e004d00300030003400340032003100350020005400200020002000200000007fff04000000424f




============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sdb    : is-GPT,    hasBIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda7    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sdb4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB


Partitions info (2/3): _________________________________________________________


sda7    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, btrfs
sdb4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sdb3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sda4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sda5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot, ntfs
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot, ntfs
sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    notwinboot, vfat
sda6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot, ntfs


Partitions info (3/3): _________________________________________________________


sda7    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdb4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sda4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda6    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 453.23 GiB, 486650431488 bytes, 950489124 sectors
Disk identifier: 8B5DCA2D-7E5D-4004-ADE0-F471AC7C06E6
         Start       End   Sectors   Size Type
sda1       2048   1026047   1024000   500M EFI System
sda2    1026048   1288191    262144   128M Microsoft reserved
sda3    1288192 422440732 421152541 200.8G Microsoft basic data
sda4  504604672 828987391 324382720 154.7G Microsoft basic data
sda5  924035072 925708287   1673216   817M Windows recovery environment
sda6  925708288 950489087  24780800  11.8G Windows recovery environment
sda7  422440734 504604671  82163938  39.2G Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: C84F2E0C-0CF3-4DB4-995D-BD65A63798A4
          Start        End    Sectors   Size Type
sdb1        2048 1797715967 1797713920 857.2G Microsoft basic data
sdb2  1797715968 1797718015       2048     1M BIOS boot
sdb3  1797718016 2883026943 1085308928 517.5G Microsoft basic data
sdb4  2883026944 3516325887  633298944   302G Microsoft basic data


parted -lm (filtered): _________________________________________________________


sda:487GB:scsi:512:512:gpt:ATA Samsung SSD 860:;
1:1049kB:525MB:524MB:fat32:EFI system partition:boot, esp;
2:525MB:660MB:134MB::Microsoft reserved partition:msftres;
3:660MB:216GB:216GB:ntfs:Basic data partition:msftdata;
7:216GB:258GB:42.1GB:btrfs:root:;
4:258GB:424GB:166GB:ntfs:Basic data partition:msftdata;
5:473GB:474GB:857MB:ntfs::hidden, diag;
6:474GB:487GB:12.7GB:ntfs::hidden, diag;
sdb:2000GB:scsi:512:512:gpt:ATA Samsung SSD 870:;
1:1049kB:920GB:920GB:ntfs:Basic data partition:msftdata;
2:920GB:920GB:1049kB:::bios_grub;
3:920GB:1476GB:556GB:ntfs:Basic data partition:msftdata;
4:1476GB:1800GB:324GB:ntfs:Basic data partition:msftdata;


Free space >10MiB: ______________________________________________________________


sda: 404779MiB:451189MiB:46410MiB
sdb: 1716956MiB:1907729MiB:190773MiB


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL             PARTLABEL
sda                                                                                                         
&#9500;&#9472;sda1 vfat     4887-94F5                            02efc03c-0d0c-43a9-966e-a6ad53c9edc5 ESP               EFI system partition
&#9500;&#9472;sda2                                               f1410272-14bb-4f7d-902e-00c6476614da                   Microsoft reserved partition
&#9500;&#9472;sda3 ntfs     CAB25579B2556B49                     f6803be0-038e-4009-b1b4-00e11a35631b OS                Basic data partition
&#9500;&#9472;sda4 ntfs     E6BA3670BA363CFD                     6a32a8f3-3407-4639-8ef8-23d8357c216d Vrac primary      Basic data partition
&#9500;&#9472;sda5 ntfs     0E029F42029F2DA9                     deca5c9e-e30b-4e86-bb82-db98815c1b35 WINRETOOLS        
&#9500;&#9472;sda6 ntfs     AEC4A02AC49FF2B7                     3e650648-465c-47f3-a779-7bf06125fb6d Image             
&#9492;&#9472;sda7 btrfs    d9350585-506b-4b2a-b402-eba8497ffdaf 2b15366a-c7a7-ef4a-bee8-6f65e8462058                   root
sdb                                                                                                         
&#9500;&#9472;sdb1 ntfs     0296F50996F4FDCB                     9d17a0a0-6488-4fb9-b86d-2538dbd4b36a Data              Basic data partition
&#9500;&#9472;sdb2                                               dd84a79c-1d3b-4e5e-a778-4eee6f623cba                   
&#9500;&#9472;sdb3 ntfs     FE0A058E0A05455D                     92cfda1c-bec8-433f-964b-0dc2796eb769 Games             Basic data partition
&#9492;&#9472;sdb4 ntfs     DE5ACB645ACB3853                     9a33b971-5eb6-40b9-b3f4-1479487d829d Save and Recovery Basic data partition


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/sda3               49.7G  75% /mnt/boot-sav/sda3
/dev/sda4               70.2G  55% /mnt/boot-sav/sda4
/dev/sda5              420.6M  49% /mnt/boot-sav/sda5
/dev/sda6               69.4M  99% /mnt/boot-sav/sda6
/dev/sda7               16.8G  56% /
/dev/sdb1              147.8G  83% /media/pfelelep/Data
/dev/sdb3              182.5G  65% /mnt/boot-sav/sdb3
/dev/sdb4                 42G  86% /mnt/boot-sav/sdb4
efivarfs                52.2K  78% /sys/firmware/efi/efivars


Mount options (filtered): ______________________________________________________


/dev/sda3              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda4              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda6              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda7              btrfs           rw,relatime,ssd,discard=async,space_cache=v2,subvolid=5,subvol=/
/dev/sdb1              ntfs3           rw,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8
/dev/sdb3              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb4              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096


===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid d9350585-506b-4b2a-b402-eba8497ffdaf root hd0,gpt7 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda7/boot/grub/grub.cfg (filtered) ======================


Ubuntu   d9350585-506b-4b2a-b402-eba8497ffdaf
Windows Boot Manager (on sda1)   osprober-efi-4887-94F5
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


========================== sda7/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during curtin installation
/dev/disk/by-uuid/d9350585-506b-4b2a-b402-eba8497ffdaf / btrfs defaults 0 1
# /boot/efi was on /dev/sda1 during curtin installation
UUID=4887-94F5  /boot/efi       vfat    defaults      0       1


======================= sda7/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


==================== sda7: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
 217.949484825 = 234.021477376  boot/grub/grub.cfg                             1
 207.728102684 = 223.046351872  boot/vmlinuz                                   1
 207.728102684 = 223.046351872  boot/vmlinuz-6.11.0-8-generic                  1
 207.453169823 = 222.751144960  boot/vmlinuz-6.8.0-45-generic                  1
 207.453169823 = 222.751144960  boot/vmlinuz.old                               1
 223.713049889 = 240.210058240  boot/initrd.img                                2
 223.713049889 = 240.210058240  boot/initrd.img-6.11.0-8-generic               2
 208.734850883 = 224.127339520  boot/initrd.img-6.8.0-41-generic               2
 223.657198906 = 240.150088704  boot/initrd.img-6.8.0-45-generic               2
 223.657198906 = 240.150088704  boot/initrd.img.old                            2


===================== sda7: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18133 Apr  4  2024 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4  2024 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4  2024 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4  2024 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4  2024 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4  2024 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5  2024 35_fwupd
-rwxr-xr-x 1 root root   214 Apr  4  2024 40_custom
-rwxr-xr-x 1 root root   215 Apr  4  2024 41_custom






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda7,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 24.10 entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)

```

I am really sorry for this mess, I am really grateful for your help. :(

---

### Post by oldfred on 2024-10-16
While you have an old BIOS boot of Windows in MBR, that would not be used with UEFI boot. But you must make sure UEFI settings are for UEFI.
Some older Dell systems needed legacy boot on, even when using UEFI. Even mentioned in man page on efibootmgr that some need legacy on.
Newer systems should have legacy/BIOS/CSM off.

Latest efibootmgr does not show the Windows entry?

Was there some reason for btrfs over normal default of ext4. I have only used ext4. Some more advanced users like some of the other Linux formats for advanced features, but best used by experienced Linux users. Needs some different settings in grub & installation of its repair tools.

You should be able to use Boot-Repair's advanced mode to select install & drive for boot files. Both systems share ESP on sda1. You show both /Microsoft & /ubuntu folders in ESP for booting.

Windows or Dell are usually pretty good about updating UEFI firmware. Do you have latest available from Dell? It may not be very new now, but if newer is available best to install it.
Compare to vendors support site
sudo dmidecode -s bios-version

With two drives, I prefer each drive have install if drives are similar or both HDD or both SSD. Both gpt with ESP - efi system partition, so either drive can boot without other drive.
But SSD is so much better then have both systems on SSD and data on HDD.

---

### Post by tea for one on 2024-10-16
> **pfelelep said:**
> pfelelep@pfelelep-Inspiron-7559:~$ efibootmgr No BootOrder is set; firmware will attempt recovery
Boot0003* Hard Drive    BBS(Floppy,,0x0)0000474f00004e4f97000000010000006f00480061007200640020004400720069007600650000000501090001000000007fff040002010c00d041030a0000000001010600001703120a000000ffff00007fff040001043e00ef47642dc93ba041ac194d51d01b4ce6340053003400310042004e004d00300030003400340032003100350020005400200020002000200000007fff04000000424f

Believe it or not, the message "No BootOrder is set; firmware will attempt recovery" is good news.
When you reboot, the UEFI firmware will populate the efibootmgr with entries.

What happens when you reboot?

---

### Post by pfelelep on 2024-10-17
> **oldfred said:**
> Was there some reason for btrfs over normal default of ext4. I have only used ext4. Some more advanced users like some of the other Linux formats for advanced features, but best used by experienced Linux users.

I was on Manjaro before, a (expert) friend of mine installed it for me, that might have been the reason.


> **oldfred said:**
> You should be able to use Boot-Repair's advanced mode to select install & drive for boot files. 

I am not sure to understand what you mean? I'll use bootrepair advanced mode, and select "repair windows boot files"?


> **oldfred said:**
> Windows or Dell are usually pretty good about updating UEFI firmware. Do you have latest available from Dell? It may not be very new now, but if newer is available best to install it.
Compare to vendors support site
Yes, I checked, I have the latest BIOS version 1.3.1

> **oldfred said:**
> With two drives, I prefer each drive have install if drives are similar or both HDD or both SSD. Both gpt with ESP - efi system partition, so either drive can boot without other drive.
But SSD is so much better then have both systems on SSD and data on HDD.

that's a good idea, I might consider that in the near future, thank you for the suggestion! :)

@**tea for one:**
thank you for the good news :)
I will attempt the boot repair now, I only created the boot info summary to share here (I am slow but I want to understand in the process, thank you everyone for your patience) O:)

---

### Post by pfelelep on 2024-10-17
Unfortunately, I am back on the very beginning: GRUB is installed but selecting windows boot manager on sda1 gives me the same "*error cannot load image*"

and selecting Ubuntu works: here am I, writing this message.


here is the boot repair log:
```
boot-repair-4ppa2081                                              [20241017_1453]

============================= Boot Repair Summary ==============================








Default settings: ______________________________________________________________


The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda7,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 24.10 entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)


User settings: _________________________________________________________________


GPT PMBR size mismatch (1953525167 != 3907029167) will be corrected by write.
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.11.0-8-generic
The settings chosen by the user will reinstall the grub-efi of
sda7,
using the following options:  sda1/boot/efi
Additional repair will be performed:  unhide-bootmenu-10s win-legacy-basic-fix use-standard-efi-file restore-efi-backups




rm /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/sda1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/sda1/efi/Boot/bootx64.efi
Quantity of real Windows: 1
Mount /dev/sda1 on /boot/efi


===================== Reinstall the grub-efi of /dev/sda7 ======================


grub-install --version
grub-install (GRUB) 2.12-5ubuntu5
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.11.0-8-generic
modprobe efivars


efibootmgr -v (filtered) before grub install
No BootOrder is set; firmware will attempt recovery
Boot0003* Hard Drive    BBS(Floppy,,0x0)0000474f00004e4f97000000010000006f00480061007200640020004400720069007600650000000501090001000000007fff040002010c00d041030a0000000001010600001703120a000000ffff00007fff040001043e00ef47642dc93ba041ac194d51d01b4ce6340053003400310042004e004d00300030003400340032003100350020005400200020002000200000007fff04000000424f


uname -r
6.11.0-8-generic


grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/sda1
mv /boot/efi/EFI/Boot/bootx64.efi /boot/efi/EFI/Boot/bkpbootx64.efi
cp /boot/efi/efi/ubuntu/grubx64.efi /boot/efi/EFI/Boot/bootx64.efi


grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
Installation finished. No error reported.


efibootmgr -v (filtered) after grub install
BootOrder: 0000
Boot0000* Ubuntu    HD(1,GPT,02efc03c-0d0c-43a9-966e-a6ad53c9edc5,0x800,0xfa000)/File(EFIubuntushimx64.efi)
Boot0003* Hard Drive    BBS(Floppy,,0x0)0000474f00004e4f97000000010000006f00480061007200640020004400720069007600650000000501090001000000007fff040002010c00d041030a0000000001010600001703120a000000ffff00007fff040001043e00ef47642dc93ba041ac194d51d01b4ce6340053003400310042004e004d00300030003400340032003100350020005400200020002000200000007fff04000000424f


update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/kdump-tools.cfg'
Found linux image: /boot/vmlinuz-6.11.0-8-generic
Found initrd image: /boot/initrd.img-6.11.0-8-generic
Found linux image: /boot/vmlinuz-6.8.0-45-generic
Found initrd image: /boot/initrd.img-6.8.0-45-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...


Unhide GRUB boot menu in sda7/boot/grub/grub.cfg


Boot successfully repaired.


You can now reboot your computer.
Please do not forget to make your UEFI firmware boot on the The OS now in use - Ubuntu 24.10 entry (sda1/efi/ubuntu/grubx64.efi file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi




============================ Boot Info After Repair ============================


 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/Manjaro/grubx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/SecureBootRecovery.efi /bootmgr


sda2: __________________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 


sda3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /bootmgr /Windows/System32/winload.exe


sda4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 1618642944. But according to the info from 
                       fdisk, sda4 starts at sector 504604672.
    Operating System:  
    Boot files:        


sda5: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 1927069696. But according to the info from 
                       fdisk, sda5 starts at sector 924035072.
    Operating System:  
    Boot files:        


sda6: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 1928742912. But according to the info from 
                       fdisk, sda6 starts at sector 925708288.
    Operating System:  
    Boot files:        


sda7: __________________________________________________________________________


    File system:       btrfs
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub


sdb1: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb2: __________________________________________________________________________


    File system:       BIOS Boot partition
    Boot sector type:  Unknown
    Boot sector info: 


sdb3: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


sdb4: __________________________________________________________________________


    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        




================================ 2 OS detected =================================


OS#1 (linux):   The OS now in use - Ubuntu 24.10 on sda7
OS#2 (windows):   Windows 10 or 11 on sda3


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: GM107M [GeForce GTX 960M] HD Graphics 530 from NVIDIA Corporation Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-6.11.0-8-generic root=UUID=d9350585-506b-4b2a-b402-eba8497ffdaf ro quiet splash crashkernel=2G-4G:320M,4G-32G:512M,32G-64G:1024M,64G-128G:2048M,128G-:4096M vt.handoff=7
df -Th / : /dev/sda7      btrfs   40G   23G   17G  58% /


===================================== UEFI =====================================


BIOS/UEFI firmware: 1.3.1(1.3) from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this installed-session.
No EFI in dmseg.
SecureBoot disabled - This system doesn't support Secure Boot.
BootOrder: 0000
Boot0000* Ubuntu    HD(1,GPT,02efc03c-0d0c-43a9-966e-a6ad53c9edc5,0x800,0xfa000)/File(\EFI\ubuntu\shimx64.efi)
Boot0003* Hard Drive    BBS(Floppy,,0x0)0000474f00004e4f97000000010000006f00480061007200640020004400720069007600650000000501090001000000007fff040002010c00d041030a0000000001010600001703120a000000ffff00007fff040001043e00ef47642dc93ba041ac194d51d01b4ce6340053003400310042004e004d00300030003400340032003100350020005400200020002000200000007fff04000000424f




============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
sdb    : is-GPT,    hasBIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda7    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sdb4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb3    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB


Partitions info (2/3): _________________________________________________________


sda7    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, btrfs
sdb4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sdb3    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sda4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sda5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot, ntfs
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot, ntfs
sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    notwinboot, vfat
sda6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot, ntfs


Partitions info (3/3): _________________________________________________________


sda7    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdb4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdb1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sda4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda6    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 453.23 GiB, 486650431488 bytes, 950489124 sectors
Disk identifier: 8B5DCA2D-7E5D-4004-ADE0-F471AC7C06E6
         Start       End   Sectors   Size Type
sda1       2048   1026047   1024000   500M EFI System
sda2    1026048   1288191    262144   128M Microsoft reserved
sda3    1288192 422440732 421152541 200.8G Microsoft basic data
sda4  504604672 828987391 324382720 154.7G Microsoft basic data
sda5  924035072 925708287   1673216   817M Windows recovery environment
sda6  925708288 950489087  24780800  11.8G Windows recovery environment
sda7  422440734 504604671  82163938  39.2G Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: C84F2E0C-0CF3-4DB4-995D-BD65A63798A4
          Start        End    Sectors   Size Type
sdb1        2048 1797715967 1797713920 857.2G Microsoft basic data
sdb2  1797715968 1797718015       2048     1M BIOS boot
sdb3  1797718016 2883026943 1085308928 517.5G Microsoft basic data
sdb4  2883026944 3516325887  633298944   302G Microsoft basic data


parted -lm (filtered): _________________________________________________________


sda:487GB:scsi:512:512:gpt:ATA Samsung SSD 860:;
1:1049kB:525MB:524MB:fat32:EFI system partition:boot, esp;
2:525MB:660MB:134MB::Microsoft reserved partition:msftres;
3:660MB:216GB:216GB:ntfs:Basic data partition:msftdata;
7:216GB:258GB:42.1GB:btrfs:root:;
4:258GB:424GB:166GB:ntfs:Basic data partition:msftdata;
5:473GB:474GB:857MB:ntfs::hidden, diag;
6:474GB:487GB:12.7GB:ntfs::hidden, diag;
sdb:2000GB:scsi:512:512:gpt:ATA Samsung SSD 870:;
1:1049kB:920GB:920GB:ntfs:Basic data partition:msftdata;
2:920GB:920GB:1049kB:::bios_grub;
3:920GB:1476GB:556GB:ntfs:Basic data partition:msftdata;
4:1476GB:1800GB:324GB:ntfs:Basic data partition:msftdata;


Free space >10MiB: ______________________________________________________________


sda: 404779MiB:451189MiB:46410MiB
sdb: 1716956MiB:1907729MiB:190773MiB


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL             PARTLABEL
sda                                                                                                         
&#9500;&#9472;sda1 vfat     4887-94F5                            02efc03c-0d0c-43a9-966e-a6ad53c9edc5 ESP               EFI system partition
&#9500;&#9472;sda2                                               f1410272-14bb-4f7d-902e-00c6476614da                   Microsoft reserved partition
&#9500;&#9472;sda3 ntfs     CAB25579B2556B49                     f6803be0-038e-4009-b1b4-00e11a35631b OS                Basic data partition
&#9500;&#9472;sda4 ntfs     E6BA3670BA363CFD                     6a32a8f3-3407-4639-8ef8-23d8357c216d Vrac primary      Basic data partition
&#9500;&#9472;sda5 ntfs     0E029F42029F2DA9                     deca5c9e-e30b-4e86-bb82-db98815c1b35 WINRETOOLS        
&#9500;&#9472;sda6 ntfs     AEC4A02AC49FF2B7                     3e650648-465c-47f3-a779-7bf06125fb6d Image             
&#9492;&#9472;sda7 btrfs    d9350585-506b-4b2a-b402-eba8497ffdaf 2b15366a-c7a7-ef4a-bee8-6f65e8462058                   root
sdb                                                                                                         
&#9500;&#9472;sdb1 ntfs     0296F50996F4FDCB                     9d17a0a0-6488-4fb9-b86d-2538dbd4b36a Data              Basic data partition
&#9500;&#9472;sdb2                                               dd84a79c-1d3b-4e5e-a778-4eee6f623cba                   
&#9500;&#9472;sdb3 ntfs     FE0A058E0A05455D                     92cfda1c-bec8-433f-964b-0dc2796eb769 Games             Basic data partition
&#9492;&#9472;sdb4 ntfs     DE5ACB645ACB3853                     9a33b971-5eb6-40b9-b3f4-1479487d829d Save and Recovery Basic data partition


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/sda3               49.7G  75% /mnt/boot-sav/sda3
/dev/sda4               70.2G  55% /mnt/boot-sav/sda4
/dev/sda5              420.6M  49% /mnt/boot-sav/sda5
/dev/sda6               69.4M  99% /mnt/boot-sav/sda6
/dev/sda7               16.6G  56% /
/dev/sdb1              147.8G  83% /media/pfelelep/Data
/dev/sdb3              182.5G  65% /mnt/boot-sav/sdb3
/dev/sdb4                 42G  86% /mnt/boot-sav/sdb4
efivarfs                  41K  82% /sys/firmware/efi/efivars


Mount options (filtered): ______________________________________________________


/dev/sda3              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda4              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda6              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda7              btrfs           rw,relatime,ssd,discard=async,space_cache=v2,subvolid=5,subvol=/
/dev/sdb1              ntfs3           rw,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8
/dev/sdb3              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb4              fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096


===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================


search.fs_uuid d9350585-506b-4b2a-b402-eba8497ffdaf root hd0,gpt7 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg


====================== sda7/boot/grub/grub.cfg (filtered) ======================


Ubuntu   d9350585-506b-4b2a-b402-eba8497ffdaf
Windows Boot Manager (on sda1)   osprober-efi-4887-94F5
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


========================== sda7/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during curtin installation
/dev/disk/by-uuid/d9350585-506b-4b2a-b402-eba8497ffdaf / btrfs defaults 0 1
# /boot/efi was on /dev/sda1 during curtin installation
UUID=4887-94F5  /boot/efi       vfat    defaults      0       1


======================= sda7/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


==================== sda7: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
 202.592394829 = 217.531927552  boot/grub/grub.cfg                             1
 207.728102684 = 223.046351872  boot/vmlinuz                                   1
 207.728102684 = 223.046351872  boot/vmlinuz-6.11.0-8-generic                  1
 207.453169823 = 222.751144960  boot/vmlinuz-6.8.0-45-generic                  1
 207.453169823 = 222.751144960  boot/vmlinuz.old                               1
 223.713049889 = 240.210058240  boot/initrd.img                                2
 223.713049889 = 240.210058240  boot/initrd.img-6.11.0-8-generic               2
 208.734850883 = 224.127339520  boot/initrd.img-6.8.0-41-generic               2
 223.657198906 = 240.150088704  boot/initrd.img-6.8.0-45-generic               2
 223.657198906 = 240.150088704  boot/initrd.img.old                            2


===================== sda7: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18133 Apr  4  2024 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4  2024 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4  2024 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4  2024 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4  2024 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4  2024 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5  2024 35_fwupd
-rwxr-xr-x 1 root root   214 Apr  4  2024 40_custom
-rwxr-xr-x 1 root root   215 Apr  4  2024 41_custom
```

---

### Post by tea for one on 2024-10-17
```
efibootmgr -v (filtered) after grub install
BootOrder: 0000
Boot0000* Ubuntu    HD(1,GPT,02efc03c-0d0c-43a9-966e-a6ad53c9edc5,0x800,0xfa000)/File(EFIubuntushimx64.efi)
Boot0003* Hard Drive    BBS
```
The Windows file is missing again.
You reported in post 8 that you fixed it, can you try the same command?

---

### Post by oldfred on 2024-10-17
Normally the issue is UEFI erases Ubuntu entries. Most UEFI seem to auto find the /efi/Microsoft folder & add an UEFI boot entry for Windows, but not find any Linux installs.

Grub can only boot working Windows. If it boots from UEFI (after adding entry again) it may be it needs chkdsk or has turned fast startup back on. It often turns fast startup aback on with updates. Fast startup sets hibernation flag & then Linux NTFS driver will not fully read/write NTFS.
Or Windows could need other repairs, which only can be done from a Windows repair/recovery drive which you should always have or from a Windows install flash drive with a recovery/repair console.

---

### Post by yancek on 2024-10-17
The EFI boot entry being missing is definitely a problem as mentioned in the last post.  What happens when you set Boot0003* Hard Drive to first boot priority in the BIOS boot options?  Does it still fail?   

Boot repair does not 'repair' windows boot files, it simply creates a standard menuentry for windows.  If windows boot files are missing from their expected location or are damaged you will need to use some windows software to repair it.  

In your last post, you show the output of sudo update-grub which indicates that it did find windows and create an entry for it so go into the /boot/grub/grub.cfg file and find the menuentry for windows and post it here.   You should have an entry similar to the below entries which is a standard entry and has what shows as your UUID for the EFI partition in your boot repair output .  You could copy them there to test and if that fails, it is likely or windows boot files are corrupted.

>  menuentry 'Windows' {
   search --fs-uuid --set=root 4887-94F5
   chainloader /EFI/Microsoft/Boot/bootmgfw.efi
}
menuentry 'Windows'{
search --no-floppy --fs-uuid --set=root 4887-94F5
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
    }

---

### Post by pfelelep on 2024-10-17
@[COLOR=#000000]**yancek**
[/COLOR]> [COLOR=#000000]go into the /boot/grub/grub.cfg file and find the menuentry for windows and post it here. [/COLOR]
here it is:
```
menuentry 'Windows Boot Manager (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-efi->        insmod part_gpt
        insmod fat
        set root='hd0,gpt1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt1 --hint-efi=hd0,gpt1 --hint-baremetal=ah>
        else
          search --no-floppy --fs-uuid --set=root 4887-94F5
        fi
        chainloader /EFI/Microsoft/Boot/bootmgfw.efi



```



@**tea for one**
> [COLOR=#000000]You reported in post 8 that you fixed it, can you try the same command?[/COLOR]

Yes, that should bring windows again.




@[COLOR=#000000]**oldfred:**
[/COLOR]> [COLOR=#000000]If it boots from UEFI (after adding entry again) it may be it needs chkdsk or has turned fast startup back on. [/COLOR][COLOR=#000000]

It didn't turn the fastboot ON last time, but I will check again and also do a chkdsk.


[/COLOR]

---

### Post by pfelelep on 2024-10-17
I am posting all the steps

1/ run the command sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

here is the result:
```
pfelelep@pfelelep-Inspiron-7559:~$ sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"[sudo] password for pfelelep: 
BootOrder: 0000
Boot0003* Hard Drive    BBS(Floppy,,0x0)0000474f00004e4f97000000010000006f00480061007200640020004400720069007600650000000501090001000000007fff040002010c00d041030a0000000001010600001703120a000000ffff00007fff040001043e00ef47642dc93ba041ac194d51d01b4ce6340053003400310042004e004d00300030003400340032003100350020005400200020002000200000007fff04000000424f
Boot0000* Windows Boot Manager    HD(1,GPT,02efc03c-0d0c-43a9-966e-a6ad53c9edc5,0x800,0xfa000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)



```

I am rebooting now :arrow:

---

### Post by pfelelep on 2024-10-17
reboot brought me straight to windows (no grub)

2/ I check the power options, no fast boot activated:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294379&stc=1[/IMG]

3/ but the hiberfil.sys file is present here, I will turn the hibernation option OFF and delete it.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294381&stc=1[/IMG]


4/ I am running a chkdsk now from command prompt.
```
C:\windows\system32>chkdsk
The type of the file system is NTFS.
Volume label is OS.


WARNING!  /F parameter not specified.
Running CHKDSK in read-only mode.


Stage 1: Examining basic file system structure ...
  1238784 file records processed.
File verification completed.
 Phase duration (File record verification): 12.61 seconds.
  22556 large file records processed.
 Phase duration (Orphan file record recovery): 0.00 milliseconds.
  0 bad file records processed.
 Phase duration (Bad file record checking): 0.50 milliseconds.


Stage 2: Examining file name linkage ...
  874 reparse records processed.
  1676434 index entries processed.
Index verification completed.
 Phase duration (Index verification): 29.94 seconds.
  0 unindexed files scanned.
 Phase duration (Orphan reconnection): 14.29 seconds.
  0 unindexed files recovered to lost and found.
 Phase duration (Orphan recovery to lost and found): 1.32 milliseconds.
  874 reparse records processed.
 Phase duration (Reparse point and Object ID verification): 12.83 milliseconds.


Stage 3: Examining security descriptors ...
Security descriptor verification completed.
 Phase duration (Security descriptor verification): 34.31 milliseconds.
  218826 data files processed.
 Phase duration (Data attribute verification): 2.04 milliseconds.
CHKDSK is verifying Usn Journal...
  38276440 USN bytes processed.
Usn Journal verification completed.
 Phase duration (USN journal verification): 246.37 milliseconds.


Windows has scanned the file system and found no problems.
No further action is required.


 210576268 KB total disk space.
 159598896 KB in 612640 files.
    479444 KB in 218827 indexes.
         0 KB in bad sectors.
   1351944 KB in use by the system.
     65536 KB occupied by the log file.
  49145984 KB available on disk.


      4096 bytes in each allocation unit.
  52644067 total allocation units on disk.
  12286496 allocation units available on disk.
Total duration: 57.16 seconds (57168 ms).


```

no problem here either.

---

### Post by tea for one on 2024-10-17
> **pfelelep said:**
> I am posting all the steps
1/ run the command sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

here is the result:
```
pfelelep@pfelelep-Inspiron-7559:~$ sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"[sudo] password for pfelelep: 
BootOrder: 0000
Boot0003* Hard Drive    BBS(Floppy,,0x0)0000474f00004e4f97000000010000006f00480061007200640020004400720069007600650000000501090001000000007fff040002010c00d041030a0000000001010600001703120a000000ffff00007fff040001043e00ef47642dc93ba041ac194d51d01b4ce6340053003400310042004e004d00300030003400340032003100350020005400200020002000200000007fff04000000424f
Boot0000* Windows Boot Manager    HD(1,GPT,02efc03c-0d0c-43a9-966e-a6ad53c9edc5,0x800,0xfa000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)
```
I am rebooting now :arrow:
Now, your efibootmgr does not have the Ubuntu entry, which you had in post 16.
Two suggestions:-
Can you boot Ubuntu from your PC boot menu?
Create an efibootmgr entry for Ubuntu?

---

### Post by pfelelep on 2024-10-18
Good Morning :-)

so, I rebooted using the same way described in [#post 9]("https://ubuntuforums.org/showthread.php?t=2501617&p=14209580#post14209580") (with the boot option F12 key)

I am back on Ubuntu now.

---

### Post by pfelelep on 2024-10-18
Now, booting into the UEFI menu > File Browser Add Boot Option > > Select...
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294386&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294385&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294384&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294383&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294382&stc=1[/IMG]

 
[LIST]
[*]**Ubuntu** brings me GRUB.64.efi (not shown on the attached pictures, sorry)
[*]**Boot** brings me Boot.64.efi
[*](the **Manjaro** entry is from an earlier distro I was using, I should clean that up)
[/LIST]

Should I choose grubx64.efi or bootx64.efi?
I assume the question here is: should I add the GRUB entry or directly the Ubuntu entry... what will happen on the next update/ grub update?

---

### Post by oldfred on 2024-10-18
The bootx64.efi is seen as a drive entry.
The bootx64.efi is originally s a copy of Windows boot file, but installing grub normally copies shimx64.efi to /EFI/Boot/bootx64.efi. The drive entry or /EFI/Boot/bootx64.efi is a backup entry. The only way I can tell grubx64,shimx64, bootx64 & Windows bootmgfw.efi is by file size and which folder in ESP they are in.

I do not have UEFI Secure boot on, but it still uses shimx64.efi. Grubx64.efi only works with secure boot off, but shimx64.efi seems to work with UEFI secure boot on or off.

I thought Windows UEFI boot entry was always bootmgfw.efi as shown in your UEFI boot entry for Windows. It should also be in the /EFI/Microsoft folder in the ESP.

---

### Post by yancek on 2024-10-18
I'm guessing that your windows boot files are corrupted if you cannot boot with the windows entry you show in post 20.  That is as it should be.  Do you still get the same result trying to select that option?  Seems pretty bizarre to me that when you created the ubuntu entry in your EFI windows disappeared and when you created the windows entry, ubuntu disappeared.

---

### Post by pfelelep on 2024-10-19
> **yancek said:**
> Do you still get the same result trying to select that option?

Yes, same result: [I]cannot load image
[/I]
> **yancek said:**
> Seems pretty bizarre to me that when you created the ubuntu entry in your EFI windows disappeared and when you created the windows entry, ubuntu disappeared.

Ubuntu (actually the GRUB loader was listed in the boot order entries (on the **4th entry)**, it is still named "windows boot manager" but it's the Grub! The Grub that cannot load W10
The **FIRST** "windows boot manager" entry is booting W10 normally.

---

### Post by pfelelep on 2024-10-19
now I am thinking,
 since the [windows boot entry manually added works]("https://ubuntuforums.org/showthread.php?t=2501617&p=14209560#post14209560") (thanks to Oldfred) but the windows boot in grub entry seems corrupted...


should I try to run
```
[COLOR=#0C0D0E][FONT=ui-monospace]if [ "${grub_platform}" == "efi" ]; then menuentry "Microsoft Windows 10 UEFI/GPT" { insmod part_gpt insmod fat insmod chain search --no-floppy --fs-uuid --set=root $hints_string $fs_uuid chainloader /EFI/Microsoft/Boot/bootmgfw.efi } fi[/FONT][/COLOR]
```

...according to this method? 
[URL="https://unix.stackexchange.com/questions/746954/grub-broke-my-windows-boot-how-to-fix"]https://unix.stackexchange.com/questions/746954/grub-broke-my-windows-boot-how-to-fix
[/URL]
I need your advice (sorry that it's taking so long, I really appreciate your help) :oops:

---

### Post by tea for one on 2024-10-19
Can you still boot into Ubuntu 24.10?
If so, please open a terminal and enter:-
```
efibootmgr
```
What do you see?

---

### Post by pfelelep on 2024-10-19
> **tea for one said:**
> Can you still boot into Ubuntu 24.10?
yes, using the grub loader I can still boot ubuntu

> **tea for one said:**
> If so, please open a terminal and enter:-
```
efibootmgr
```
What do you see?

I got this:
> pfelelep@pfelelep-Inspiron-7559:~$ efibootmgrNo BootOrder is set; firmware will attempt recovery
Boot0003* Hard Drive    BBS(Floppy,,0x0)0000474f00004e4f97000000010000006f00480061007200640020004400720069007600650000000501090001000000007fff040002010c00d041030a0000000001010600001703120a000000ffff00007fff040001043e00ef47642dc93ba041ac194d51d01b4ce6340053003400310042004e004d00300030003400340032003100350020005400200020002000200000007fff04000000424f




---

### Post by tea for one on 2024-10-19
I'm very surprised to see that you do not have any efi files for Ubuntu or Windows?
They seem to constantly disappear............?
While you are in Ubuntu, open a terminal and run:-
```
sudo update-grub
```
What is the output?

---

### Post by pfelelep on 2024-10-19
> **tea for one said:**
> I'm very surprised to see that you do not have any efi files for Ubuntu or Windows?
They seem to constantly disappear............?

me too... I start to think my laptop could be haunted...:biggrin:

```
pfelelep@pfelelep-Inspiron-7559:~$ sudo update-grub[sudo] password for pfelelep: 
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/kdump-tools.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.11.0-8-generic
Found initrd image: /boot/initrd.img-6.11.0-8-generic
Found linux image: /boot/vmlinuz-6.8.0-45-generic
Found initrd image: /boot/initrd.img-6.8.0-45-generic
Found memtest86+ 64bit EFI image: /boot/memtest86+x64.efi
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done



```

---

### Post by tea for one on 2024-10-19
The output from update-grub looks normal.
Now, I suggest that you reboot into Windows 10
Run chkdsk, defrag and any other disk tools.
Double check that fast startup and hibernation are disabled.
Power off when you think all suitable utilities have been run.
Power on and see if Grub appears and you can boot Windows via Grub?

Edit: Please isolate, de-activate or physically remove Disk sdb: 1.82 TiB before power on.

---

### Post by yancek on 2024-10-19
> efibootmgr No BootOrder is set; firmware will attempt recovery 

If you don't have any luck with the other suggestions, you might try an online search on how reset the boot order on your specific manufacturer UEFI BIOS.

---

### Post by pfelelep on 2024-10-19
> **tea for one said:**
> The output from update-grub looks normal.
Now, I suggest that you reboot into Windows 10
Run chkdsk, defrag and any other disk tools.
Double check that fast startup and hibernation are disabled.
Power off when you think all suitable utilities have been run.
Power on and see if Grub appears and you can boot Windows via Grub?

Edit: Please isolate, de-activate or physically remove Disk sdb: 1.82 TiB before power on.

unfortunately, we're back on stage 1: the grub menu appears, but choosing the **windows boot manager on /dev/sda1 **gets me the same **error : cannot load the image** again.
the only way I can boot on windows is to [URL="https://ubuntuforums.org/showthread.php?t=2501617&p=14209560#post14209560"][COLOR=#000000]create a new entry, if ESP is sda1, uses defaults:[/COLOR]
[COLOR=#000000]sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"[/COLOR][/URL] again.

(btw, I physically disconnected the Disk sdb: 1.82 TiB before I rebooted)

---

### Post by pfelelep on 2024-10-19
> **yancek said:**
> If you don't have any luck with the other suggestions, you might try an online search on how reset the boot order on your specific manufacturer UEFI BIOS.

I won't mind but the issue is that *either* I:
> [COLOR=#000000][FONT=&amp]sudo update-grub[/FONT][/COLOR]
and this allows me to boot ubuntu (but not windows as the windows boot manager option seems corrupt?)

*or*:
 I create the new entry
 > 
create a new entry, if ESP is sda1, uses defaults:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

and then I directly boot on windows without any option to boot ubuntu.

to summarize: I just don't have any (working) option to boot either windows or ubuntu at the same time. any repair to get either windows or grub/ubuntu will break the other boot option. :/

I am on ubuntu now: I can't boot windows unless I "*create a new entry, if ESP is sda1, uses defaults:**sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi""*

---

### Post by tea for one on 2024-10-19
4 days without concrete progress........a bit frustrating, methinks?
I don't know what else to suggest at the moment other than a more radical approach.
You have two disks on your PC, would you consider Windows on one disk and Ubuntu on the other?
I reckon we could eliminate the haunting before Halloween ;)

---

### Post by oldfred on 2024-10-20
If grub does not boot Windows but UEFI does, then fast startup, bitlocker or chkdsk required.
Grub only boots working Windows, but settings make a difference.


Windows updates may turn settings back on with updates when you directly boot it and you may not see update.

---

### Post by pfelelep on 2024-10-20
> **oldfred said:**
> If grub does not boot Windows but UEFI does, then fast startup, bitlocker or chkdsk required.
Grub only boots working Windows, but settings make a difference.

Windows updates may turn settings back on with updates when you directly boot it and you may not see update.

I did: chkdsk: no error, no hiberfile, no bitlocker, no fastboot, all seems clean.
no windows update so far that I can check.
Grub is pointing to a windows boot file that doesn't work, while the UEFI windows entry works well... it puzzles me...

---

### Post by pfelelep on 2024-10-20
> **tea for one said:**
> 
You have two disks on your PC, would you consider Windows on one disk and Ubuntu on the other?
Actually, if you would be kind to help me through the steps, I'll be happy to try :)

> **tea for one said:**
> I reckon we could eliminate the haunting before Halloween ;)
Hehe, you have a plan [Dr Venkman]("https://en.wikipedia.org/wiki/Peter_Venkman")? :grin:

---

### Post by tea for one on 2024-10-21
> **pfelelep said:**
> Actually, if you would be kind to help me through the steps, I'll be happy to try :)
Hehe, you have a plan [Dr Venkman]("https://en.wikipedia.org/wiki/Peter_Venkman")? :grin:
Yes, I have a plan
Let&#8217;s see if it is suitable for you?

The plan is to tidy up the Windows disk sda and install Ubuntu on sdb

Backup all personal data from disk sda (both Windows and Ubuntu)
Backup data from disk sdb because you will eventually install Ubuntu here

Power off and remove disk sdb
Leave Windows on disk sda attached
Reset UEFI settings to default

Boot Windows and use Windows tools to remove Ubuntu partition from sda 
(or boot live Ubuntu session and remove all Ubuntu partitions from sda)
Possibly remove duplicated Windows recovery partition
Boot into Windows and check data is intact
Run chkdsk and other utilities to double check
Reboot a couple of times (just checking and re-checking)
Happy that Windows is booting and functioning as normal?

Remove Windows disk sda
Attach disk sdb
Disable Secure Boot and any TPM settings in UEFI
Boot into live Ubuntu 24.04 session in UEFI mode
Open Gparted and create GPT (this will completely remove all data and partitions, it doesn&#8217;t matter because you have a data backup)
Install Ubuntu 24.04 (your disk is approx 2TB so you may wish to leave free space for a shared NTFS partition later and/or other partitions)
Suggestion:-
ESP = partition 1 (default 1.13GB)
System = partition 2 say 50GB &#8211; Choose Ext4
Home = partition 3 say 100GB &#8211; Choose Ext4
Restore Ubuntu data
Reboot a few times to check that everything is OK
Add shared partition(s) later when all tests are satisfactory

The objective is:-
Windows and Ubuntu boot and operate independently
Each OS has its own ESP
If one fails to boot, it doesn&#8217;t affect the other (i.e. boot via PC boot menu)
A shared NTFS data partition can be added if required
Windows tools to repair Windows and Ubuntu tools to repair Ubuntu
For convenience, we can make grub boot Windows if you wish (although Windows will always boot independently)

---

### Post by pfelelep on 2024-10-23
Hello, sorry for the late reply, I have been busy with some family matters.

@[[COLOR=#000000]tea for one[/COLOR]]("https://ubuntuforums.org/member.php?u=585392")
Thank you so much for the detailed instructions, I will definitely work on it, but I need to get an external hard drive to backup the ssd first.

At the moment, I am investigating on a possible grub2 issue related to the latest 24.10 ubuntu, [as seen on the askubuntu forum:]("https://askubuntu.com/questions/1530083/cannot-boot-windows-from-grub-after-upgrade-to-kubuntu-24-10")
> [COLOR=#0C0D0E][FONT=-apple-system]It's due to an issue in GRUB2 being non-compatible with non-NX shim which includes Windows 10 [/FONT][/COLOR][https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2084104](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2084104)

---

### Post by pfelelep on 2024-11-20
Greetings everyone, 
sorry for the VERY late update, but the problem has been solved with an GRUB2 update, as the solution posted on the askubuntu forum:
[https://askubuntu.com/questions/1530083/cannot-boot-windows-from-grub-after-upgrade-to-kubuntu-24-10](https://askubuntu.com/questions/1530083/cannot-boot-windows-from-grub-after-upgrade-to-kubuntu-24-10)

[COLOR=#636B74][FONT=-apple-system][FONT=inherit]answered [FONT=inherit]Oct 16 at 19:42[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#636B74][FONT=-apple-system][URL="https://askubuntu.com/users/860828/bushkov"][FONT=inherit][IMG]https://www.gravatar.com/avatar/2f70a88dfba311d726e47f3d251a498f?s=64&d=identicon&r=PG&f=y&so-version=2[/IMG][/FONT]
[/URL][/FONT][/COLOR]
[COLOR=#636B74][FONT=-apple-system][bushkov]("https://askubuntu.com/users/860828/bushkov"):[/FONT][/COLOR]
> [COLOR=#0C0D0E][FONT=-apple-system]It's due to an issue in GRUB2 being non-compatible with non-NX shim which includes Windows 10
[/FONT][/COLOR]
[COLOR=#636B74][FONT=-apple-system][FONT=inherit]answered [FONT=inherit]Nov 15 at 15:38[/FONT][/FONT]
[/FONT][/COLOR]
[COLOR=#636B74][FONT=-apple-system][URL="https://askubuntu.com/users/1660002/milanium"][FONT=inherit][IMG]https://www.gravatar.com/avatar/62e3eab3fb631e8a8699bf309360a7ec?s=64&d=identicon&r=PG[/IMG][/FONT]
[/URL][/FONT][/COLOR]
[COLOR=#636B74][FONT=-apple-system][Milanium]("https://askubuntu.com/users/1660002/milanium")[/FONT][/COLOR]
> [COLOR=#0C0D0E][FONT=-apple-system]Follow the instructions at [/FONT][/COLOR][https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)[COLOR=#0C0D0E][FONT=-apple-system] then in a console [/FONT][/COLOR]sudo apt install -t oracular-proposed grub-common grub-efi-amd64-bin grub-efi-amd64-signed grub-efi-amd64-unsigned grub-pc grub-pc-bin grub2-common

The grub dual boot allows to boot from windows normally (/phew/).

MY deepest thanks to everyone who helped me as I was really "circonvolutionning" ](*,) madly.

I would like to thank personally **ubfan1, yancek,** **oldfred **and especially** tea for one**, who patiently wrote me a very detailed step-by-step method to make a clean reinstall of both ubuntu and windows on 2 separate HDs (I hope to use this method after new year, when my 2 daughters leave me some time to focuse on the task ) :biggrin:

problem solved, I will update the title of that post, I hope it can help other people.

---

