---
title: "Need help resuce grub"
date: 2024-03-02
forum: Installation &amp; Upgrades
---

### Post by dinarsalem on 2024-03-02
boot-repair-4ppa2075                                              [20240302_1202]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for 
    (lvmid/unLdNe-VEHw-rEQ4-mQav-2pXN-w1X9-hjUb69/ds4fzV-juvf-1x2i-cbLn-DhmM-BD
    74-lSAckX)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos diskfilter lvm biosdisk
    ---------------------------------------------------------------------------

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sdb: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/FD/sdb: /dev/sdb already mounted or mount point busy.


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: HD Graphics 5500 from Intel Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04.3 LTS, focal, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: A02(5.4) from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
No EFI in dmseg.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0000,0002,0001,2001,2002,2003
Boot0000* USB Storage Device	BBS(HD,USB Storage Device,0x500)............................`.....................................4T........A.....................
Boot0001* Network	BBS(128,Network,0x0).......................................................................
Boot0002* Hard Drive	BBS(HD,Hard Drive,0x500)................-...........................................................A.........................
Boot0003* EFI USB DeviceUSB1-1 (SanDisk)	PciRoot(0x0)/Pci(0x14,0x0)/USB(11,0)/HD(1,MBR,0x2cf4ba3a,0x506fcc,0x1f40)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________


Partitions info (1/3): _________________________________________________________


Partitions info (2/3): _________________________________________________________


Partitions info (3/3): _________________________________________________________


fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0x6bffaf06
     Boot      Start        End    Sectors   Size Id Type
sda2  *       1001470 1953523711 1952522242   931G  5 Extended
sda5          1001472 1025001471 1024000000 488.3G 8e Linux LVM
sda6       1025003520 1953523711  928520192 442.8G  7 HPFS/NTFS/exFAT
Disk sdb: 28.66 GiB, 30752000000 bytes, 60062500 sectors
Disk identifier: 0x2cf4ba3a
     Boot   Start      End  Sectors  Size Id Type
sdb1  *          0  5999871  5999872  2.9G  0 Empty
sdb2       5271500  5279499     8000  3.9M ef EFI (FAT-12/16/32)
sdb3       6000640 60062499 54061860 25.8G 83 Linux
Disk mapper/ubuntu--vg-root: 400 GiB, 429496729600 bytes, 838860800 sectors

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:unknown:ATA HGST HTS541010A9:;
sdb:30.8GB:scsi:512:512:unknown:SanDisk Ultra USB 3.0:;

blkid (filtered): ______________________________________________________________

NAME                FSTYPE   UUID                                 PARTUUID                             LABEL                    PARTLABEL
sda                                                                                                                             
&#9500;&#9472;sda2                                                            6bffaf06-02                                                   
&#9500;&#9472;sda5                                                                                                                          
&#9474; &#9492;&#9472;ubuntu--vg-root ext2     0c3b2901-e21a-4331-8594-224d25203798                                                               
&#9492;&#9472;sda6                                                                                                                          
sdb                 iso9660  2021-08-19-11-03-38-00                                                    Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdb1              iso9660  2021-08-19-11-03-38-00               2cf4ba3a-01                          Ubuntu 20.04.3 LTS amd64 
&#9500;&#9472;sdb2              vfat     54C5-9C6C                            2cf4ba3a-02                                                   
&#9492;&#9472;sdb3              ext4     a0281fc8-f212-43e5-a05d-6511465e2e43 2cf4ba3a-03                          writable                 

Mount points (filtered): _______________________________________________________

                                                              Avail Use% Mounted on
/dev/sdb1                                                         0 100% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sdb1                                                     iso9660         ro,noatime,nojoliet,check=s,map=n,blocksize=2048

============================== ls -R /dev/mapper/ ==============================

/dev/mapper:
control
ubuntu--vg-root

======================== Unknown MBRs/Boot Sectors/etc =========================

Unknown BootLoader on sdb




Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.

---

### Post by Rubi1200 on 2024-03-02
What was supposed to be installed? I say supposed to be because the script shows you have no operating system installed.

What happened to get you to this point?

The more information you can give us, the easier it will be to help.

---

### Post by yancek on 2024-03-02
You will have to post more information on what you had and what you tried to do.  Boot repair shows sda6 as an ntfs filesystem (windows) but that is the only windows partition.  Your drive appears to have a dos partition table and there is no primary partition for windows and windows requires boot files on a primary partition.  Did you have windows installed and want to keep it.   Boot repair also shows the computer is EFI capable but shows no EFI entries for either Ubuntu or windows.  It appears you used the option to install using LVM which generally requires a separate /boot partition which you do not have.  Did you use some tutorial to try to do the installation.  As indicated in post 2, there is no OS shown as being installed.  Did you intend to use LVM?  Do you understand how it works?

---

