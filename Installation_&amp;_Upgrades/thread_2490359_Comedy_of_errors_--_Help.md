---
title: "Comedy of errors -- Help"
date: 2023-08-31
forum: Installation &amp; Upgrades
---

### Post by makitso on 2023-08-31
I am attempting a dual-boot install Ubuntu 22.04.3 on a New Dell XPS 9530.  The first install went fine, just turned off Secure Boot. 
Now the sad part.

However, the windows partition was too large.  So, booted up to windows 11 and shrank the "C" drive partition down.  Windows booted fine after this.
I booted up the live CD and sized up the /home partition (gparted).  I then did a reinstall and it went fine till the error-ed out with not being able to write GRUB to the drive.

Unable to install GRUB in /dev/nvme0n1
Executing 'grub-install /dev/nvme0n1' failed.

Install: error: cannot open '/boot/efi/EFI/ubuntu/grubxc64.efi': Not a directory.

I have tried every UEFI setting change, including turning off RAID and using legacy for the disk drives.

Any Ideas???

---

### Post by Rubi1200 on 2023-08-31
Please use the liveUSB to boot and then run the report for the boot info script in my signature. No repairs, just the report please.

Should help us diagnose the situation better.

---

### Post by makitso on 2023-08-31
```

boot-repair-4ppa2056                                              [20230831_1715]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/dell/SOS/bootmgfw.efi 
                       /efi/dell/SOS/bootmgr.efi /efi/dell/SOS/bootx64.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

nvme0n1p2: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /Windows/System32/winload.exe

nvme0n1p4: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p5: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p6: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p7: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /etc/fstab /etc/default/grub

nvme0n1p8: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

nvme0n1p9: _____________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda already mounted or mount point busy.


================================ 2 OS detected =================================

OS#1:   Ubuntu 22.04.3 LTS on nvme0n1p7
OS#2:   Windows 10 or 11 on nvme0n1p3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Intel Corporation Intel Corporation from Intel Corporation Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.5.0(1.5) from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
No EFI in dmseg.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0002
Timeout: 5 seconds
BootOrder: 0003,0000,0002,0001
Boot0000* UEFI RST PC801 NVMe SK hynix 512GB YC1N00771180172S     HD(1,GPT,31de4d90-1354-40b5-ba69-a15cbef64037,0x800,0x78000)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.
Boot0001* UEFI HTTPs Boot    PciRoot(0x0)/Pci(0x1f,0x6)/MAC(000000000000,0)/IPv4(0.0.0.00.0.0.0,0,0)/Uri()N.....YM....R,Y.
Boot0002* UEFI Corsair Voyager 3.0 23A11105512706E5    PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(2,GPT,5c541e13-b3a0-44ac-aa74-c681547bcf3a,0x6e0e50,0x2754)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.
Boot0003* Windows Boot Manager    HD(1,GPT,31de4d90-1354-40b5-ba69-a15cbef64037,0x800,0x78000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0................

64349b3622c65f495a99dbf6102496e3   nvme0n1p1/Boot/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   nvme0n1p1/Boot/fbx64.efi
a660182adef313615746a665966d2ccc   nvme0n1p1/Boot/mmx64.efi
19cb825a89130540289671cfa7fcb7c9   nvme0n1p1/dell/SOS/bootmgfw.efi
467b94109a1cee7b81b6f247e0406757   nvme0n1p1/dell/SOS/bootmgr.efi
19cb825a89130540289671cfa7fcb7c9   nvme0n1p1/dell/SOS/bootx64.efi
e8ff23a00deb497b7c2810724c12b886   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
ffede7b36c5c8710ef9560a03f5c7948   nvme0n1p1/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p7    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios
nvme0n1p8    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
nvme0n1p5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
nvme0n1p6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
nvme0n1p7    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p8    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p6    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p7    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p8    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk identifier: 5C0ECF29-4B03-4755-9A40-474EDC21D3AC
              Start        End   Sectors   Size Type
nvme0n1p1      2048     493567    491520   240M EFI System
nvme0n1p2    493568     755711    262144   128M Microsoft reserved
nvme0n1p3    755712  191895551 191139840  91.1G Microsoft basic data
nvme0n1p4 951851008  953878527   2027520   990M Windows recovery environment
nvme0n1p5 953878528  997074943  43196416  20.6G Windows recovery environment
nvme0n1p6 997076992 1000187903   3110912   1.5G Windows recovery environment
nvme0n1p7 191895552  395937791 204042240  97.3G Linux filesystem
nvme0n1p8 395937792  885141503 489203712 233.3G Linux filesystem
nvme0n1p9 885141504  951851007  66709504  31.8G Linux swap
Partition table entries are not in disk order.
Disk sda: 14.96 GiB, 16063135744 bytes, 31373312 sectors
Disk identifier: 5C541E13-B3A0-44AC-AA76-C681547BCF3A
        Start      End  Sectors  Size Type
sda1       64  7212623  7212560  3.4G Microsoft basic data
sda2  7212624  7222691    10068  4.9M EFI System
sda3  7222692  7223291      600  300K Microsoft basic data
sda4  7225344 31373248 24147905 11.5G Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:16.1GB:scsi:512:512:gpt:Corsair Voyager 3.0:;
1:32.8kB:3693MB:3693MB::ISO9660:hidden, msftdata;
2:3693MB:3698MB:5155kB::Appended2:boot, esp;
3:3698MB:3698MB:307kB::Gap1:hidden, msftdata;
4:3699MB:16.1GB:12.4GB:ext4::;
nvme0n1:512GB:nvme:512:512:gpt:PC801 NVMe SK hynix 512GB:;
1:1049kB:253MB:252MB:fat32:EFI system partition:boot, esp;
2:253MB:387MB:134MB::Microsoft reserved partition:msftres;
3:387MB:98.3GB:97.9GB:ntfs:Basic data partition:msftdata;
7:98.3GB:203GB:104GB:ext4::;
8:203GB:453GB:250GB:ext4::;
9:453GB:487GB:34.2GB:linux-swap(v1)::swap;
4:487GB:488GB:1038MB:ntfs::hidden, diag;
5:488GB:511GB:22.1GB:ntfs::hidden, diag;
6:511GB:512GB:1593MB:ntfs::hidden, diag;

Free space >10MiB: ______________________________________________________________

nvme0n1: 488373MiB:488386MiB:13.3MiB

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                           PARTLABEL
sda         iso9660  2023-08-07-15-49-47-00                                                    Ubuntu-Budgie 22.04.3 LTS amd64 
&#9500;&#9472;sda1      iso9660  2023-08-07-15-49-47-00               5c541e13-b3a0-44ac-aa77-c681547bcf3a Ubuntu-Budgie 22.04.3 LTS amd64 ISO9660
&#9500;&#9472;sda2      vfat     F7DB-4D56                            5c541e13-b3a0-44ac-aa74-c681547bcf3a ESP                             Appended2
&#9500;&#9472;sda3                                                    5c541e13-b3a0-44ac-aa75-c681547bcf3a                                 Gap1
&#9492;&#9472;sda4      ext4     fd7d11c6-6573-4728-9524-53965f9db20d f97be1e3-9951-5747-9521-56b5ad414dfc writable                        
nvme0n1                                                                                                                        
&#9500;&#9472;nvme0n1p1 vfat     4AD8-634A                            31de4d90-1354-40b5-ba69-a15cbef64037 ESP                             EFI system partition
&#9500;&#9472;nvme0n1p2                                               e4ec7856-c05b-46fb-bf3b-8bf6ba2b6558                                 Microsoft reserved partition
&#9500;&#9472;nvme0n1p3 ntfs     A22EDA5C2EDA28D5                     69d54a89-8ea5-425c-94bf-a24e31970572 OS                              Basic data partition
&#9500;&#9472;nvme0n1p4 ntfs     0AB41C9EB41C8DF7                     e8624dde-3618-49ef-8264-27b57c1f54cc WINRETOOLS                      
&#9500;&#9472;nvme0n1p5 ntfs     C6501CCD501CC5D9                     08950c91-52b6-48fb-8e3f-1ede819f6e68 Image                           
&#9500;&#9472;nvme0n1p6 ntfs     30F8BDD8F8BD9C92                     89ac8a72-a74b-4d87-a201-c4d10eab3627 DELLSUPPORT                     
&#9500;&#9472;nvme0n1p7 ext4     9d6b3135-86c2-4f36-8607-242567e093ae e3d7800c-7889-4c82-927d-48d916504e3e                                 
&#9500;&#9472;nvme0n1p8 ext4     86f15481-2011-4a56-b693-1900aafbc4b6 8aed983b-2315-4d43-a6a9-4b8efc424689                                 
&#9492;&#9472;nvme0n1p9 swap     a8d846b6-8718-48d6-9963-144f77d09dba 70b45b60-b322-4b58-a29b-f812b980901b                                 

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2023-08-30.1/crash]  10.6G   0% /var/crash
/dev/disk/by-label/writable[/install-logs-2023-08-30.1/log]    10.6G   0% /var/log
/dev/nvme0n1p1                                                133.1M  44% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3                                                 37.5G  59% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4                                                300.9M  70% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5                                                 74.9M 100% /mnt/boot-sav/nvme0n1p5
/dev/nvme0n1p6                                                498.1M  67% /mnt/boot-sav/nvme0n1p6
/dev/nvme0n1p7                                                 81.3G   9% /mnt/boot-sav/nvme0n1p7
/dev/nvme0n1p8                                                216.9G   0% /mnt/boot-sav/nvme0n1p8
/dev/sda1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________


======================== nvme0n1p7/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p7 during installation
UUID=9d6b3135-86c2-4f36-8607-242567e093ae /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=4AD8-634A  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme0n1p8 during installation
UUID=86f15481-2011-4a56-b693-1900aafbc4b6 /home           ext4    defaults        0       2
# swap was on /dev/nvme0n1p9 during installation
UUID=a8d846b6-8718-48d6-9963-144f77d09dba none            swap    sw              0       0

==================== nvme0n1p7/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

================= nvme0n1p7: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
 163.346675873 = 175.392157696  boot/vmlinuz                                   2
 163.346675873 = 175.392157696  boot/vmlinuz-6.2.0-26-generic                  2
 162.877925873 = 174.888841216  boot/initrd.img                                2
 162.877925873 = 174.888841216  boot/initrd.img-6.2.0-26-generic               2
 162.877925873 = 174.888841216  boot/initrd.img.old                            2

=================== nvme0n1p7: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17 05:35 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi of
nvme0n1p7,
using the following options:  nvme0n1p1/boot/efi
Additional repair would be performed: unhide-bootmenu-10s use-standard-efi-file

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your UEFI firmware boot on the Ubuntu 22.04.3 LTS entry (nvme0n1p1/efi/****/grub****.efi (**** will be updated in the final message) file) !
If your computer reboots directly into Windows, try to change the boot order in your UEFI firmware.
If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\****\grub****.efi (**** will be updated in the final message)


```

---

### Post by oldfred on 2023-08-31
I do not really see anything in report, perhaps someone else will.

Did Windows do any updates or update Dell's UEFI when you booted into Windows? 
That can reset settings that you have to change or originally changed.
Do not turn on legacy. I thought Dell's this new did not even have that mode. My Dell 5310 with 11th Gen Intel does not have Legacy/CSM/BIOS boot mode. But you may have a setting beyond UEFI Secure Boot that locks ESP. Or Windows turns on bitlocker or Windows fast startup.

Recheck settings both UEFI & Windows.

Then try reinstall of grub  & newest kernel from Boot-Repair's advanced mode. Be sure to boot in UEFI boot mode.

---

### Post by makitso on 2023-08-31
As an experiment, I ran boot-repair and let it attempt to fix the problem.  It failed with this error:

Error: NVram is locked (Ubuntu not found in efibootmgr).

---

### Post by makitso on 2023-08-31
OK, got it to boot.  I reset the bios to factory default and turned on Secure Boot.

---

