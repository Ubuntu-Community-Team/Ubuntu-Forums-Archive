---
title: "GUI upgrraded failed to blank screen then BIOS.  Help is appreciated."
date: 2024-09-10
forum: Installation &amp; Upgrades
---

### Post by rickybobby135 on 2024-09-10
Sir/Ma'am,

I am a fan of linux and open source.  First major upgrade on my desktop and the cpu failed to boot and went to the bios screen.  I used a thumbdrive from when I installed linux to try to get back on forums.  Below is the output and I am trying to get whatever failed to be reuploaded to my hardrive to not loose all the files stored on the hard drive.  Thanks in advance for the support.

V/r,

Rob

boot-repair-4ppa2081                                              [20240910_0442]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => libparted MBR boot code is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.

nvme0n1p1: _____________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

nvme0n1p4: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

nvme0n1p5: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, nvme0n1p5 
                       starts at sector 123045888. But according to the info 
                       from fdisk, nvme0n1p5 starts at sector 293027840.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda: ___________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sdd: /dev/sdd already mounted or mount point busy.


================================ 1 OS detected =================================

OS#1 (linux):   Ubuntu 24.04.1 LTS on nvme0n1p2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Navi 10 [Radeon RX 5600 OEM/5600 XT / 5700/5700 XT] from Advanced Micro Devices, Inc. [AMD/ATI]
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.3 LTS, focal, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: F51(5.14) from American Megatrends Inc.
The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).


85fa9d77b929ec4231aba29476574eb6   nvme0n1p5/BOOT/fbx64.efi
469e608783843a701d172242f016c79c   nvme0n1p5/BOOT/mmx64.efi
fa1bf1a7f90a852abe0bdbd089b7f1b0   nvme0n1p5/ubuntu/grubx64.efi
469e608783843a701d172242f016c79c   nvme0n1p5/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p5/ubuntu/shimx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p5/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
sdc    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p2    : is-os,    64, apt-get,    grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
nvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme0n1p5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdc1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

nvme0n1p2    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4
nvme0n1p5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, vfat
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4
sdc1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4

Partitions info (3/3): _________________________________________________________

nvme0n1p2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p4    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
sdb1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb
sdc1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 953.89 GiB, 1024209543168 bytes, 2000409264 sectors
Disk identifier: 88ED3BBC-E70D-408A-9067-9B1D38D11774
             Start        End    Sectors   Size Type
nvme0n1p1      2048   64452607   64450560  30.8G Linux swap
nvme0n1p2  64452608  293027839  228575232   109G Linux filesystem
nvme0n1p4 294981632 2000408575 1705426944 813.2G Linux filesystem
nvme0n1p5 293027840  294981631    1953792   954M Microsoft basic data
Partition table entries are not in disk order.
Disk sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk sdb: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0x54ad6f9b
     Boot Start       End   Sectors   Size Id Type
sdb1        2048 976773119 976771072 465.8G 83 Linux
Disk sdc: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: BC012324-481A-4EC4-8701-8CE3E4D10A78
     Start       End   Sectors   Size Type
sdc1   2048 976773119 976771072 465.8G Linux filesystem
Disk sdd: 7.56 GiB, 8103395328 bytes, 15826944 sectors
Disk identifier: 0x2cf4ba3a
     Boot   Start      End Sectors  Size Id Type
