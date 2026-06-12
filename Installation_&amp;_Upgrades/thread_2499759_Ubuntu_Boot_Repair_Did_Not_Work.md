---
title: "Ubuntu Boot Repair Did Not Work"
date: 2024-08-09
forum: Installation &amp; Upgrades
---

### Post by thinmint99 on 2024-08-09
Ubuntu just boots into GRUB. Ran the Boot-Repair tool to no effect. 

At the time I started having problems, I was provided a prompt in Ubuntu where it said I had to restart to install an update - white rectangular box prompt at the top of the screen (I didn't pay attention to what it was). Ubuntu never rebooted successfully after that.

Can anyone make heads/tails of this Boot Repair Summary for me?

Thanks in advance



boot-repair-4ppa2079                                              [20240809_1652]


============================= Boot Repair Summary ==============================


GPT PMBR size mismatch (31293406 != 31293439) will be corrected by write.


Recommended repair: ____________________________________________________________


The default repair of the Boot-Repair utility will purge (in order to fix packages) and reinstall the grub2 of
sda2 into the MBR of sda.
Grub-efi will not be selected by default because no ESP detected outside live discs.
Additional repair will be performed: unhide-bootmenu-10s




chroot /mnt/boot-sav/sda2 apt-get -y update
Running in chroot, ignoring command 'start'
Purge the GRUB of /dev/sda2
grub-pc available


The following packages were automatically installed and are no longer required:
linux-modules-6.8.0-39-generic linux-modules-extra-6.8.0-39-generic
linux-tools-6.8.0-39 linux-tools-6.8.0-39-generic
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
grub-common grub-gfxpayload-lists grub-pc-bin grub2-common os-prober
Suggested packages:
multiboot-doc grub-emu mtools xorriso desktop-base
The following NEW packages will be installed:
grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common os-prober
0 upgraded, 6 newly installed, 0 to remove and 24 not upgraded.
DEBCHECK debOK, grub-pc
DEBCHECK debOK
Then type: sudo chroot "/mnt/boot-sav/sda2" dpkg --configure -ansudo chroot "/mnt/boot-sav/sda2" apt-get install -fynsudo chroot "/mnt/boot-sav/sda2" apt-get install -y grub-pc


Unhide GRUB boot menu in sda2/etc/default/grub


====================== Reinstall the grub-pc of /dev/sda2 ======================


chroot /mnt/boot-sav/sda2 grub-install --version
grub-install (GRUB) 2.12-1ubuntu7


==> Reinstall the GRUB of /dev/sda2 into the MBR of /dev/sda


chroot /mnt/boot-sav/sda2 grub-install /dev/sda
Installing for i386-pc platform.
Installation finished. No error reported.


chroot /mnt/boot-sav/sda2 update-grub
Sourcing file `/etc/default/grub'
Found linux image: /boot/vmlinuz-6.8.0-40-generic
Found initrd image: /boot/initrd.img-6.8.0-40-generic
Adding boot menu entry for UEFI Firmware Settings ...


Unhide GRUB boot menu in sda2/boot/grub/grub.cfg


Boot successfully repaired.


You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (DELL PERC H730 Mini) disk!


The boot files of [sda2 (end>100GB)] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


============================ Boot Info After Repair ============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive for core.img. core.img is at this location and 
    looks for (,gpt2)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_gpt biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.
 => Syslinux GPTMBR (3.74-4.03) is installed in the MBR of /dev/sdc.


sda1: __________________________________________________________________________


    File system:       BIOS Boot partition
    Boot sector type:  Grub2's core.img
    Boot sector info: 


sda2: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img


sdb1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 6.04
    Boot sector info:  Syslinux looks at sector 30912 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/boot/bootx64.efi /efi/boot/grubx64.efi 
                       /efi/boot/mmx64.efi /ldlinux.sys


sdc1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Syslinux 3.53-3.86
    Boot sector info:  No evidence that this is realy a Syslinux boot 
                       sector. According to the info in the boot sector, sdc1 
                       starts at sector 0. But according to the info from 
                       fdisk, sdc1 starts at sector 64.
    Operating System:  
    Boot files:        /syslinux.cfg /efi/VMware/mboot64.efi 
                       /efi/VMware/safeboot64.efi /ldlinux.sys


sdc5: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc5 starts at sector 208896.
    Operating System:  
    Boot files:        


sdc6: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdc6 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc6 starts at sector 2308096.
    Operating System:  
    Boot files:        


sdc7: __________________________________________________________________________


    File system:       VMFS_volume_member
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sdc7: unknown filesystem type 'VMFS_volume_member'.




================================ 1 OS detected =================================


OS#1:   Ubuntu 24.04 LTS on sda2


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: G200eR2 from Matrox Electronics Systems Ltd.
Live-session OS is Linuxmint 64-bit (Linux Mint 21.2, victoria, x86_64)


===================================== UEFI =====================================


BIOS/UEFI firmware: 2.4.3(2.4) from Dell Inc.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).




d67e97859014e86f278efab33ba55d56   sdc1/VMware/mboot64.efi
5902f0b95112c5b506325d84a1e709fc   sdc1/VMware/safeboot64.efi
5902f0b95112c5b506325d84a1e709fc   sdc1/BOOT/BOOTx64.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : is-GPT,    hasBIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sdc    : is-GPT,    no-BIOSboot,    has---ESP,     liveusb,    not-mmc, no-os,    no-wind,    64 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda2    : is-os,    64, apt-get,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdc7    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far


Partitions info (2/3): _________________________________________________________


sda2    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc7    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


sda2    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sdc7    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc6    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc


fdisk -l (filtered): ___________________________________________________________


Disk sda: 3.64 TiB, 3998614552576 bytes, 7809794048 sectors
Disk identifier: 59712761-2AA4-4557-9BFC-E7529BD6DD9B
     Start        End    Sectors  Size Type
sda1   2048       4095       2048    1M BIOS boot
sda2   4096 7809791999 7809787904  3.6T Linux filesystem
Disk sdb: 57.3 GiB, 61524148224 bytes, 120164352 sectors
Disk identifier: 0x004dd308
     Boot Start       End   Sectors  Size Id Type
sdb1  *     2048 120164287 120162240 57.3G  c W95 FAT32 (LBA)
Disk sdc: 14.92 GiB, 16022241280 bytes, 31293440 sectors
Disk identifier: 4A540B6F-AE62-4715-ADEC-EECFFA636B38
       Start      End  Sectors  Size Type
sdc1       64   204863   204800  100M EFI System
sdc5   208896  2306047  2097152    1G Microsoft basic data
sdc6  2308096  4405247  2097152    1G Microsoft basic data
sdc7  4407296 31293406 26886111 12.8G unknown


parted -lm (filtered): _________________________________________________________


sda:3999GB:scsi:512:4096:gpt:DELL PERC H730 Mini:;
1:1049kB:2097kB:1049kB:::bios_grub;
2:2097kB:3999GB:3999GB:ext4::;
sdb:61.5GB:scsi:512:512:msdos: USB  SanDisk 3.2Gen1:;
1:1049kB:61.5GB:61.5GB:fat32::boot, lba;
sdc:16.0GB:scsi:512:512:gpt:DELL IDSDM:;
1:32.8kB:105MB:105MB:fat16:BOOT:boot, esp;
5:107MB:1181MB:1074MB:fat16:BOOTBANK1:msftdata;
6:1182MB:2255MB:1074MB:fat16:BOOTBANK2:msftdata;
7:2257MB:16.0GB:13.8GB::LOCKER:;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE             UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                             
&#9500;&#9472;sda1                                                         907d6077-9eb6-4b21-a677-c9421690958a             
&#9492;&#9472;sda2 ext4               d9c67e4d-da05-42d7-8572-7ada4d0fc26b e33e577b-3e7a-41ed-ae12-21011b639411             
sdb                                                                                                             
&#9492;&#9472;sdb1 vfat               11F9-3411                            004dd308-01                          BOOT-REPAIR 
sdc                                                                                                             
&#9500;&#9472;sdc1 vfat               532A-4F19                            0b914813-8731-40e1-b6cc-0179893ee01d             BOOT
&#9500;&#9472;sdc5 vfat               532A-4F19                            7a675fca-82ab-40df-a370-14b362349d57             BOOTBANK1
&#9500;&#9472;sdc6 vfat               532A-4F1A                            cccc29b5-a0ac-448f-8cb0-635bd3f5a37d             BOOTBANK2
&#9492;&#9472;sdc7 VMFS_volume_member                                      b343c277-d8aa-4248-b1d4-e38fbd961722             LOCKER


Mount points (filtered): _______________________________________________________


             Avail Use% Mounted on
/dev/sda2     3.4T   1% /mnt/boot-sav/sda2
/dev/sdb1    54.8G   4% /cdrom
/dev/sdc1    99.3M   1% /mnt/boot-sav/sdc1
/dev/sdc5   813.9M  21% /media/mint/532A-4F19
/dev/sdc6   814.8M  20% /media/mint/532A-4F1A


Mount options (filtered): ______________________________________________________


/dev/sda2   ext4            rw,relatime
/dev/sdb1   vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdc1   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdc5   vfat            rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro
/dev/sdc6   vfat            rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro


====================== sda2/boot/grub/grub.cfg (filtered) ======================


Ubuntu   d9c67e4d-da05-42d7-8572-7ada4d0fc26b
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


========================== sda2/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during curtin installation
/dev/disk/by-uuid/d9c67e4d-da05-42d7-8572-7ada4d0fc26b / ext4 defaults 0 1
/swap.img    none    swap    sw    0    0


======================= sda2/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


==================== sda2: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
 932.168315887 = 1000.908107776 boot/grub/i386-pc/core.img                     1
2775.570556641 = 2980.246192128 boot/vmlinuz                                   1
2775.570556641 = 2980.246192128 boot/vmlinuz-6.8.0-40-generic                  1
2775.570556641 = 2980.246192128 boot/vmlinuz.old                               1
2775.625644684 = 2980.305342464 boot/initrd.img                                2
2775.625644684 = 2980.305342464 boot/initrd.img-6.8.0-40-generic               2
2775.625644684 = 2980.305342464 boot/initrd.img.old                            2


===================== sda2: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 18133 Apr  4 10:12 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4 10:12 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4 10:12 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4 10:12 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4 10:12 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4 10:12 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Apr  4 10:12 40_custom
-rwxr-xr-x 1 root root   215 Apr  4 10:12 41_custom


====================== sdb1/boot/grub/grub.cfg (filtered) ======================


Start Boot-Repair-Disk 64-bit
Start Boot-Repair-Disk 64-bit (compatibility mode)
UEFI Firmware Settings
Test memory


========================= sdb1/syslinux.cfg (filtered) =========================


DEFAULT loadconfig


LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/


==================== sdb1: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1


================== sdb1: Location of files loaded by Syslinux ==================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1


========================= sdc1/syslinux.cfg (filtered) =========================


default safeboot.c32 -S 1
nohalt 1


================== sdc1: Location of files loaded by Syslinux ==================


           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             mboot.c32                                      1
            ?? = ??             safeboot.c32                                   1


=============== sdc1: Version of COM32(R) files used by Syslinux ===============


 mboot.c32                          :  COM32R module (v4.xx)
 safeboot.c32                       :  COM32R module (v4.xx)


======================== Unknown MBRs/Boot Sectors/etc =========================


Unknown GPT Partiton Type
39eab24e55789047a79efae495e21f8d
Unknown BootLoader on sdc5


Unknown BootLoader on sdc6


*******.us ko ()

---

### Post by yancek on 2024-08-09
Your sda drive on which you have Ubuntu is a GPT drive and generally, installing on a GPT drive will be in UEFI mode but you selected to install in Legacy/CSM mode?  Do you have Legacy/CSM option in your BIOS firmware enabled?  Is this a new install?  If so and you don't have any data, I would suggest that you boot and install in UEfI mode.  If you have data, back it up.  You will sometimes see a message that a reboot is necessary after an update and it is best to pay attention to what it says sine no one here is likely to know.

So what exactly happens now when you try to boot?  Is it the same as before you tried the boot repair?

---

