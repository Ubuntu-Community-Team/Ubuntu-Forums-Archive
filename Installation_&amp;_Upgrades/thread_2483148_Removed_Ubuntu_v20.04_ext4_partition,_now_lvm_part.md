---
title: "Removed Ubuntu v20.04 ext4 partition, now lvm partition with Ubuntu v22.04 won't boot"
date: 2023-01-21
forum: Installation &amp; Upgrades
---

### Post by zerodefect on 2023-01-21
On an HDD that already had a partition containing Ubuntu v22.04 (lvm), I installed Ubuntu v20.04 into a new ext4 partition which positioned at the front of the disk.

Unfortunately, since removing Ubuntu v20.04, I cannot get my previous Ubuntu v22.04 install to boot.

This is how the disk layout appears according to GParted:

[IMG]https://i.ibb.co/2g5QKqm/Screenshot-from-2023-01-21-13-10-26.png[/IMG]

I have gone away and run boot-repair. Here is the output.

```

boot-repair-4ppa203                                              [20230121_1258]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Grub2 (v2.00) is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------

sda2: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi

sdb: ___________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sdb and looks at sector 1870954872 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location.
    Operating System:  Ubuntu 20.04.5 LTS
    Boot files:        /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img


================================ 1 OS detected =================================

OS#1:   Ubuntu 22.04.1 LTS on mapper/gubuntu--vg-lvol0

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: GP107GL [Quadro P600] from NVIDIA Corporation
Live-session OS is Ubuntu 64-bit (Ubuntu 22.04.1 LTS, jammy, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 2.22.0(2.22) from Dell Inc.
This live-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda	: notGPT,	no-BIOSboot,	has-noESP, 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

mapper/gubuntu--vg-lvol0	: is-os,	64, apt-get,	no-docgrub,	nogrub,	nogrubinstall,	no-grubenv,	noupdategrub,	not-far

Partitions info (2/3): _________________________________________________________

mapper/gubuntu--vg-lvol0	: isnotESP,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot

Partitions info (3/3): _________________________________________________________

mapper/gubuntu--vg-lvol0	: not--sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0xd4040dd7
      Boot      Start        End   Sectors   Size Id Type
sda2  *    1136642048 1953519615 816877568 389.5G 83 Linux
Disk sdb: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0x00000000
Disk mapper/gubuntu--vg-lvol0: 350 GiB, 375809638400 bytes, 734003200 sectors
Disk mapper/gubuntu--vg-swap_2: 1 GiB, 1073741824 bytes, 2097152 sectors
Disk sdd: 7.5 GiB, 8053063680 bytes, 15728640 sectors
Disk identifier: 0x14f23075
      Boot Start      End  Sectors  Size Id Type
sdd1  *     2048 15728639 15726592  7.5G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:1000GB:scsi:512:4096:msdos:ATA HGST HTS721010A9:;
2:582GB:1000GB:418GB:::boot;
sdb:1000GB:scsi:512:4096:msdos:ATA HGST HTS721010A9:;
sdd:8053MB:scsi:512:512:msdos:Generic Flash Disk:;
1:1049kB:8053MB:8052MB:fat32::boot, lba;
mapper/gubuntu--vg-swap_2:1074MB:dm:512:4096:loop:Linux device-mapper (linear):;
1:0.00B:1074MB:1074MB:linux-swap(v1)::;
mapper/gubuntu--vg-lvol0:376GB:dm:512:4096:loop:Linux device-mapper (linear):;
1:0.00B:376GB:376GB:ext4::;

Free space >10MiB: ______________________________________________________________

sda: 0.00MiB:555001MiB:555001MiB
sdb: 0.00MiB:953870MiB:953870MiB

blkid (filtered): ______________________________________________________________

NAME                   FSTYPE      UUID                                   PARTUUID                             LABEL       PARTLABEL
sda                                                                                                                        
&#9492;&#9472;sda2                 LVM2_member oGICbi-KF6F-A5bZ-gAIO-Yirh-OpP6-t1U87a d4040dd7-02                                      
  &#9500;&#9472;gubuntu--vg-lvol0  ext4        88920d1b-584c-4410-a7b5-d89c4acb9774                                                    
  &#9492;&#9472;gubuntu--vg-swap_2 swap        a5f3e4f9-db18-4019-b0cf-88b90c33c446                                                    
sdb                    ext4        f02fcfae-3728-4381-b0ce-280f255750f5                                                    
sdc                                                                                                                        
sdd                                                                                                                        
&#9492;&#9472;sdd1                 vfat        C4C6-89FC                              14f23075-01                          UBUNTU 22_0 

Mount points (filtered): _______________________________________________________

                               Avail Use% Mounted on
/dev/mapper/gubuntu--vg-lvol0  62.2G  77% /mnt/boot-sav/mapper/gubuntu--vg-lvol0
/dev/sdb                      860.9G   1% /media/ubuntu/f02fcfae-3728-4381-b0ce-280f255750f5
/dev/sdd1                       3.9G  48% /cdrom

Mount options (filtered): ______________________________________________________


============================== ls -R /dev/mapper/ ==============================

/dev/mapper:
control
gubuntu--vg-lvol0
gubuntu--vg-swap_2

====================== sdd1/boot/grub/grub.cfg (filtered) ======================

Try or Install Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sdd1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

=========================== sdb/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb during installation
UUID=f02fcfae-3728-4381-b0ce-280f255750f5 /               ext4    errors=remount-ro 0       1
/dev/mapper/gubuntu--vg-swap_2 none            swap    sw              0       0

======================= sdb/etc/default/grub (filtered) ========================

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

==================== sdb: Location of files loaded by Grub =====================

           GiB - GB             File                                 Fragment(s)
 892.140827179 = 957.928919040  boot/grub/i386-pc/core.img                     1
   4.719253540 = 5.067259904    boot/vmlinuz                                   1
   4.719253540 = 5.067259904    boot/vmlinuz-5.14.0-1056-oem                   1
   4.719253540 = 5.067259904    boot/vmlinuz.old                               1
 539.161052704 = 578.919772160  boot/initrd.img                                2
 539.161052704 = 578.919772160  boot/initrd.img-5.14.0-1056-oem                2
 539.161052704 = 578.919772160  boot/initrd.img.old                            2

====================== sdb: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18224 Jan 11  2022 10_linux
-rwxr-xr-x 1 root root 42359 Jan 11  2022 10_linux_zfs
-rwxr-xr-x 1 root root 12894 Jan 11  2022 20_linux_xen
-rwxr-xr-x 1 root root 12059 Jan 11  2022 30_os-prober
-rwxr-xr-x 1 root root  1424 Jan 11  2022 30_uefi-firmware
-rwxr-xr-x 1 root root   700 Feb 21  2022 35_fwupd
-rwxr-xr-x 1 root root   214 Jan 11  2022 40_custom
-rwxr-xr-x 1 root root   216 Jan 11  2022 41_custom

================================= User choice ==================================

Is there RAID on this computer? no


==================== blkid (filtered) before lvm activation ====================

/dev/mapper/gubuntu--vg-lvol0: UUID="88920d1b-584c-4410-a7b5-d89c4acb9774" BLOCK_SIZE="4096" TYPE="ext4"
/dev/sdb: UUID="f02fcfae-3728-4381-b0ce-280f255750f5" BLOCK_SIZE="4096" TYPE="ext4" PTTYPE="dos"
/dev/sdd1: LABEL="UBUNTU 22_0" UUID="C4C6-89FC" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="14f23075-01"
/dev/mapper/gubuntu--vg-swap_2: UUID="a5f3e4f9-db18-4019-b0cf-88b90c33c446" TYPE="swap"
/dev/sda2: UUID="oGICbi-KF6F-A5bZ-gAIO-Yirh-OpP6-t1U87a" TYPE="LVM2_member" PARTUUID="d4040dd7-02"


================================ LVM activation ================================

modprobe dm-mod  
vgscan --mknodes
  Found volume group "gubuntu-vg" using metadata type lvm2
vgchange -ay
  2 logical volume(s) in volume group "gubuntu-vg" now active
lvscan
  ACTIVE            '/dev/gubuntu-vg/lvol0' [350.00 GiB] inherit
  ACTIVE            '/dev/gubuntu-vg/swap_2' [1.00 GiB] inherit
blkid -g



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to fix packages) and reinstall the grub2 of
mapper/gubuntu--vg-lvol0 into the MBR of sda.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s

```

Admittedly, fiddling with disks volumes/partitions is not my forte. Is it safe to carry out the suggested repairs?

```


Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to fix packages) and reinstall the grub2 of
mapper/gubuntu--vg-lvol0 into the MBR of sda.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s

```

Advice would be greatly appreciated.

---

### Post by Impavidus on 2023-01-21
It appears that you use bios/legacy booting and an MBR partitioned hard drive. It only has one bootloader, which looked for its configuration on partition sda1, which you deleted. It think boot-repair's default repair will fix this.

grub can boot from lvm. It can't boot from en encrypted filesystem, which would require a /boot partition, but it doesn't look like you've such a system.

---

