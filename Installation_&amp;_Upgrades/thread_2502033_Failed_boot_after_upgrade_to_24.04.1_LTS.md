---
title: "Failed boot after upgrade to 24.04.1 LTS"
date: 2024-10-30
forum: Installation &amp; Upgrades
---

### Post by wcalvert on 2024-10-30
Hello all.  As the title suggests, I've boofed something on the upgrade to 24.04.1 LTS and the machine (Dell Inspiron w/ dual windows boot option) will not boot.  Now says "no bootable device found" or similar.  I'm not any kind of expert, but ran the boot repair and will include the result here.  No change after the repair so now I'm a little stuck.   If you're able to assist .... thanks ahead.  Wilson

```
boot-repair-4ppa2081                                              [20241030_1637]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/ubuntu/fwupdx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.


================================ 2 OS detected =================================

OS#1 (linux):   Ubuntu 24.04.1 LTS on sda5
OS#2 (windows):   Windows 8 or 10 on sda3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: UHD Graphics 620 from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.3 LTS, focal, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.14.0(1.14) from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0001,0000,0002
Boot0000* Windows Boot Manager    HD(1,GPT,d091f8d5-b26d-4623-87e5-6864351227bd,0x800,0xf9800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...r................
Boot0001* Ubuntu    PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,32768,0)/HD(1,GPT,d091f8d5-b26d-4623-87e5-6864351227bd,0x800,0xf9800)/File(/EFI/Ubuntu)
Boot0002* UEFI: SanDisk Cruzer 8.02, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(1,MBR,0x2cf4ba3a,0x506fcc,0x1f40)..BO

66f69798ad23240e43b7ba0044a914c4   sda1/Boot/bkpbootx64.efi
66f69798ad23240e43b7ba0044a914c4   sda1/Boot/bootx64.efi
2895d47544fd587b26c7e29be1295c27   sda1/Boot/fbx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sda1/Boot/mmx64.efi
b79608a8b4b6d20b9434d77fe1b85b3d   sda1/ubuntu/fwupdx64.efi
66f69798ad23240e43b7ba0044a914c4   sda1/ubuntu/grubx64.efi
dc3c47be2f78a78e5e57d097ae6c5c84   sda1/ubuntu/mmx64.efi
78415fb8fb9b909f8029858113f1335f   sda1/ubuntu/shimx64.efi
ee7c82a82dd0ce765ff8f9515d0dfb55   sda1/Microsoft/Boot/bootmgfw.efi
86c49eee6e6bf50ddfdd9c62f6ad9e84   sda1/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda5    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, vfat
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sda4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot, ntfs
sda5    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: E6263EE3-847B-4E08-9B2D-93BF846CD904
          Start        End   Sectors   Size Type
sda1        2048    1023999   1021952   499M EFI System
sda2     1024000    1286143    262144   128M Microsoft reserved
sda3     1286144  929718271 928432128 442.7G Microsoft basic data
sda4  1952600064 1953521663    921600   450M Windows recovery environment
sda5  1541400576 1952600063 411199488 196.1G Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 3.76 GiB, 4022337024 bytes, 7856127 sectors
Disk identifier: 0x2cf4ba3a
     Boot   Start     End Sectors  Size Id Type
sdb1  *          0 5999871 5999872  2.9G  0 Empty
sdb2       5271500 5279499    8000  3.9M ef EFI (FAT-12/16/32)
sdb3       6000640 7856126 1855487  906M 83 Linux

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:gpt:ATA ST1000LM035-1RK1:;
1:1049kB:524MB:523MB:fat32:EFI system partition:boot, esp;
2:524MB:659MB:134MB::Microsoft reserved partition:msftres;
3:659MB:476GB:475GB:ntfs:Basic data partition:msftdata;
5:789GB:1000GB:211GB:ext4::;
4:1000GB:1000GB:472MB:ntfs::hidden, diag;
sdb:4022MB:scsi:512:512:unknown:SanDisk Cruzer:;

Free space >10MiB: ______________________________________________________________

sda: 453964MiB:752637MiB:298673MiB

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                
&#9500;&#9472;sda1 vfat     EEDC-1691                            d091f8d5-b26d-4623-87e5-6864351227bd ESP                      EFI system partition
&#9500;&#9472;sda2                                               c3f72f69-12fb-4823-998c-849c888d7b69                          Microsoft reserved partition
&#9500;&#9472;sda3 ntfs     2E38DFD638DF9B63                     d9a742a6-ede8-4cce-878f-d55fe158adcc OS                       Basic data partition
&#9500;&#9472;sda4 ntfs     5C1219C81219A852                     f7cd1e6f-7072-427d-b3f7-d197956be9e5 WINRETOOLS               
&#9492;&#9472;sda5 ext4     2e8a4205-058b-44bc-810a-910260e478f3 e3141ef3-8bb9-4441-828a-3a5b6546202f                          
sdb    iso9660  2021-08-19-11-03-38-00                                                    Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdb1 iso9660  2021-08-19-11-03-38-00               2cf4ba3a-01                          Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdb2 vfat     54C5-9C6C                            2cf4ba3a-02                                                   
&#9492;&#9472;sdb3 ext4     e8fbacfc-6eee-46bc-a286-eb39f31c3d19 2cf4ba3a-03                          writable                 

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/sda1                                                     436.5M  12% /mnt/boot-sav/sda1
/dev/sda3                                                     406.1G   8% /mnt/boot-sav/sda3
/dev/sda4                                                       103M  77% /mnt/boot-sav/sda4
/dev/sda5                                                     139.5G  23% /mnt/boot-sav/sda5
/dev/sdb1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda1                                                     vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda3                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda4                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5                                                     ext4            rw,relatime
/dev/sdb1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 2e8a4205-058b-44bc-810a-910260e478f3 root hd0,gpt5 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sda5/boot/grub/grub.cfg (filtered) ======================

Ubuntu   2e8a4205-058b-44bc-810a-910260e478f3
Windows Boot Manager (on sda1)   osprober-efi-EEDC-1691
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

========================== sda5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=2e8a4205-058b-44bc-810a-910260e478f3 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=EEDC-1691  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

======================= sda5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

==================== sda5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
 765.030693054 = 821.445451776  boot/grub/grub.cfg                             1
 854.425060272 = 917.431922688  boot/vmlinuz                                   2
 766.437652588 = 822.956163072  boot/vmlinuz-5.15.0-124-generic                2
 854.425060272 = 917.431922688  boot/vmlinuz-6.8.0-47-generic                  2
 766.437652588 = 822.956163072  boot/vmlinuz.old                               2
 859.747066498 = 923.146383360  boot/initrd.img                                6
 799.864253998 = 858.847703040  boot/initrd.img-5.15.0-124-generic             7
 859.747066498 = 923.146383360  boot/initrd.img-6.8.0-47-generic               6
 799.864253998 = 858.847703040  boot/initrd.img.old                            7

===================== sda5: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18133 Apr  4  2024 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4  2024 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4  2024 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4  2024 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4  2024 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4  2024 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  4  2024 40_custom
-rwxr-xr-x 1 root root   215 Apr  4  2024 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
sda5,
using the following options:  sda1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 24.04.1 LTS entry (sda1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)
```