sdd1  *          0  5999871 5999872  2.9G  0 Empty
sdd2       5271500  5279499    8000  3.9M ef EFI (FAT-12/16/32)
sdd3       6000640 15826943 9826304  4.7G 83 Linux

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:512:loop:ATA ST3500312CS:;
1:0.00B:500GB:500GB:ext4::;
sdb:500GB:scsi:512:512:msdos:ATA ST3500312CS:;
1:1049kB:500GB:500GB:ext4::;
sdc:500GB:scsi:512:512:gpt:ATA WDC WD5000AVDS-6:;
1:1049kB:500GB:500GB:ext4::;
sdd:8103MB:scsi:512:512:unknown:JetFlash Transcend 8GB:;
nvme0n1:1024GB:nvme:512:512:gpt:ADATA SX8200PNP:;
1:1049kB:33.0GB:33.0GB:linux-swap(v1)::swap;
2:33.0GB:150GB:117GB:ext4::;
5:150GB:151GB:1000MB:fat32::msftdata;
4:151GB:1024GB:873GB:ext4::;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda         ext4     79feb5d3-536c-4d9c-b27c-5716de245383                                      500G3                    
sdb                                                                                                                     
&#9492;&#9472;sdb1      ext4     54542146-d932-4d5b-94ce-8ead1cd17b38 54ad6f9b-01                          500GB Videos             
sdc                                                                                                                     
&#9492;&#9472;sdc1      ext4     7071f933-3ac5-49cc-b2af-7e2c4bccbf99 1116e0c8-babb-494a-9faa-c1c33d3455f1 wd500                    
sdd         iso9660  2021-08-19-11-03-38-00                                                    Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdd1      iso9660  2021-08-19-11-03-38-00               2cf4ba3a-01                          Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdd2      vfat     54C5-9C6C                            2cf4ba3a-02                                                   
&#9492;&#9472;sdd3      ext4     c147f8fd-a3b5-46fa-9e98-b5b0f9e32e28 2cf4ba3a-03                          writable                 
nvme0n1                                                                                                                 
&#9500;&#9472;nvme0n1p1 swap     f15332f2-dfd9-4deb-ae76-6a06db72a884 37b26784-4166-40f8-86be-ad449e4089df                          
&#9500;&#9472;nvme0n1p2 ext4     ef90ba2b-0c6f-4d05-9dac-8a63bf83d033 3a4b5a22-890f-48f4-a03b-88db9ff7bbc9                          
&#9500;&#9472;nvme0n1p4 ext4     e022b309-6b89-4101-812b-eb0fb2f3125d bc19b442-4130-42e1-9afa-00313edd0276                          
&#9492;&#9472;nvme0n1p5 vfat     3100-CFB7                            184c2182-f3ca-48c4-bbd8-c79f6ff4eb54                          

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/nvme0n1p2                                                 59.1G  41% /mnt/boot-sav/nvme0n1p2
/dev/nvme0n1p4                                                523.8G  29% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5                                                946.9M   1% /mnt/boot-sav/nvme0n1p5
/dev/sdb1                                                      19.3M  95% /mnt/boot-sav/sdb1
/dev/sdc1                                                     163.5G  59% /mnt/boot-sav/sdc1
/dev/sdd1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p2                                                ext4            rw,relatime
/dev/nvme0n1p4                                                ext4            rw,relatime
/dev/nvme0n1p5                                                vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdb1                                                     ext4            rw,relatime
/dev/sdc1                                                     ext4            rw,relatime
/dev/sdd1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048

=================== nvme0n1p2/boot/grub/grub.cfg (filtered) ====================

Ubuntu   ef90ba2b-0c6f-4d05-9dac-8a63bf83d033
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p2/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p2 during installation
UUID=ef90ba2b-0c6f-4d05-9dac-8a63bf83d033 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p3 during installation
UUID=3100-CFB7  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme0n1p4 during installation
UUID=e022b309-6b89-4101-812b-eb0fb2f3125d /home           ext4    defaults        0       2
# swap was on /dev/nvme0n1p1 during installation
UUID=f15332f2-dfd9-4deb-ae76-6a06db72a884 none            swap    sw              0       0

==================== nvme0n1p2/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

================= nvme0n1p2: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
  77.858181000 = 83.599585280   boot/grub/grub.cfg                             1
  60.233394623 = 64.675115008   boot/vmlinuz                                   2
  66.163082123 = 71.042068480   boot/vmlinuz-5.15.0-119-generic                2
  92.209957123 = 99.009687552   boot/vmlinuz-6.5.0-45-generic                  2
  44.444332123 = 47.721738240   boot/vmlinuz-6.8.0-40-generic                  2
  60.233394623 = 64.675115008   boot/vmlinuz-6.8.0-41-generic                  2
  66.163082123 = 71.042068480   boot/vmlinuz.old                               2
  84.374019623 = 90.595913728   boot/initrd.img-5.15.0-119-generic             9
  65.116207123 = 69.917995008   boot/initrd.img-6.5.0-45-generic               9
  89.560234070 = 96.164569088   boot/initrd.img-6.8.0-40-generic               3
  89.608394623 = 96.216281088   boot/initrd.img-6.8.0-41-generic               3
  84.374019623 = 90.595913728   boot/initrd.img.old                            9

=================== nvme0n1p2: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18133 Apr  4 10:12 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4 10:12 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4 10:12 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4 10:12 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4 10:12 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4 10:12 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5 11:36 35_fwupd
-rwxr-xr-x 1 root root   214 Jul 31  2020 40_custom
-rwxr-xr-x 1 root root   215 Apr 15  2022 41_custom

=================== nvme0n1p5/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid ef90ba2b-0c6f-4d05-9dac-8a63bf83d033 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sdd




Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub2 of
nvme0n1p2 into the MBR of nvme0n1.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s

Blockers in case of suggested repair: __________________________________________

 GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your BIOS boot on nvme0n1 (ADATA SX8200PNP) disk!

The boot files of [nvme0n1p2 (end>100GB)] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

---

