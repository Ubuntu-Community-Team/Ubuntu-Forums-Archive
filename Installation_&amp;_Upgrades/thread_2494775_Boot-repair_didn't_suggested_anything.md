---
title: "Boot-repair didn't suggested anything"
date: 2024-01-26
forum: Installation &amp; Upgrades
---

### Post by felipegutierrez on 2024-01-26
Hello, I've got a boot problem it seems. 

I tried using boot-repair, the recommended repair button wasn't available. I created a bootinfo, available here: [https://*******.us/CC91QL](https://*******.us/CC91QL)

```
boot-repair-4ppa2075                                              [20240126_1755]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/BOOT/fbx64.efi /efi/BOOT/mmx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/ubuntu/grub.cfg

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda2: can't read superblock on /dev/sda2.

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.


================================ 1 OS detected =================================

OS#1:   Ubuntu 22.04.1 LTS on sda2

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: TU104 [GeForce RTX 2070 SUPER] from NVIDIA Corporation
Live-session OS is Linuxmint 64-bit (Linux Mint 21.2, victoria, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 0802(5.13) from American Megatrends Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0000,0001,0002
Boot0000* ubuntu    HD(1,GPT,fe40fa48-5eaa-4923-9584-30d4d0f78d29,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)
Boot0001* UEFI: KingstonDataTraveler 2.0PMAP    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/CDROM(1,0x23c,0x84c0)..BO
Boot0002* UEFI: KingstonDataTraveler 2.0PMAP, Partition 2    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/HD(2,MBR,0x14eb2669,0x23c,0x2130)..BO

c152ec201c37b6e97bbc2207e49d1271   sda1/BOOT/fbx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/BOOT/mmx64.efi
3795ef72a4ed0369ca44e711527904bf   sda1/ubuntu/grubx64.efi
fdafb5eece6caeccb788c946a28e6872   sda1/ubuntu/mmx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/ubuntu/shimx64.efi
728124f6ec8e22fbdbe7034812c81b95   sda1/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,  not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 223.57 GiB, 240057409536 bytes, 468862128 sectors
Disk identifier: 54887E3C-3F39-4DE1-986B-0752ADA0DA5F
       Start       End   Sectors   Size Type
sda1     2048   1050623   1048576   512M EFI System
sda2  1050624 468860927 467810304 223.1G Linux filesystem
Disk sdb: 14.42 GiB, 15483273216 bytes, 30240768 sectors
Disk identifier: 0x14eb2669
     Boot   Start      End  Sectors  Size Id Type
sdb1  *          0  5138431  5138432  2.5G  0 Empty
sdb2           572     9067     8496  4.1M ef EFI (FAT-12/16/32)
sdb3       5140480 30240767 25100288   12G 83 Linux

parted -lm (filtered): _________________________________________________________

sda:240GB:scsi:512:512:gpt:ATA SATAFIRM S11:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:240GB:240GB:ext4::;
sdb:15.5GB:scsi:512:512:msdos:Kingston DataTraveler 2.0:;
2:293kB:4643kB:4350kB:::esp;
3:2632MB:15.5GB:12.9GB:ext4::;

Free space >10MiB: ______________________________________________________________

sdb: 4.43MiB:2510MiB:2506MiB

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL                  PARTLABEL
sda                                                                                                              
&#9500;&#9472;sda1 vfat     5155-A723                            fe40fa48-5eaa-4923-9584-30d4d0f78d29                        EFI System Partition
&#9492;&#9472;sda2 ext4     0a28ec6d-eee0-4910-b7dd-3f2395183bc9 439b86bf-fda6-4d2c-99f4-6e9ce31df533                        
sdb    iso9660  2023-12-23-05-05-55-00                                                    Boot-Repair-Disk 64bit 
&#9500;&#9472;sdb1 iso9660  2023-12-23-05-05-55-00               14eb2669-01                          Boot-Repair-Disk 64bit 
&#9500;&#9472;sdb2 vfat     8D6C-A9F8                            14eb2669-02                          ESP                    
&#9492;&#9472;sdb3 ext4     e6dbaf9b-92ea-4951-8f78-53137cc7963b 14eb2669-03                          writable               

Mount points (filtered): _______________________________________________________

                                                             Avail Use% Mounted on
/dev/sda1                                                   505.7M   1% /mnt/boot-sav/sda1
/dev/sdb1                                                        0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda1                                                   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdb1                                                   iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048,iocharset=utf8

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 0a28ec6d-eee0-4910-b7dd-3f2395183bc9 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sdb




Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.

```

I don't know what to do.

I have a lot of stuff done in this computer for my masters' thesis. Please help me.

Thanks in advance.

---

### Post by ubfan1 on 2024-01-26
Please fix your bootinfo link, and include the boot errors you see.

---

### Post by felipegutierrez on 2024-01-26
When I try to boot the PC it just goes to the UEFI setup screen

---

### Post by tea for one on 2024-01-26
```
Mounting failed: mount: /mnt/BootInfo/sda2: can't read superblock on /dev/sda2
```
Looks like a damaged partition

Boot into a live session
Double check via Disks that your System Partition is still sda2
Make sure the partition is not mounted
Open a terminal
```
sudo fsck /dev/sda2
```

If you cannot repair the file system, then the information from this site may help
[https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

---

### Post by felipegutierrez on 2024-01-29
I wasn't able to recover the partition with either suggestion.

sda2 is my system partition.
the fsck output was?

> fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
/dev/sda2: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway<y>? yes
fsck.ext4: Input/output error while recovering journal of /dev/sda2

fsck.ext4: unable to set superblock flags on /dev/sda2


/dev/sda2: ********** WARNING: Filesystem still has errors **********



And then following the instruction on the cyberciti, I can get a list of the superblocks, but when I try to repair the partition I get this?
> fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
/dev/sda2: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
fsck.ext4: Input/output error while recovering journal of /dev/sda2
Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
fsck.ext4: unable to set superblock flags on /dev/sda2


/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****

/dev/sda2: ********** WARNING: Filesystem still has errors **********



And for the other sutff I saw about this the SSD is gone for good. So I have to buy another one. Thanks for the help

---

