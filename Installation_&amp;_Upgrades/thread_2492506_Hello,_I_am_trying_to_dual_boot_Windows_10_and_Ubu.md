---
title: "Hello, I am trying to dual boot Windows 10 and Ubuntu on two seperate SSDS (HELP)"
date: 2023-11-13
forum: Installation &amp; Upgrades
---

### Post by brankonius on 2023-11-13
So at the moment I am following a course on Theodinproject for learning to program/code.  It recommended me to do a dual boot with Linux.  I followed the guide to a tee. It's listed here. [https://www.theodinproject.com/lessons/foundations-installations](https://www.theodinproject.com/lessons/foundations-installations). 

Everything was going smoothly, before I started the process I shrink 100gb of space off in Disk management off an NVme Drive that doesn't have windows installed on it. I do use that nvme drive for installing and storing files/games, but I made sure to create new free space for the Ubuntu installation.  I created a /boot directory and even told the boat loader to install there in the install, after I created a root and home partition. The root was granted 70gigs of disk space and the home took what was leftover. Then that was the end of the install, it told me to reboot, remove install media, then press enter. I was expected to see a boot menu for Ubuntu and windows but I got what I have linked below. 

**TL;DR  **Now the problem at hand is here [https://i.imgur.com/Dcjc5gz.jpg](https://i.imgur.com/Dcjc5gz.jpg)  I have no idea why it's leading me here.  I've also done the command "ls" and I don't even see my drive that I installed Ubuntu on. I only see the disk and partitions from my windows SSD.  Any help please?


Also I did boot-repair and it did not fix the grub interface on boot. I still haven't booted directly into ubuntu once without the USB that I used to install. I used the installation media to create a live environment for boot-repair, after running get this error [https://media.discordapp.net/attachments/690588805648089169/1173721693471113377/image.png?ex=6564fc82&is=65528782&hm=09d5e5220c3108e31c02c7d95afc29b28e0241b68876b1745d091fc73717a66b&=](https://media.discordapp.net/attachments/690588805648089169/1173721693471113377/image.png?ex=6564fc82&is=65528782&hm=09d5e5220c3108e31c02c7d95afc29b28e0241b68876b1745d091fc73717a66b&=)

[U][B]This is also the log file generated after running boot-repair.


[/B][/U]If anyone wants to dm me on discord and help me out faster do so by @bbranko on discord


```
''' boot-repair-4ppa2056                                              [20231113_2249]

============================= Boot Repair Summary ==============================





modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic
ls: cannot access '/sys/firmware/efi/vars': No such file or directory

=================== /boot detected. Please check the options.

Repair blocked: ________________________________________________________________
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
nvme0n1p3,
using the following options:  nvme0n1p2/boot sda2/boot/efi
Additional repair will be performed:  unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


rm /mnt/boot-sav/sda2/efi/Boot/bootx64.efi
mv /mnt/boot-sav/sda2/efi/Boot/bkpbootx64.efi /mnt/boot-sav/sda2/efi/Boot/bootx64.efi
Mount nvme0n1p2 on /mnt/boot-sav/nvme0n1p3/boot
Mount sda2 on /mnt/boot-sav/nvme0n1p3/boot/efi

===================== Reinstall the grub-efi of nvme0n1p3 ======================

chroot /mnt/boot-sav/nvme0n1p3 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7.2
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.2.0-26-generic
chroot /mnt/boot-sav/nvme0n1p3 modprobe efivars

chroot /mnt/boot-sav/nvme0n1p3 efibootmgr -v before grub install
EFI variables are not supported on this system.


chroot /mnt/boot-sav/nvme0n1p3 uname -r
6.2.0-26-generic

chroot /mnt/boot-sav/nvme0n1p3 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/sda2
mv /mnt/boot-sav/nvme0n1p3/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/nvme0n1p3/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/nvme0n1p3/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/nvme0n1p3/boot/efi/EFI/Boot/bootx64.efi

chroot /mnt/boot-sav/nvme0n1p3 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/nvme0n1p3 efibootmgr -v after grub install
EFI variables are not supported on this system.

Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

chroot /mnt/boot-sav/nvme0n1p3 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.2.0-36-generic
Found initrd image: /boot/initrd.img-6.2.0-36-generic
Found linux image: /boot/vmlinuz-6.2.0-26-generic
Found initrd image: /boot/initrd.img-6.2.0-26-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi

An error occurred during the repair.
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

Locked-NVram detected.


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => Windows 7/8/10/11/2012 is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.

nvme0n1p1: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p2: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

nvme0n1p3: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04.3 LTS
    Boot files:        /etc/fstab /etc/default/grub

nvme0n1p4: _____________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

nvme0n1p5: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10 or 11
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


================================ 2 OS detected =================================

OS#1:   Ubuntu 22.04.3 LTS on nvme0n1p3
OS#2:   Windows 10 or 11 on sda4

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GP102 [GeForce GTX 1080 Ti] Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller from NVIDIA Corporation Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.3 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: F7(4.6) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0008
Timeout: 1 seconds
BootOrder: 0005,0004,0000,0008,0007,0009
Boot0000* Windows Boot Manager    HD(2,GPT,39c4f5f2-90eb-4aed-bb1f-f1768b734919,0xe1800,0x31800)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...3................
Boot0004* ubuntu    HD(2,GPT,39c4f5f2-90eb-4aed-bb1f-f1768b734919,0xe1800,0x31800)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0005* ubuntu    HD(2,GPT,39c4f5f2-90eb-4aed-bb1f-f1768b734919,0xe1800,0x31800)/File(\EFI\UBUNTU\GRUBX64.EFI)
Boot0007* Samsung SSD 850 PRO 256GB    BBS(HD,,0x0)AMBO
Boot0008* UEFI: SanDisk    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/HD(1,GPT,dc2583d5-253b-4109-bab6-ebf5a7f916e2,0x800,0xe51f7c0)AMBO
Boot0009* SanDisk    BBS(HD,,0x0)AMBO

64349b3622c65f495a99dbf6102496e3   sda2/Boot/bkpbootx64.efi
64349b3622c65f495a99dbf6102496e3   sda2/Boot/bootx64.efi
a9c517741ac31962d7feb152948ad1ee   sda2/Boot/fbx64.efi
a660182adef313615746a665966d2ccc   sda2/Boot/mmx64.efi
a1da253696a304dce6b4668b70151c0e   sda2/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda2/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda2/ubuntu/shimx64.efi
8561c3e35368c746fd3cf8b9c0e71663   sda2/Microsoft/Boot/bootmgfw.efi
8f87a2fbaaa64d7b22150e1881b9eb87   sda2/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    grubenv-ok,    noupdategrub,    farbios
nvme0n1p3    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    no-grubenv,    update-grub,    farbios
nvme0n1p5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda4    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
sda5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p3    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sda2    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda4    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot
sda5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p2    : is---sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    no---boot,    fstab-has-goodBOOT,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1
nvme0n1p5    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 30858618-0DC1-48E7-9970-A8EBE1D8C96C
               Start        End    Sectors   Size Type
nvme0n1p1       2048 1748721663 1748719616 833.9G Microsoft basic data
nvme0n1p2 1748721664 1749405695     684032   334M Linux filesystem
nvme0n1p3 1749405696 1886124031  136718336  65.2G Linux filesystem
nvme0n1p4 1945524224 1953523711    7999488   3.8G Linux swap
nvme0n1p5 1886124032 1945524223   59400192  28.3G Linux filesystem
Partition table entries are not in disk order.
Disk sda: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk identifier: 0C67BCC4-1065-4096-B05A-B35C26DD2D7C
          Start       End   Sectors   Size Type
sda1       2048    923647    921600   450M Windows recovery environment
sda2     923648   1126399    202752    99M EFI System
sda3    1126400   1159167     32768    16M Microsoft reserved
sda4    1159168 498373181 497214014 237.1G Microsoft basic data
sda5  498374656 500115455   1740800   850M Windows recovery environment
Disk sdb: 114.56 GiB, 123010547712 bytes, 240254976 sectors
Disk identifier: CE638709-D081-4A8F-ACB0-610F69FEDA2A
      Start       End   Sectors   Size Type
sdb1   2048 240254911 240252864 114.6G Microsoft basic data

parted -lm (filtered): _________________________________________________________

sda:256GB:scsi:512:512:gpt:ATA Samsung SSD 850:;
1:1049kB:473MB:472MB:ntfs:Basic data partition:hidden, diag;
2:473MB:577MB:104MB:fat32:EFI system partition:boot, esp;
3:577MB:593MB:16.8MB::Microsoft reserved partition:msftres;
4:593MB:255GB:255GB:ntfs:Basic data partition:msftdata;
5:255GB:256GB:891MB:ntfs::hidden, diag;
sdb:123GB:scsi:512:512:gpt:SanDisk Ultra:;
1:1049kB:123GB:123GB:fat32:Main Data Partition:msftdata;
nvme0n1:1000GB:nvme:512:512:gpt:WDS100T3X0C-00SJG0:;
1:1049kB:895GB:895GB:ntfs:Basic data partition:msftdata;
2:895GB:896GB:350MB:ext4::;
3:896GB:966GB:70.0GB:ext4::;
5:966GB:996GB:30.4GB:ext4::;
4:996GB:1000GB:4096MB:linux-swap(v1)::swap;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                        
&#9500;&#9472;sda1      ntfs     5C6C03056C02DA22                     ec68fd08-3b9b-4941-a860-ba951a7f91f0 Recovery    Basic data partition
&#9500;&#9472;sda2      vfat     4C03-5787                            39c4f5f2-90eb-4aed-bb1f-f1768b734919             EFI system partition
&#9500;&#9472;sda3                                                    08c65eac-bd52-41e0-ad10-bf3617be7db7             Microsoft reserved partition
&#9500;&#9472;sda4      ntfs     50FC04CBFC04ACF2                     a1c6045e-8c52-4e0b-905b-4771efc84a53             Basic data partition
&#9492;&#9472;sda5      ntfs     02F487ECF487DFF1                     4e8a59d8-0720-483f-87c5-6726ad7495e0             
sdb                                                                                                        
&#9492;&#9472;sdb1      vfat     1112-0D6D                            dc2583d5-253b-4109-bab6-ebf5a7f916e2 UBUNTU 22_0 Main Data Partition
nvme0n1                                                                                                    
&#9500;&#9472;nvme0n1p1 ntfs     82E8B218E8B20A85                     8964c12a-4bc3-4c94-b062-d04d34c0d360 Games       Basic data partition
&#9500;&#9472;nvme0n1p2 ext4     198bf63f-830f-4114-9c5d-65e11924b16e bdf2ef01-d6fc-445d-8446-fe4c7990e932             
&#9500;&#9472;nvme0n1p3 ext4     4989d0a4-e325-4303-ba6b-c88e3c91fd27 c44e760e-fcb4-40f0-88db-d7e29638ed99             
&#9500;&#9472;nvme0n1p4 swap     13340588-f9de-47dc-a45b-b20bffb1d6e7 68312df1-b6f2-4016-9587-d564d4c48219             
&#9492;&#9472;nvme0n1p5 ext4     600bee78-0b60-4556-aa4a-a202a431cbe3 bf34aaca-1a2c-48d0-9b21-8f75cfd3f7d6             

Mount points (filtered): _______________________________________________________

                           Avail Use% Mounted on
/dev/nvme0n1p1            393.2G  53% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p2             83.8M  64% /mnt/boot-sav/nvme0n1p2
/dev/nvme0n1p3               48G  19% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p5             26.3G   0% /mnt/boot-sav/nvme0n1p5
/dev/sda1                 440.1M   2% /mnt/boot-sav/sda1
/dev/sda2                  62.4M  34% /mnt/boot-sav/sda2
/dev/sda4                 121.8G  49% /mnt/boot-sav/sda4
/dev/sda5                 271.4M  68% /mnt/boot-sav/sda5
/dev/sdb1                 109.8G   4% /cdrom

Mount options (filtered): ______________________________________________________


====================== nvme0n1p2/grub/grub.cfg (filtered) ======================

Ubuntu   4989d0a4-e325-4303-ba6b-c88e3c91fd27
Ubuntu, with Linux 6.2.0-36-generic   4989d0a4-e325-4303-ba6b-c88e3c91fd27
Ubuntu, with Linux 6.2.0-26-generic   4989d0a4-e325-4303-ba6b-c88e3c91fd27
Windows Boot Manager (on sda2)   osprober-efi-4C03-5787
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

================= nvme0n1p2: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
 834.180335999 = 895.694315520  grub/grub.cfg                                  1
 834.126129150 = 895.636111360  vmlinuz                                        1
 834.024539948 = 895.527030784  vmlinuz-6.2.0-26-generic                       1
 834.126129150 = 895.636111360  vmlinuz-6.2.0-36-generic                       1
 834.024539948 = 895.527030784  vmlinuz.old                                    1
 834.167964935 = 895.681032192  initrd.img                                     3
 834.097652435 = 895.605534720  initrd.img-6.2.0-26-generic                    3
 834.167964935 = 895.681032192  initrd.img-6.2.0-36-generic                    3
 834.097652435 = 895.605534720  initrd.img.old                                 3

======================== nvme0n1p3/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p3 during installation
UUID=4989d0a4-e325-4303-ba6b-c88e3c91fd27 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/nvme0n1p2 during installation
UUID=198bf63f-830f-4114-9c5d-65e11924b16e /boot           ext4    defaults        0       2
# /boot/efi was on /dev/sda2 during installation
UUID=4C03-5787  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme0n1p5 during installation
UUID=600bee78-0b60-4556-aa4a-a202a431cbe3 /home           ext4    defaults        0       2
# swap was on /dev/nvme0n1p4 during installation
UUID=13340588-f9de-47dc-a45b-b20bffb1d6e7 none            swap    sw              0       0

==================== nvme0n1p3/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

=================== nvme0n1p3: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Dec 18  2022 10_linux
-rwxr-xr-x 1 root root 43031 Dec 18  2022 10_linux_zfs
-rwxr-xr-x 1 root root 14387 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Dec 18  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Dec 18  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 May 17 05:35 35_fwupd
-rwxr-xr-x 1 root root   214 Dec 18  2022 40_custom
-rwxr-xr-x 1 root root   215 Dec 18  2022 41_custom

===================== sda2/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 198bf63f-830f-4114-9c5d-65e11924b16e root 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1'''
```

---

### Post by ubfan1 on 2023-11-13
What Ubuntu release did you install?  I am a bit confused by:
ls: cannot access '/sys/firmware/efi/vars': No such file or directory
The directory should be /sys/firmware/efi/efivars

My Ubuntu 22.04 desktop running in UEFI mode does not have an efivars module.

/boot ? not an EFI partition?  Typically not needed unless you have a reason (ancient BIOS, raid, encryption,...)

Different releases have different installers, some of which (22.04) will not properly make an EFI partition
on an external disk.  
With gpt disks, Windows must be installed in Uefi mode.  I don't know why boot-repair thinks a bios-grub partition
is needed unless you booted in legacy mode.

---

### Post by oldfred on 2023-11-13
With desktop best not to have separate /boot partition. Its just another partition to manage size of.
Also /home should be larger than / (root), but if new user probably better not to have separate /home either, until you know how much space you need.

Check UEFI settings for locking/protecting boot entries.
Some have reported turning on UEFI Secure boot, others turning it off.
Locked-NVram
[https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up](https://askubuntu.com/questions/1488426/trying-to-reinstall-grub-after-windows-update-messed-it-up) & 
[https://ubuntuforums.org/showthread.php?t=2491460](https://ubuntuforums.org/showthread.php?t=2491460)  &
[https://ubuntuforums.org/showthread.php?t=2482909](https://ubuntuforums.org/showthread.php?t=2482909)

---

### Post by brankonius on 2023-11-13
The release I installed was 22.04.3 LTS

What do you recommend I do then on the install screen. For example if I have 100g of free space and on the Installation type screen I choose something else how would allocate the rest of the space properly to install Ubuntu. Maybe I made a mistake there in a tutorial I was following. It told me when I get to that part of the install to go the something else option and partition drives there.[IMG]https://ubuntucommunity.s3-us-east-2.amazonaws.com/original/2X/4/46e9947d7b4ad3e96487d81cf61c327485d56b5a.png[/IMG]

---

### Post by yancek on 2023-11-14
Try turning off Secure Boot in the BIOS firmware and rebooting to test as suggested in post 3.  Have you set the windows drive (sda) to first boot order in the BIOS firmware and test booted?  The EFI partition is on that drive and has EFI files for both windows and Ubuntu .

> GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag)

The warning above would indicate that as you have a GPT drive, you need to install in EFI mode OR create a BIOS-Boot partition on that drive.  Setting sda to first boot may resolve the problem.  The UUID in the grub.cfg file on the sda2 EFI partition is pointing to the correct partition UUID on the SSD so I would try booting from sda as a first option.

---

### Post by oldfred on 2023-11-14
If Boot-Repair is asking for a bios_grub partition, that is required for BIOS/Legacy/CSM boot with gpt partitioned drives. You do not want BIOS boot and should always boot live installer for Ubuntu or any Windows repair flash drives in UEFI mode, for UEFI based repairs.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

---

