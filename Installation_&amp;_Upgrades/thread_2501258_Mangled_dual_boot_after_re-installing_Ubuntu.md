---
title: "Mangled dual boot after re-installing Ubuntu"
date: 2024-09-29
forum: Installation &amp; Upgrades
---

### Post by har-wing-9982 on 2024-09-29
I decided to perform a fresh install of Ubuntu to upgrade from an older version. I had Ubuntu and Windows 11 working perfectly (note: I originally installed Windows 10 and upgraded to 11) prior to this exercise

 I took a photo of the output of [FONT=courier new]**df -h**[/FONT] and re-installed ubuntu in advanced mode keeping the filesystem partitions the same, however when I rebooted I no longer saw the Windows option in Grub. One thing I noticed and perhaps this caused the error was that Ubuntu detected [FONT=courier new]**/dev/nvme1n1p2**[/FONT] as [FONT=courier new]**/boot/efi/**[/FONT] during install but I changed this to [FONT=courier new]**/dev/nvme0n1p1**[/FONT] to match the prior output from df.

I since ran boot-repair from a live Ubuntu the output of which is below. However this has not solved my issue and I still no-longer see Windows as an option.

```

boot-repair-4ppa2081                                              [20240929_1949]

============================= Boot Repair Summary ==============================


mount -t ntfs-3g -o remove_hiberfile /dev/nvme0n1p3 /mnt/boot-sav/nvme0n1p3 



Failed to write lock '/dev/nvme0n1p3': Resource temporarily unavailable
Error opening '/dev/nvme0n1p3': Resource temporarily unavailable
Failed to mount '/dev/nvme0n1p3': Resource temporarily unavailable
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.8.0-41-generic

=================== /boot detected. Please check the options.

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will reinstall the grub-efi of
nvme1n1p4,
using the following options:  nvme1n1p1/boot nvme1n1p2/boot/efi
Additional repair will be performed: unhide-bootmenu-10s use-standard-efi-file restore-efi-backups


rm /mnt/boot-sav/nvme0n1p1/efi/Boot/bootx64.efi
mv /mnt/boot-sav/nvme0n1p1/efi/Boot/bkpbootx64.efi /mnt/boot-sav/nvme0n1p1/efi/Boot/bootx64.efi
rm /mnt/boot-sav/nvme1n1p2/efi/Boot/bootx64.efi
mv /mnt/boot-sav/nvme1n1p2/efi/Boot/bkpbootx64.efi /mnt/boot-sav/nvme1n1p2/efi/Boot/bootx64.efi
Mount /dev/nvme1n1p1 on /mnt/boot-sav/nvme1n1p4/boot
Mount /dev/nvme1n1p2 on /mnt/boot-sav/nvme1n1p4/boot/efi

=================== Reinstall the grub-efi of /dev/nvme1n1p4 ===================

chroot /mnt/boot-sav/nvme1n1p4 grub-install --version
grub-install (GRUB) 2.12-1ubuntu7
modprobe: FATAL: Module efivars not found in directory /lib/modules/6.8.0-41-generic
chroot /mnt/boot-sav/nvme1n1p4 modprobe efivars

chroot /mnt/boot-sav/nvme1n1p4 efibootmgr -v (filtered) before grub install
EFI variables are not supported on this system.
error trace:


chroot /mnt/boot-sav/nvme1n1p4 uname -r
6.8.0-41-generic

chroot /mnt/boot-sav/nvme1n1p4 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.
df /dev/nvme1n1p2
mv /mnt/boot-sav/nvme1n1p4/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/nvme1n1p4/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/nvme1n1p4/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/nvme1n1p4/boot/efi/EFI/Boot/bootx64.efi
df /dev/nvme0n1p1
mv /mnt/boot-sav/nvme0n1p1/EFI/Boot/bootx64.efi /mnt/boot-sav/nvme0n1p1/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/nvme1n1p4/boot/efi/efi/ubuntu/grubx64.efi /mnt/boot-sav/nvme0n1p1/EFI/Boot/bootx64.efi

chroot /mnt/boot-sav/nvme1n1p4 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

chroot /mnt/boot-sav/nvme1n1p4 efibootmgr -v (filtered) after grub install
EFI variables are not supported on this system.
error trace:

Warning: NVram is locked (Ubuntu not found in efibootmgr).

chroot /mnt/boot-sav/nvme1n1p4 update-grub
Sourcing file `/etc/default/grub'
Found linux image: /boot/vmlinuz-6.8.0-45-generic
Found initrd image: /boot/initrd.img-6.8.0-45-generic
Found memtest86+ 64bit EFI image: /memtest86+x64.efi
Adding boot menu entry for UEFI Firmware Settings ...