---

### Post by yancek on 2024-10-30
Does that mean you can not boot either Ubuntu or windows?  There's nothing in boot repair that would indicate a problem.  When you say you upgraded, what did you upgrade FROM and HOW did you upgrade?  Did you use terminal commands, use the software updater, reinstall over the old system using the same drive/partition?  When you access your BIOS, are you able to boot either windows or ubuntu from the UEFI menu boot options?

---

### Post by wcalvert on 2024-10-30
Yanek, thanks for the questions.  Agree that the boot repair shows nothing wrong, but the machine will still not boot.  

I did the upgrade from 22 to 24 using the software updater.  There are questions along the way for how to do the install, and I'm thinking I took the wrong path.  My intent was to install the new version without disturbing the existing files, not a clean wipe.  

I can choose to boot to ubuntu or windows when accessing the one time boot menu.  Ubuntu won't continue past the error of "no bootable device.." and windows goes to a page that says that "there is a problem .." and attempts to do a repair but fails.  In order for me to be more specific I'll need to exit this session (Live) and take some notes.

So now I'm looking for more specific questions or direction.

---

### Post by yancek on 2024-10-30
> My intent was to install the new version without disturbing the existing files, not a clean wipe 

 I saw a recent post that indicated that option was available in the 24.04 installer, not sure about the software update/upgrade   That has always been possible using a manual installation.  One would simply select to NOT format the / filesystem and/or data partitions during an install.  Just did that successfully last week with Slackware.

When you boot and access the BIOS (not the one time boot options), do you have an option to Boot from EFI file?  If so, do that and look for the ubuntu directory option and check to see what files are available to boot and try them if they are there to see if you get the same result.  Do the same with windows.

Did you keep notes during this upgrade?  Do you remember what option you chose for the upgrade?  Did you get any warning or error message during the upgrade that you recall?  Since you are able to boot the USB with Ubuntu 20.04 on it, you are changing the default boot device in the BIOS before booting from the internal??  I don't know that it would help but, when you are doing repairs like this it is best to have the same version as the installed version, in this case 24.04.  Don't really have any other suggestions.

