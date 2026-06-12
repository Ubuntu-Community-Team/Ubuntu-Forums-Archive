---
title: "Boot Repair error (NVram is locked)"
date: 2023-01-13
forum: Installation &amp; Upgrades
---

### Post by peternovak on 2023-01-13
Hi all,

I have previously restored the grub boot loader on my computer (a long time ago), but after replacing a broken motherboard yesterday I needed to do it again. Despite following the same process as last time, I got this error:

[URL="https://paste.ubuntu.com/p/6xJVyDYF8y/"]https://paste.ubuntu.com/p/6xJVyDYF8y/

[/URL]I noted there were a number of advanced options available in the Boot Repair settings, but not sure which (if any) should be appropriate to use, grateful for advice regarding how to restore my system.

Many thanks,

Peter


```
----------------

boot-repair-4ppa203                                              [20230113_1222]

============================= Boot Repair Summary ==============================






Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
nvme0n1p8,
using the following options:  nvme0n1p1/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


rm /mnt/boot-sav/nvme0n1p1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/nvme0n1p1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/nvme0n1p1/efi/Boot/bootx64.efi
nvme0n1p8 is 97 % full

** (org.gnome.Nautilus:21615): WARNING **: 12:22:43.619: Unable to get contents of the bookmarks file: Error opening file /root/.gtk-bookmarks: No such file or directory

** (org.gnome.Nautilus:21615): WARNING **: 12:22:43.620: Unable to get contents of the bookmarks file: Error opening file /root/.gtk-bookmarks: No such file or directory
Nautilus-Share-Message: 12:22:43.731: Called "net usershare info" but it failed: Failed to execute child process “net” (No such file or directory)
Nautilus-Share-Message: 12:24:53.484: Called "net usershare info" but it failed: Failed to execute child process “net” (No such file or directory)
Mount nvme0n1p1 on /mnt/boot-sav/nvme0n1p8/boot/efi

===================== Reinstall the grub-efi of nvme0n1p8 ======================

chroot /mnt/boot-sav/nvme0n1p8 grub-install --version
grub-install (GRUB) 2.06-2ubuntu7
modprobe: FATAL: Module efivars not found in directory /lib/modules/5.15.0-43-generic
chroot /mnt/boot-sav/nvme0n1p8 modprobe efivars

chroot /mnt/boot-sav/nvme0n1p8 efibootmgr -v before grub install
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0005,0000,0001,0002,0003,0004
Boot0000* Windows Boot Manager    HD(1,GPT,4a30f3d5-52ac-4b31-b129-01e416166a1a,0x800,0xfa000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0............. ...
Boot0001* Diskette Drive    BBS(Floppy,Diskette Drive,0x0)..BO
Boot0002* USB Storage Device    BBS(USB,General USB Flash Disk 1.00,0x0)..BO
Boot0003* CD/DVD/CD-RW Drive    BBS(CDROM,CD/DVD/CD-RW Drive,0x0)..BO
Boot0004* Onboard NIC    BBS(Network,Onboard NIC,0x0)..BO
Boot0005* UEFI: General USB Flash Disk 1.00, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,GPT,9240a165-d190-4ab6-8a12-46dc207b42ee,0x71e8a0,0x2130)..BO

chroot /mnt/boot-sav/nvme0n1p8 uname -r
5.15.0-43-generic

chroot /mnt/boot-sav/nvme0n1p8 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/nvme0n1p1
mv /mnt/boot-sav/nvme0n1p8/boot/efi/efi/Boot/bootx64.efi /mnt/boot-sav/nvme0n1p8/boot/efi/efi/Boot/bkpbootx64.efi
cp /mnt/boot-sav/nvme0n1p8/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/nvme0n1p8/boot/efi/efi/Boot/bootx64.efi

chroot /mnt/boot-sav/nvme0n1p8 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/nvme0n1p8 efibootmgr -v after grub install
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0005,0000,0001,0002,0003,0004
Boot0000* Windows Boot Manager    HD(1,GPT,4a30f3d5-52ac-4b31-b129-01e416166a1a,0x800,0xfa000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0............. ...
Boot0001* Diskette Drive    BBS(Floppy,Diskette Drive,0x0)..BO
Boot0002* USB Storage Device    BBS(USB,General USB Flash Disk 1.00,0x0)..BO
Boot0003* CD/DVD/CD-RW Drive    BBS(CDROM,CD/DVD/CD-RW Drive,0x0)..BO
Boot0004* Onboard NIC    BBS(Network,Onboard NIC,0x0)..BO
Boot0005* UEFI: General USB Flash Disk 1.00, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,GPT,9240a165-d190-4ab6-8a12-46dc207b42ee,0x71e8a0,0x2130)..BO
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

chroot /mnt/boot-sav/nvme0n1p8 update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.15.0-30-generic
Found initrd image: /boot/initrd.img-5.15.0-30-generic
Found linux image: /boot/vmlinuz-5.13.0-27-generic
Found initrd image: /boot/initrd.img-5.13.0-27-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi

Unhide GRUB boot menu in nvme0n1p8/boot/grub/grub.cfg

An error occurred during the repair.
Error: NVram is locked (Ubuntu not found in efibootmgr). Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

Locked-NVram detected.


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/10/11/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bkpbootx64.efi /efi/Boot/bootx64.efi 
                       /efi/Boot/fbx64.efi /efi/Boot/mmx64.efi 
                       /efi/PEBoot/bootx64.efi /efi/ubuntu/fwupdx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg 
                       /efi/dell/SOS/bootmgfw.efi /efi/dell/SOS/bootmgr.efi 
                       /efi/dell/SOS/bootx64.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi /bootmgr /boot/bcd

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

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme0n1p8: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 22.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub

sda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sda: /dev/sda already mounted or mount point busy.


================================ 2 OS detected =================================

OS#1:   Ubuntu 22.04 LTS on nvme0n1p8
OS#2:   Windows 10 or 11 on nvme0n1p3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GP107M [GeForce GTX 1050 Ti Mobile] CoffeeLake-H GT2 [UHD Graphics 630] from NVIDIA Corporation Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.1 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.27.0(1.27) from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0005,0000,0001,0002,0003,0004
Boot0000* Windows Boot Manager    HD(1,GPT,4a30f3d5-52ac-4b31-b129-01e416166a1a,0x800,0xfa000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0............. ...
Boot0001* Diskette Drive    BBS(Floppy,Diskette Drive,0x0)..BO
Boot0002* USB Storage Device    BBS(USB,General USB Flash Disk 1.00,0x0)..BO
Boot0003* CD/DVD/CD-RW Drive    BBS(CDROM,CD/DVD/CD-RW Drive,0x0)..BO
Boot0004* Onboard NIC    BBS(Network,Onboard NIC,0x0)..BO
Boot0005* UEFI: General USB Flash Disk 1.00, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/HD(2,GPT,9240a165-d190-4ab6-8a12-46dc207b42ee,0x71e8a0,0x2130)..BO

728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/Boot/bkpbootx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/Boot/bootx64.efi
c152ec201c37b6e97bbc2207e49d1271   nvme0n1p1/Boot/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   nvme0n1p1/Boot/mmx64.efi
dd719fddad19ab643c555eb8d7855a10   nvme0n1p1/PEBoot/bootx64.efi
2fe4ec2fece5365a314456d043f6ed93   nvme0n1p1/ubuntu/fwupdx64.efi
f62c28d9b477b6a1a7b1c991b2b6637d   nvme0n1p1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   nvme0n1p1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   nvme0n1p1/ubuntu/shimx64.efi
e87c4f299e44cf4153ad321c6fc7dabc   nvme0n1p1/dell/SOS/bootmgfw.efi
ac84bbacadaa85317812273ac07cda2f   nvme0n1p1/dell/SOS/bootmgr.efi
e87c4f299e44cf4153ad321c6fc7dabc   nvme0n1p1/dell/SOS/bootx64.efi
20ac8dde00311476f3755604eb0e545a   nvme0n1p1/Microsoft/Boot/bootmgfw.efi
27d382c5fc21df6f4a75baed05aa1d9d   nvme0n1p1/Microsoft/Boot/bootmgr.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p7    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios
nvme0n1p8    : is-os,    64, apt-get,    signed grub-pc grub-efi ,    grub2,    grub-install,    grubenv-ok,    update-grub,    farbios

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot
nvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
nvme0n1p5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
nvme0n1p6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
nvme0n1p7    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
nvme0n1p8    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p6    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p7    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p8    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme0n1

fdisk -l (filtered): ___________________________________________________________

Disk nvme0n1: 1.86 TiB, 2048408248320 bytes, 4000797360 sectors
Disk identifier: 0D22E1F7-BB9A-45EA-B0C8-4DF27206A45C
               Start        End    Sectors   Size Type
nvme0n1p1       2048    1026047    1024000   500M EFI System
nvme0n1p2    1026048    1288191     262144   128M Microsoft reserved
nvme0n1p3    1288192  796954623  795666432 379.4G Microsoft basic data
nvme0n1p4  796954624 2435354623 1638400000 781.3G Microsoft basic data
nvme0n1p5 3971354624 3973382143    2027520   990M Windows recovery environment
nvme0n1p6 3973382144 3998386175   25004032  11.9G Windows recovery environment
nvme0n1p7 3998386176 4000778239    2392064   1.1G Windows recovery environment
nvme0n1p8 2435354624 3971354623 1536000000 732.4G Linux filesystem
Partition table entries are not in disk order.
Disk sda: 3.73 GiB, 4009754624 bytes, 7831552 sectors
Disk identifier: 9240A165-D190-4AB6-8A10-46DC207B42EE
        Start     End Sectors  Size Type
sda1       64 7465119 7465056  3.6G Microsoft basic data
sda2  7465120 7473615    8496  4.1M EFI System
sda3  7473616 7474215     600  300K Microsoft basic data
sda4  7475200 7831488  356289  174M Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:4010MB:scsi:512:512:gpt:General USB Flash Disk:;
1:32.8kB:3822MB:3822MB::ISO9660:hidden, msftdata;
2:3822MB:3826MB:4350kB::Appended2:boot, esp;
3:3826MB:3827MB:307kB::Gap1:hidden, msftdata;
4:3827MB:4010MB:182MB:ext4::;
nvme0n1:2048GB:nvme:512:512:gpt:KXG50PNV2T04 NVMe TOSHIBA 2048GB:;
1:1049kB:525MB:524MB:fat32:EFI system partition:boot, esp;
2:525MB:660MB:134MB::Microsoft reserved partition:msftres;
3:660MB:408GB:407GB:ntfs:Basic data partition:msftdata;
4:408GB:1247GB:839GB:ntfs:Basic data partition:msftdata;
8:1247GB:2033GB:786GB:ext4::;
5:2033GB:2034GB:1038MB:ntfs::hidden, diag;
6:2034GB:2047GB:12.8GB:ntfs::hidden, diag;
7:2047GB:2048GB:1225MB:ntfs::hidden, diag;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda         iso9660  2022-08-10-16-21-45-00                                                    Ubuntu 22.04.1 LTS amd64 
&#9500;&#9472;sda1      iso9660  2022-08-10-16-21-45-00               9240a165-d190-4ab6-8a11-46dc207b42ee Ubuntu 22.04.1 LTS amd64 ISO9660
&#9500;&#9472;sda2      vfat     8D6C-A9F8                            9240a165-d190-4ab6-8a12-46dc207b42ee ESP                      Appended2
&#9500;&#9472;sda3                                                    9240a165-d190-4ab6-8a13-46dc207b42ee                          Gap1
&#9492;&#9472;sda4      ext4     f39bb3b3-2ea4-4ec5-912c-bddfc17d2b7c 0814ba72-37e7-1f47-836a-ba0cbb640321 writable                 
nvme0n1                                                                                                                 
&#9500;&#9472;nvme0n1p1 vfat     BADD-6CA2                            4a30f3d5-52ac-4b31-b129-01e416166a1a ESP                      EFI system partition
&#9500;&#9472;nvme0n1p2                                               b814fa1c-90db-4cce-b080-c744013230ef                          Microsoft reserved partition
&#9500;&#9472;nvme0n1p3 ntfs     0CD6DE03D6DDED48                     87fb86c2-9c87-4013-a110-d48762c05abe OS                       Basic data partition
&#9500;&#9472;nvme0n1p4 ntfs     16DA5C0BDA5BE591                     f75ada5c-ccd5-4ad3-83ec-831340894fd9 Dropbox                  Basic data partition
&#9500;&#9472;nvme0n1p5 ntfs     D032DE4C32DE3766                     e3c8b591-14f1-48eb-9bfc-3e864287a90d WINRETOOLS               
&#9500;&#9472;nvme0n1p6 ntfs     06ECDE85ECDE6E85                     e109ff79-3b57-413f-9ea7-8151bb06ebf6 Image                    
&#9500;&#9472;nvme0n1p7 ntfs     6C3EDED93EDE9C00                     0459d170-4365-45ed-b585-d6da3a0092a4 DELLSUPPORT              
&#9492;&#9472;nvme0n1p8 ext4     2fa72e93-a39a-409e-9923-1d94c09e78d1 4aa8d9c5-0116-47ba-85a2-866ad08cac0c                          

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/disk/by-label/writable[/install-logs-2023-01-13.0/crash] 131.6M   2% /var/crash
/dev/disk/by-label/writable[/install-logs-2023-01-13.0/log]   131.6M   2% /var/log
/dev/nvme0n1p1                                                352.1M  29% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3                                                 18.6G  95% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4                                                  4.4G  99% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5                                                373.8M  62% /mnt/boot-sav/nvme0n1p5
/dev/nvme0n1p6                                                186.2M  98% /mnt/boot-sav/nvme0n1p6
/dev/nvme0n1p7                                                323.4M  72% /mnt/boot-sav/nvme0n1p7
/dev/nvme0n1p8                                                 25.2G  91% /mnt/boot-sav/nvme0n1p8
/dev/sda1                                                          0 100% /cdrom

Mount options (filtered): ______________________________________________________


=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 2fa72e93-a39a-409e-9923-1d94c09e78d1 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

=================== nvme0n1p8/boot/grub/grub.cfg (filtered) ====================

Ubuntu   2fa72e93-a39a-409e-9923-1d94c09e78d1
Ubuntu, with Linux 5.15.0-30-generic   2fa72e93-a39a-409e-9923-1d94c09e78d1
Ubuntu, with Linux 5.13.0-27-generic   2fa72e93-a39a-409e-9923-1d94c09e78d1
Windows Boot Manager (on nvme0n1p1)   osprober-efi-BADD-6CA2
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

======================== nvme0n1p8/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p8 during installation
UUID=2fa72e93-a39a-409e-9923-1d94c09e78d1 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=BADD-6CA2  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

==================== nvme0n1p8/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

================= nvme0n1p8: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1
1532.176319122 = 1645.161795584 boot/vmlinuz                                   2
1556.441165924 = 1671.215976448 boot/vmlinuz-5.13.0-27-generic                 2
1532.176319122 = 1645.161795584 boot/vmlinuz-5.15.0-30-generic                 2
1556.441165924 = 1671.215976448 boot/vmlinuz.old                               2
1550.856475830 = 1665.219461120 boot/initrd.img                                5
1553.626720428 = 1668.193988608 boot/initrd.img-5.13.0-27-generic              6
1550.856475830 = 1665.219461120 boot/initrd.img-5.15.0-30-generic              5
1553.626720428 = 1668.193988608 boot/initrd.img.old                            6

=================== nvme0n1p8: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18683 Apr 15  2022 10_linux
-rwxr-xr-x 1 root root 43031 Mar 30  2021 10_linux_zfs
-rwxr-xr-x 1 root root 14180 Apr 15  2022 20_linux_xen
-rwxr-xr-x 1 root root 13369 Apr 15  2022 30_os-prober
-rwxr-xr-x 1 root root  1372 Apr 15  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 19  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Jul 17  2018 40_custom
-rwxr-xr-x 1 root root   215 Apr 15  2022 41_custom
```