Boot successfully repaired.

Locked-NVram detected. Please do not forget to make your UEFI firmware boot on the Ubuntu 24.04.1 LTS entry (nvme1n1p2/efi/ubuntu/grubx64.efi file) !


============================ Boot Info After Repair ============================

 => No boot loader is installed in the MBR of /dev/nvme0n1.
 => No boot loader is installed in the MBR of /dev/nvme1n1.
 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

nvme0n1p1: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme0n1p2: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

nvme0n1p3: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8 or 10
    Boot files:        /bootmgr /Windows/System32/winload.exe

nvme0n1p4: _____________________________________________________________________

    File system:       ntfs
    Boot sector type:  NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

nvme1n1p1: _____________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

nvme1n1p2: _____________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/bkpbootx64.efi /efi/BOOT/bootx64.efi 
                       /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

nvme1n1p3: _____________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

nvme1n1p4: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 24.04.1 LTS
    Boot files:        /etc/fstab /etc/default/grub

nvme1n1p5: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sdc and looks at sector 0 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:   mount: /mnt/BootInfo/FD/sdc: /dev/sdc already mounted or mount point busy.
       dmesg(1) may have more information after failed mount system call.


================================ 2 OS detected =================================

OS#1 (linux):   Ubuntu 24.04.1 LTS on nvme1n1p4
OS#2 (windows):   Windows 8 or 10 on nvme0n1p3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: TU104 [GeForce RTX 2080 Rev. A] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 24.04.1 LTS, noble, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 3607(5.17) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0004,0002,0003
Boot0002* Ubuntu    HD(1,GPT,35996724-fd6b-487b-8308-6c0d4ccc54dd,0x800,0x32000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0003* ubuntu    HD(2,GPT,dddb0521-b348-4f4e-9f2a-b9a6f6efffa6,0xa7000,0x47800)/File(\EFI\UBUNTU\SHIMX64.EFI)0000424f
Boot0004* UEFI: SanDisk, Partition 2    PciRoot(0x0)/Pci(0x1,0x2)/Pci(0x0,0x0)/USB(6,0)/HD(2,GPT,eed3de8a-acd3-4541-ba17-9014c007d874,0xb8b5a0,0x27a0)0000424f

07e25dcaf57c776875f78fa36827c58e   nvme0n1p1/BOOT/bkpbootx64.efi
66f69798ad23240e43b7ba0044a914c4   nvme0n1p1/BOOT/bootx64.efi
39bc76ff6662f4fbe9aa116e4c997b41   nvme0n1p1/BOOT/fbx64.efi
4ba5a5aad43c197e9fb58b76b404d287   nvme0n1p1/BOOT/mmx64.efi
66f69798ad23240e43b7ba0044a914c4   nvme0n1p1/ubuntu/grubx64.efi
4ba5a5aad43c197e9fb58b76b404d287   nvme0n1p1/ubuntu/mmx64.efi
07e25dcaf57c776875f78fa36827c58e   nvme0n1p1/ubuntu/shimx64.efi
07e25dcaf57c776875f78fa36827c58e   nvme1n1p2/BOOT/bkpbootx64.efi
07e25dcaf57c776875f78fa36827c58e   nvme1n1p2/BOOT/bootx64.efi
39bc76ff6662f4fbe9aa116e4c997b41   nvme1n1p2/BOOT/fbx64.efi
4ba5a5aad43c197e9fb58b76b404d287   nvme1n1p2/BOOT/mmx64.efi
66f69798ad23240e43b7ba0044a914c4   nvme1n1p2/ubuntu/grubx64.efi
4ba5a5aad43c197e9fb58b76b404d287   nvme1n1p2/ubuntu/mmx64.efi
07e25dcaf57c776875f78fa36827c58e   nvme1n1p2/ubuntu/shimx64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

nvme0n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    has-win,    2048 sectors * 512 bytes
nvme1n1    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes
sda    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes
sdb    : is-GPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

nvme0n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme0n1p3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme0n1p4    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
nvme1n1p1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    grubenv-ok,    noupdategrub,    not-far
nvme1n1p2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
nvme1n1p4    : is-os,    64, apt-get,    signed grub-efi ,    grub2,    grub-install,    no-grubenv,    update-grub,    not-far
nvme1n1p5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

nvme0n1p1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, vfat
nvme0n1p3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot, ntfs
nvme0n1p4    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot, ntfs
nvme1n1p1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext2
nvme1n1p2    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, vfat
nvme1n1p4    : isnotESP,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4
nvme1n1p5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ext4
sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot, ntfs

Partitions info (3/3): _________________________________________________________

nvme0n1p1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme0n1p4    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme0n1
nvme1n1p1    : is---sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme1n1
nvme1n1p2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme1n1
nvme1n1p4    : not--sepboot,    no---boot,    fstab-has-goodBOOT,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    nvme1n1
nvme1n1p5    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    nvme1n1
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sdb1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb

fdisk -l (filtered): ___________________________________________________________

Disk sda: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk identifier: FC380C21-E054-47FD-A005-45E4CB9FC6E6
     Start        End    Sectors  Size Type
sda1   2048 3907029134 3907027087  1.8T Microsoft basic data
Disk sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: B9C571EC-4FED-41C2-A4B2-625D658ED1DE
     Start        End    Sectors   Size Type
sdb1   2048 1953523711 1953521664 931.5G Microsoft basic data
Disk nvme0n1: 465.76 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 1F98A626-8438-496D-9743-816DD2A8A19C
             Start       End   Sectors   Size Type
nvme0n1p1      2048    206847    204800   100M EFI System
nvme0n1p2    206848    239615     32768    16M Microsoft reserved
nvme0n1p3    239616 975064915 974825300 464.8G Microsoft basic data
nvme0n1p4 975065088 976769023   1703936   832M Windows recovery environment
Disk nvme1n1: 238.47 GiB, 256060514304 bytes, 500118192 sectors
Disk identifier: 8D06603A-6877-4B22-BF57-F7E982DF8A15
             Start       End   Sectors   Size Type
nvme1n1p1      2048    683688    681641 332.8M Linux filesystem
nvme1n1p2    684032    976895    292864   143M EFI System
nvme1n1p3    976896  40976383  39999488  19.1G Linux swap
nvme1n1p4  40976384 140976127  99999744  47.7G Linux filesystem
nvme1n1p5 140976128 500117503 359141376 171.3G Linux filesystem
Disk sdc: 28.65 GiB, 30765219840 bytes, 60088320 sectors
Disk identifier: EED3DE8A-ACD3-4541-BA15-9014C007D874
        Start      End  Sectors  Size Type
sdc1        64 12105119 12105056  5.8G Microsoft basic data
sdc2  12105120 12115263    10144    5M EFI System
sdc3  12115264 12115863      600  300K Microsoft basic data
sdc4  12115968 60086271 47970304 22.9G Linux filesystem

parted -lm (filtered): _________________________________________________________

sda:2000GB:scsi:512:4096:gpt:ATA ST2000DM001-1ER1:;
1:1049kB:2000GB:2000GB:ntfs:Media:msftdata;
sdb:1000GB:scsi:512:512:gpt:ATA Samsung SSD 860:;
1:1049kB:1000GB:1000GB:ntfs:Basic data partition:msftdata;
sdc:30.8GB:scsi:512:512:gpt:SanDisk Cruzer Blade:;
1:32.8kB:6198MB:6198MB::ISO9660:hidden, msftdata;
2:6198MB:6203MB:5194kB::Appended2:boot, esp;
3:6203MB:6203MB:307kB::Gap1:hidden, msftdata;
4:6203MB:30.8GB:24.6GB:ext4::;
nvme0n1:500GB:nvme:512:512:gpt:Samsung SSD 980 PRO 500GB:;
1:1049kB:106MB:105MB:fat16:EFI system partition:boot, esp, no_automount;
2:106MB:123MB:16.8MB::Microsoft reserved partition:msftres, no_automount;
3:123MB:499GB:499GB:ntfs:Basic data partition:msftdata;
4:499GB:500GB:872MB:ntfs::hidden, diag, no_automount;
nvme1n1:256GB:nvme:512:512:gpt:SAMSUNG MZVPV256HDGL-00000:;
1:1049kB:350MB:349MB:ext2::;
2:350MB:500MB:150MB:fat32::boot, esp;
3:500MB:21.0GB:20.5GB:linux-swap(v1)::swap;
4:21.0GB:72.2GB:51.2GB:ext4::;
5:72.2GB:256GB:184GB:ext4::;

blkid (filtered): ______________________________________________________________

NAME        FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                     
&#9492;&#9472;sda1      ntfs     219982C928262DFB                     25f7ecf7-68d6-2441-8152-d93d07bd3383 Media                    Media
sdb                                                                                                                     
&#9492;&#9472;sdb1      ntfs     4F06EC1543A1C939                     77715184-1e2e-4102-a733-e53bb8b04589 Binaries                 Basic data partition
sdc         iso9660  2024-08-27-16-23-26-00                                                    Ubuntu 24.04.1 LTS amd64 
&#9500;&#9472;sdc1      iso9660  2024-08-27-16-23-26-00               eed3de8a-acd3-4541-ba14-9014c007d874 Ubuntu 24.04.1 LTS amd64 ISO9660
&#9500;&#9472;sdc2      vfat     3C53-CAEB                            eed3de8a-acd3-4541-ba17-9014c007d874 ESP                      Appended2
&#9500;&#9472;sdc3                                                    eed3de8a-acd3-4541-ba16-9014c007d874                          Gap1
&#9492;&#9472;sdc4      ext4     43a89caa-6ede-4ebe-9da0-1a78bc3b3bbd 84d5528e-ce49-494c-b95b-48d4f3bc2acb writable                 
nvme0n1                                                                                                                 
&#9500;&#9472;nvme0n1p1 vfat     38BE-FB13                            35996724-fd6b-487b-8308-6c0d4ccc54dd                          EFI system partition
&#9500;&#9472;nvme0n1p2                                               e55da894-fdd1-40ce-a574-5890868f229d                          Microsoft reserved partition
&#9500;&#9472;nvme0n1p3 ntfs     EAA42E92A42E6175                     99da41ad-3a68-4e2f-a16e-f4f0ed407265                          Basic data partition
&#9492;&#9472;nvme0n1p4 ntfs     F4AEA536AEA4F272                     4b83b196-0379-4d6b-aa75-39aa4287a101                          
nvme1n1                                                                                                                 
&#9500;&#9472;nvme1n1p1 ext2     7b53dfe4-fe9f-45aa-90a7-c3f6836160c0 7fa80b07-9cb7-4985-9875-91e2c8599b0e                          
&#9500;&#9472;nvme1n1p2 vfat     2B43-A857                            dddb0521-b348-4f4e-9f2a-b9a6f6efffa6                          
&#9500;&#9472;nvme1n1p3 swap     db6decf5-abde-4788-ba4b-224471f69126 ff2e910b-00ab-4117-9b1d-841549f434cc                          
&#9500;&#9472;nvme1n1p4 ext4     9b748736-9db6-4d33-b997-71a0d25b8d86 3ac42968-2d88-4775-a05c-76ebd77f56b6                          
&#9492;&#9472;nvme1n1p5 ext4     4870c89f-3797-4d04-a944-e2ba023ee0ec 574b1d46-6094-4e99-8899-bf048121f2db                          

Mount points (filtered): _______________________________________________________

                                                               Avail Use% Mounted on
/dev/nvme0n1p1                                                 91.1M   9% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3                                                240.3G  48% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4                                                 68.4M  92% /mnt/boot-sav/nvme0n1p4
/dev/nvme1n1p1                                                178.3M  37% /mnt/boot-sav/nvme1n1p1
/dev/nvme1n1p2                                                133.8M   5% /mnt/boot-sav/nvme1n1p2
/dev/nvme1n1p4                                                 29.6G  31% /mnt/boot-sav/nvme1n1p4
/dev/nvme1n1p5                                                124.9G  20% /mnt/boot-sav/nvme1n1p5
/dev/sda1                                                       1.6T  12% /mnt/boot-sav/sda1
/dev/sdb1                                                       345G  63% /mnt/boot-sav/sdb1
/dev/sdc1                                                          0 100% /cdrom
efivarfs                                                         72K  40% /sys/firmware/efi/efivars

Mount options (filtered): ______________________________________________________

/dev/nvme0n1p1                                                vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme0n1p3                                                fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme0n1p4                                                fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/nvme1n1p1                                                ext2            rw,relatime
/dev/nvme1n1p2                                                vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/nvme1n1p4                                                ext4            rw,relatime
/dev/nvme1n1p5                                                ext4            rw,relatime
/dev/sda1                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdb1                                                     fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdc1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

=================== nvme0n1p1/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 7b53dfe4-fe9f-45aa-90a7-c3f6836160c0 root 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

====================== nvme1n1p1/grub/grub.cfg (filtered) ======================

Ubuntu   9b748736-9db6-4d33-b997-71a0d25b8d86
### END /etc/grub.d/30_os-prober ###
UEFI Firmware Settings   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###

================= nvme1n1p1: Location of files loaded by Grub ==================

           GiB - GB             File                                 Fragment(s)
   0.146720886 = 0.157540352    grub/grub.cfg                                  1
   0.046146393 = 0.049549312    vmlinuz                                        9
   0.046146393 = 0.049549312    vmlinuz-6.8.0-45-generic                       9
   0.046146393 = 0.049549312    vmlinuz.old                                    9
   0.109027863 = 0.117067776    initrd.img                                     8
   0.178764343 = 0.191946752    initrd.img-6.8.0-41-generic                    8
   0.109027863 = 0.117067776    initrd.img-6.8.0-45-generic                    8
   0.109027863 = 0.117067776    initrd.img.old                                 8

=================== nvme1n1p2/efi/ubuntu/grub.cfg (filtered) ===================

search.fs_uuid 7b53dfe4-fe9f-45aa-90a7-c3f6836160c0 root 
set prefix=($root)'/grub'
configfile $prefix/grub.cfg

======================== nvme1n1p4/etc/fstab (filtered) ========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme1n1p4 during curtin installation
/dev/disk/by-uuid/9b748736-9db6-4d33-b997-71a0d25b8d86 / ext4 defaults 0 1
# /boot was on /dev/nvme1n1p1 during curtin installation
# /home was on /dev/nvme1n1p5 during curtin installation
/dev/disk/by-uuid/4870c89f-3797-4d04-a944-e2ba023ee0ec /home ext4 defaults 0 1
# /boot/efi was on /dev/nvme0n1p1 during curtin installation
/swap.img    none    swap    sw    0    0
UUID=7b53dfe4-fe9f-45aa-90a7-c3f6836160c0  /boot       ext2    defaults      0       2
UUID=2B43-A857  /boot/efi       vfat    defaults      0       1

==================== nvme1n1p4/etc/default/grub (filtered) =====================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`( . /etc/os-release; echo ${NAME:-Ubuntu} ) 2>/dev/null || echo Ubuntu`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

=================== nvme1n1p4: ls -l /etc/grub.d/ (filtered) ===================

-rwxr-xr-x 1 root root 18133 Apr  4 10:12 10_linux
-rwxr-xr-x 1 root root 43202 Apr  4 10:12 10_linux_zfs
-rwxr-xr-x 1 root root 14513 Apr  4 10:12 20_linux_xen
-rwxr-xr-x 1 root root   786 Apr  4 10:12 25_bli
-rwxr-xr-x 1 root root 13120 Apr  4 10:12 30_os-prober
-rwxr-xr-x 1 root root  1174 Apr  4 10:12 30_uefi-firmware
-rwxr-xr-x 1 root root   722 Apr  5 11:36 35_fwupd
-rwxr-xr-x 1 root root   214 Apr  4 10:12 40_custom
-rwxr-xr-x 1 root root   215 Apr  4 10:12 41_custom

```

---

### Post by yancek on 2024-09-29
Both of your drives are GPT drives which means that windows requires the OS to be installed in UEFI mode.  You have an EFI partition on both the drive on which windows was installed as well as the drive on which Ubuntu was installed.  If you look at the contents of both those partitions you can see that you have only EFI files for Ubuntu and absolutely no sign of windows.  If you look at the output of sudo efibootmgr you will see two entries for Ubuntu but none for windows.  It appears wrong choices were made as the Ubuntu installer will create and populate a directory on the EFI partition but will NOT overwrite other existing directories.  You will need some windows install iso or usb to repair windows.

---

### Post by oldfred on 2024-09-29
[FONT=arial]I prefer to keep ESP on same drive as install when using multiple drives.

It looks like you reformatted /dev/nvme0n1p1 from normal FAT32 to FAT16 and that erased the Windows boot files in that ESP.

Your fstab in nvme1n1 shows mount of the ESP on nvme1n1.[/FONT]
Use Boot-Repair's advanced mode & reinstall grub to nvme1n1

Since boot & UEFI entries now missing from nvme0n1, you have to use a Windows repair flash drive to fix it. UEFI used to allow FA16 for external drives, but I have only seen FAT32 for internal drives. So reformat nvme0n1p1 to FAT32 which will erase the Ubuntu entries that should be on nvme1 anyway. 

It looks like you have/had Windows fast startup on. That sets hibernation flags which prevents the Linux NTFS driver from correctly seeing all NTFS partitions. Make sure fast startup is off. Windows is known to turn it back on with some updates.

---

### Post by har-wing-9982 on 2024-09-30
oldfred & yancek thanks for the reply. I've managed to repair the boot record now.

1. Formatted [FONT=arial][FONT=courier new]**/dev/nvme0n1p1**[/FONT] as FAT32
2. Created a bootable windows USB from [https://www.microsoft.com/software-download/windows11](https://www.microsoft.com/software-download/windows11)
3. Once the [/FONT][FONT=arial]Windows installer was running [/FONT][FONT=arial]I selected Repair Computer -> Troubleshoot -> Advanced Options -> Command Prompt

I then used a series of commands to re-install boot files

```

diskpart
select disk 0
list vol

```

Identified [/FONT][FONT=arial][FONT=courier new]**/dev/nvme0n1p1**[/FONT] by identifying volume size & filesystem type (FAT32). I also identified the main Windows partition and took a note of the drive letter which in my case was **E**

[/FONT][FONT=arial]```

select vol <vol number>
assign letter=J
exit

```

I then copied over the boot info

```

bcdboot E:\Windows /s J: /f UEFI

```

I then rebooted the machine and could see both OS in my BIOS. I booted into Linux and re-installed Grub

[/FONT][FONT=arial]```

sudo os-prober
sudo update-grub

```[/FONT][FONT=arial]



[/FONT]

---