---

### Post by tea for one on 2024-10-30
> **wcalvert said:**
> So now I'm looking for more specific questions or direction.
rEFInd may help.
You do not have to install it to your internal disk, simply make a bootable USB
[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
[https://www.rodsbooks.com/refind/getting.html](https://www.rodsbooks.com/refind/getting.html) > A USB Flash Drive Image File 
Options include:-
Start an EFI shell (where you can find both Windows and Ubuntu boot files)
Boot the kernel directly
Find and boot the grub efi file

---

### Post by wcalvert on 2024-10-30
Your comments are most appreciated... and I'll say that most of the language is over my head!  I don't know how to do any of the following:

    Start an EFI shell (where you can find both Windows and Ubuntu boot files)
    Boot the kernel directly
    Find and boot the grub efi file 				

I do not find a boot option for my hd, so I added one that references the grub efi file (I think).  That will boot and goes to a login, where I am able to log in and use a terminal type entry format.  But no GUI access.  

I'll take a look at your suggestions and see what else might work.

And for now, the install does not give me the option to install without erasing everything, with big warnings!  Will more into that as well.  

Thanks

---

### Post by wcalvert on 2024-10-30
Your comments are most appreciated... and I'll say that most of the language is over my head!  I don't know how to do any of the following:

    Start an EFI shell (where you can find both Windows and Ubuntu boot files)
    Boot the kernel directly
    Find and boot the grub efi file                 

I do not find a boot option for my hd, so I added one that references the grub efi file (I think).  That will boot and goes to a login, where I am able to log in and use a terminal type entry format.  But no GUI access.  

I'll take a look at your suggestions and see what else might work.

And for now, the install does not give me the option to install without erasing everything, with big warnings!  Will more into that as well.  

Thanks

---

### Post by wcalvert on 2024-10-31
So I reinstalled 24.04.1 successfully without (I think) wiping any data.  Now it still will boot to the login screen but no access to the GUI.  I'm convinced it's only a boot path/options type issue.  

One thought I had was whether the dual boot is causing issues. 

It is booting to UEFI vs Legacy, AHCI vs RAID, Secure Boot disabled.  What else?

---

### Post by tea for one on 2024-10-31
> **wcalvert said:**
> Your comments are most appreciated... and I'll say that most of the language is over my head!  I don't know how to do any of the following:
    Start an EFI shell (where you can find both Windows and Ubuntu boot files)
    Boot the kernel directly
    Find and boot the grub efi file 
The rEFInd USB will take care of booting the kernel or booting the grub.efi file - it's point and click.
Using the EFI shell is a bit more complicated.
Did you make the USB successfully?

---

### Post by wcalvert on 2024-10-31
I looked at rEFind by installing it during a Live session but it didn't help any of the issues.  Although it did boot to the rEFind the next boot attempt.  Does it need to be on a thumb drive for it to do it's thing?  I'll give that a try for now.  Thanks

---

### Post by wcalvert on 2024-10-31
I have some really great instructions from: [https://forums.linuxmint.com/viewtopic.php?t=389479](https://forums.linuxmint.com/viewtopic.php?t=389479) but it isn't working on this machine running Live.  I'll move to another system and get that done, then come back and try refind on the broken machine ... stand by!

---

### Post by wcalvert on 2024-10-31
Ok, this is some progress but maybe not in the right direction.  I ran the refind, choosing the best option I could, and now the machine will boot to 24.04.1, but it looks like a totally clean install.

I do not recall choosing any option during the install that included an erase and install process, so now I'm stuck again.

Is there any avenue here that could help me recover the previous version and regain access to my data, or even a way to confirm it is still there?

Thanks

---

### Post by yancek on 2024-10-31
In an earlier post, you indicated you used the software updater in22.04 to update/upgrade to 24.04.  In post 8, you indicate that you reinstalled 24.04.   How?  Did you run the updater again or did you download a 24.04 iso file, write it to a USB and reinstall?  If you did an actual install from a USB, did you select to not format the / parittion?  If you allowed the default to format the partition then yes, it overwrote everything.  I explained this as an option I have used in an earlier post.

---

### Post by wcalvert on 2024-10-31
The first attempt was through the updater that appeared as an available update.  Later I was running the system from a USB in "try" mode to see if I could find the issue with the boot.  After I ran the refind it was able to boot from the HD.  Now the machine just acts like it's running 24.04 Live, but the USB is not plugged in.  So now without a viable backup (my mistake), it's on to trying to discover what's left of the data.  That might be a new post.

---