---

### Post by oldfred on 2023-01-13
If posting terminal output, please use code tags. Easy to add in Forum's advanced editor & # icon.
And with Boot-Repair, you just need to post the link.

Many posts with Locked NVram issue. Have not seen once known solution. Users often try various things & then it works.
This user posted the changes he made. May be an UEFI setting for security of some sort.
HP Zbook 15 NVRAM locked, install issues
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)

---

### Post by MAFoElffen on 2023-01-14
What brand, model, and type of computer?

---

### Post by VMC on 2023-01-14
1)Try resetting the CMOS jumpers to clear the NVRAM
2) If you can get to BIOS, try resetting to default.

---

### Post by arjunaoverdrive on 2023-05-01
For me, the solution was to create a USB-stick with the GPT (UEFI) option selected, not MBR, and reinstall Ubuntu. In this case, everything went fine -- I didn't get the message that the boot-loader cannot be installed, so I avoided getting this NVram is locked error when trying to install the boot loader manually.

---

### Post by marcakaplan7 on 2023-08-16
[COLOR=#000000]I hit this same (NVRAM-locked) error on my Lenovo Flex 5-14 (circa 2021-2022ish) laptop.[/COLOR]
[COLOR=#000000]I got into this situation after I deliberately booted into Windows, which I had not done for many months...[/COLOR]
[COLOR=#000000]Windows (still on V10) got the idea to do some Microsoft updates and Lenovo got the idea to do a BIOS update.[/COLOR]
[COLOR=#000000]Upo rebooting ... laptop kept coming up in Windows 10.[/COLOR]
[COLOR=#000000]Well I thought, this happened to me before also sometime many months ago.... so I'll just fix it with my (X)ubuntu bootable USB system and run boot-repair and all will be well again...[/COLOR]
[COLOR=#000000]But not so much.... Got the NVRAM-Locked error/warning from boot-repair....[/COLOR]
[COLOR=#000000]To make the story somewhat shorter ... ...[/COLOR]
[COLOR=#000000]Fiddled around with BIOS settings from the Lenovo BIOS screen (F2 early and often during boot!) Still no dice.[/COLOR]

[COLOR=#000000]My guess is that the BIOS update did something that prevents the linux command efibootmgr from updating the NVRAM entries.... Perhaps efibootmgr can be improved to deal with this... Almost certainly Microsoft knows how... But until there is an efibootmgr fix...[/COLOR]
[COLOR=#000000](I considered finding a back level BIOS.... But that seemed too uncertain and possibly problematic and I could still get caught in this situation in the future....[/COLOR]
[COLOR=#000000]Say next time I let Windows/Microsoft/Lenovo take control....)[/COLOR]

[COLOR=#000000]My[/COLOR][B] workaround is to:

[LIST]
[*]obtain a very short, stubby, USB stick.
[*]Format the stick with a small EFI/FAT partition (about 72MB is way more than enough) and just because, a second partition that can be used to import/export data. (Easily done with the ubuntu GUI "disks" app.)
[*]Then copy (rsync -avuP) all the files from the first (EFI) partition on my main internal drive to the will-be EFI 72MB partition on the USB stick. (Also use disks GUI to set the partition to EFI and bootable).
(But that doesn't quite work .... so also move the Microsoft directory and its files to an location .../xx/... on the stick (just in case, I suppose I could have deleted the Microsoft directory)
[*]Go back to the BIOS setup screen... Set the #1 boot preference to the new USB stick....
[*][B][I]Voila -- just leave the little, stubby, stick in the PC and the PC now is back to booting into Xubuntu.... my preferred OS!

[/I][/B]*(But subscribe to this thread in hope that someone will offer a "real" fix, rather than a workaround. )*
[*]
[/LIST]
[/B]

---

### Post by oldfred on 2023-08-16
Have not seen a for sure fix.
There is this one:
[https://ubuntuforums.org/showthread.php?t=2482555&page=2](https://ubuntuforums.org/showthread.php?t=2482555&page=2)

Seems to be a UEFI setting, so I might review if you have a new setting or changed back to original setting and it needs to be updated.

---

### Post by jeremy31 on 2023-08-16
Is there a boot order lock option in BIOS settings?

---

### Post by marcakaplan7 on 2023-08-17
thanks.  There is no "boot order lock option in the the BIOS settings...
But see my followup post...

---

### Post by marcakaplan7 on 2023-08-17
Update... Well the workaround continued to work... And I learned a tiny bit about (U)EFI in the making of it....  
But today, just for the heck of it...  I installed boot-repair on my Xubuntu system, that I had booted with my workaround.... 
Tried the newly installed boot-repair.... And voila-voila boot-repair worked.    Go figure...  I'll take my success....
Thanks for "listening".   Perhaps my previous post will help someone down the road who is also a UEFI newbie.  
If you have a USB memory stick... You almost can't make things worse... You're just copying some bytes onto that USB...  And delete or rename the Microsoft boot files from just that USB.
When you reboot off of the USB you're not running any code you didn't already have on your filesystem(s) anyway.

---

### Post by oldfred on 2023-08-17
Just saw this which is a Lenovo with UEFI setting for locking.
It is on a password settings page.

[https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg](https://www.reddit.com/media?url=https%3A%2F%2Fi.redd.it%2Foygxuo193ui41.jpg)

Workaround probably works as booting from USB is not included in the lock.
Some systems with UEFI boot, do have another setting on allowing USB boot or not. With Selcure boot on, it may not by default allow USB boot for security reasons.

---

### Post by marcakaplan7 on 2023-08-18
That would make sense, but the BIOS settings pages of my Lenovo Flex 14-5 do not have a "lock the nvram" setting.  There are options for disk password(s), secure boot, etc, etc but NOT for locking the EFI nvram boot settings (entries and boot order).

---

### Post by #&amp;thj^% on 2023-08-18
just my effort here to help, Ive seen where Resetting the CMOS jumpers worked, and others had  need to flash the BIOS. Go to the manufacturer's website and download the latest for your machine.

---

### Post by MAFoElffen on 2023-08-18
This may help... This was from me converting a Ubuntu 32bit Legacy BIOS system to install Ubuntu 64bit UFEI and Grub2 to boot the 32bit OS.
```

# become root
sudo su
# mount the root partition
mount /dev/sda3 /mnt 
mount  /dev/sda2 /mnt/boot
mkdir /mnt/boot/efi
apt update
apt upgrade
apt install reinstall grub-efi-amd64 grub-efi-amd64-signed shim-signed
for i in /dev /dev/pts /proc /sys; do mount -B $i /mnt$i; done
[COLOR=#ff0000]modprobe efivars
apt-get install --reinstall grub-efi-amd64-signed
grub-install --no-nvram --root-directory=/mnt
[/COLOR]chroot /mnt
update-grub
cd /boot/efi/EFI
mkdir ./BOOT
cp -R ubuntu/* ./BOOT/
cd ./BOOT
cp grubx64.efi bootx64.efi
## manually added EFI partiton to /boot/efi
reboot

```
Notice some rare options?

---

### Post by tlesick37 on 2023-09-05
I don't know if this will help anyone, but I was experencing the same issue and disabling secure boot resolved the issue for me.

---

### Post by jusii2 on 2024-02-28
This finally fixed it for me: mount -t efivarfs none /sys/firmware/efi/efivars

After that efibootmgr was able to write and even plain grub-install just worked. I assume ubuntu Boot-Repair would have worked after this, but as I was already trying to install grub manually, didn't try.

But, booted with Ubuntu 22.04 USB stick, chose Try Ubuntu and then:

Mounted my Ubuntu root partition to /mnt
Mounted my Ubuntu boot partition to /mnt/boot
Mounted my EFI partition to /mnt/boot/efi (have it on separate disk)

mount --bind /dev /mnt/dev
mount --bind /proc /mnt/sys
mount --bind /proc /mnt/proc
cd /mnt
chroot .
mount -t efivarfs none /sys/firmware/efi/efivars
grub-install

reboot

---

### Post by him610 on 2024-02-28
> obtain a very short, stubby, USB stick
Why? 
Why not use any USB stick, not necessarily very short, stubby; as long as, it has the capacity?

---

