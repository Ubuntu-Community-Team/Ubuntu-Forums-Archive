---
title: "Boot problem after install"
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by rochte on 2011-09-27
I still cannot boot after a clean install of Ubuntu 11.04.  I have tried boot-repair without success.  (I've installed and used Linux since the very earliest releases in the mid-90s, so I'm feeling particularly troubled by this problem...)

Here's what was posted to pastebin:

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sda1 has 0 
                       sectors.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 520 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              34        39,096        39,063 EFI System partition
/dev/sda2          39,097   968,744,175   968,705,079 EFI System partition
/dev/sda3     968,744,176   976,773,118     8,028,943 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1006 MB, 1006108672 bytes
24 heads, 23 sectors/track, 3559 cylinders, total 1965056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *            248     1,965,055     1,964,808   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3E7D-3A4E                              vfat       
/dev/sda2        35ced8ec-85b9-4aef-80a1-9cd880a920e6   ext4       
/dev/sda3        dfb1f846-6422-4ddc-8147-07d16d7248cb   swap       
/dev/sdb1        E0FD-1813                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=35ced8ec-85b9-4aef-80a1-9cd880a920e6 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=3E7D-3A4E  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=dfb1f846-6422-4ddc-8147-07d16d7248cb none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   1.526936054 = 1.639535104    boot/initrd.img-2.6.38-8-generic               2
  32.151459217 = 34.522366464   boot/vmlinuz-2.6.38-8-generic                  1
   1.526936054 = 1.639535104    initrd.img                                     2
  32.151459217 = 34.522366464   vmlinuz                                        1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)


ADDITIONAL INFORMATION :
**************** log of boot-repair 2011-09-23__19h24 ****************
boot-repair version : 3-0ppa7~natty
clean-ubiquity-common version : 3-0ppa6~natty
internet: connected
boot-repair-common version : 3.0-0ppa7~natty
LIVESESSION is : yes
BYTES_BEFORE_PART[1] (sda) = 34 sectors * 512 bytes = 17408 bytes.
OSPROBER: /dev/sda2:Ubuntu 11.04 (11.04):Ubuntu:linux
BLKID: /dev/loop0: TYPE="squashfs"
/dev/sda1: SEC_TYPE="msdos" UUID="3E7D-3A4E" TYPE="vfat"
/dev/sda2: UUID="35ced8ec-85b9-4aef-80a1-9cd880a920e6" TYPE="ext4"
/dev/sda3: UUID="dfb1f846-6422-4ddc-8147-07d16d7248cb" TYPE="swap"
/dev/sdb1: SEC_TYPE="msdos" LABEL="PENDRIVE" UUID="E0FD-1813" TYPE="vfat"
sda2 contains Ubuntu 11.04 (linux)
1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
Total of 1 OS detected on sda disk.
sda contains minimum one OS
EFI_OF_PART[2]  (# )

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

FDISK
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT

Disk /dev/sdb: 1006 MB, 1006108672 bytes
24 heads, 23 sectors/track, 3559 cylinders, total 1965056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         248     1965055      982404    6  FAT16

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
LIST_GPTPART[1] is 1 (sda1 , sda)

Disk /dev/sdb: 1006 MB, 1006108672 bytes
24 heads, 23 sectors/track, 3559 cylinders, total 1965056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         248     1965055      982404    6  FAT16
sda1 : sda, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda1, no-os, gpt, no-fstab.
sda2 : sda, not-sepboot, grub, aptget, 64, with boot, /mnt/clean/sda2, with-os, no-gpt, fstab-efi.
PARTED: Model: ATA ST3500514NS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      17.4kB  20.0MB  20.0MB  fat16                 boot
2      20.0MB  496GB   496GB   ext4                  boot
3      496GB   500GB   4111MB  linux-swap(v1)


Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdb: 1006MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
1      127kB  1006MB  1006MB  primary  fat16        boot
MOUNT aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/clean/sda1 type vfat (rw)
/dev/sda2 on /mnt/clean/sda2 type ext4 (rw)
/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  agpgart autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency disk dri dvd ecryptfs fb0 fd full fuse hidraw0 hidraw1 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem pktcdvd port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda3 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout tpm0 uinput urandom usbmon0 usbmon1 usbmon2 vga_arbiter zero
/dev/mapper:  control

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

DF Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    1.9G  101M  1.8G   6% /
none      devtmpfs    1.9G  656K  1.9G   1% /dev
/dev/sdb1     vfat    960M  702M  258M  74% /cdrom
/dev/loop0
squashfs    665M  665M     0 100% /rofs
none         tmpfs    1.9G  112K  1.9G   1% /dev/shm
tmpfs        tmpfs    1.9G  184K  1.9G   1% /tmp
none         tmpfs    1.9G   92K  1.9G   1% /var/run
none         tmpfs    1.9G     0  1.9G   0% /var/lock
/dev/sda1     vfat     19M  127K   19M   1% /mnt/clean/sda1
/dev/sda2     ext4    455G  3.1G  429G   1% /mnt/clean/sda2
FDISK
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT

Disk /dev/sdb: 1006 MB, 1006108672 bytes
24 heads, 23 sectors/track, 3559 cylinders, total 1965056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         248     1965055      982404    6  FAT16
Logs saved into /mnt/clean/sda2/var/log/clean/log/2011-09-23__19h24boot-repair51
combobox_ostoboot_bydefault_fillin
Order Linux according to their /boot type noorder
combobox_efi_fillin sda2
combobox_separateboot_fillin
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
separate_bootpart and efi show_hide sda2
efi_show_hide 2 (no-gpt)
combobox_efi_fillin sda2
set_radiobutton_place_grub
separate_bootpart and efi show_hide sda2
efi_show_hide 2 (no-gpt)
combobox_efi_fillin sda2
************************Before mainwindow appear
PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 2 (sda2)
FSCK_ACTION yes PASTEBIN_ACTION no
REINSTALL_POSSIBLE yes MBR_ACTION reinstall UNHIDEBOOT_ACTION yes (10.s)
PART_TO_REINSTALL_GRUB 2 (sda2) FORCE_GRUB no NOFORCE_DISK sda REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sda1) grub-pc (sda1)
/usr/share/clean/cleancommon-gui.sh: line 591:  9531 Terminated              while true; do
done
RETOURCOMBO_purge_grub : sda2 (Ubuntu 11.04)
RETOURCOMBO_ostoboot_bydefault : sda2 (Ubuntu 11.04)
separate_bootpart and efi show_hide sda2
efi_show_hide 2 (no-gpt)
combobox_efi_fillin sda2
RETOURCOMBO_efi (EFIPART_TO_USE) : sda1
RETOURCOMBO_place_grub (NOFORCE_DISK) : sda
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sda1
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
separate_bootpart and efi show_hide sda2
efi_show_hide 2 (no-gpt)
combobox_efi_fillin sda2
set_radiobutton_place_grub
separate_bootpart and efi show_hide sda2
efi_show_hide 2 (no-gpt)
combobox_efi_fillin sda2
RETOURCOMBO_place_grub (NOFORCE_DISK) : sda
RETOURCOMBO_efi (EFIPART_TO_USE) : sda1
RETOURCOMBO_efi (EFIPART_TO_USE) : sda1
RETOURCOMBO_efi (EFIPART_TO_USE) : sda1
separate_bootpart and efi show_hide sda2
efi_show_hide 2 (no-gpt)
combobox_efi_fillin sda2
RETOURCOMBO_efi (EFIPART_TO_USE) : sda1
internet: connected
************************Before Repairing
PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 2 (sda2)
FSCK_ACTION no PASTEBIN_ACTION yes
REINSTALL_POSSIBLE yes MBR_ACTION purge UNHIDEBOOT_ACTION yes (10.s)
PART_TO_REINSTALL_GRUB 2 (sda2) FORCE_GRUB no NOFORCE_DISK sda REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sda1) grub-efi (sda1)
Freed space function
/dev/sda2            476751400   3165524 449368252   1% /mnt/clean/sda2
internet: connected
Purge the GRUB of sda2
Unmount (force) all OS partitions except / and partition where we reinstall GRUB (sda2)
mount EFI boot /mnt/clean/sda1
Mounted the EFI partition /dev/sda1 on /mnt/clean/sda2/boot/efi
Activate all repositories in /mnt/clean/sda2/etc/apt/sources.list
dpkg_function
internet: connected
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security InRelease
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty InRelease
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates InRelease
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports InRelease
Ign [http://archive.canonical.com]("http://archive.canonical.com/") natty InRelease
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty InRelease
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security Release.gpg
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty Release.gpg
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates Release.gpg
Get:1 [http://archive.canonical.com]("http://archive.canonical.com/") natty Release.gpg [198 B]
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty Release.gpg
Get:2 [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports Release.gpg [198 B]
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security Release
Get:3 [http://archive.canonical.com]("http://archive.canonical.com/") natty Release [5,916 B]
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty Release
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty Release
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates Release
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main Sources
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main Sources
Get:4 [http://archive.canonical.com]("http://archive.canonical.com/") natty/partner amd64 Packages [7,513 B]
Get:5 [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports Release [23.3 kB]
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main amd64 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted amd64 Packages
Hit [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main amd64 Packages
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main TranslationIndex
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe amd64 Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse amd64 Packages
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main TranslationIndex
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse TranslationIndex
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted TranslationIndex
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe TranslationIndex
Ign [http://archive.canonical.com]("http://archive.canonical.com/") natty/partner TranslationIndex
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/main Sources
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/restricted Sources
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/universe Sources
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/multiverse Sources
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/main amd64 Packages
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/multiverse amd64 Packages
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/main TranslationIndex
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/multiverse TranslationIndex
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/restricted TranslationIndex
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/universe TranslationIndex
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/main Sources
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/universe Sources
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/main amd64 Packages
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/multiverse amd64 Packages
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/main TranslationIndex
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/multiverse TranslationIndex
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/restricted TranslationIndex
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/universe TranslationIndex
Get:6 [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/main amd64 Packages [2,150 B]
Get:7 [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/restricted amd64 Packages [14 B]
Get:8 [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/universe amd64 Packages [14.0 kB]
Get:9 [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/multiverse amd64 Packages [1,473 B]
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/main TranslationIndex
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/multiverse TranslationIndex
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/restricted TranslationIndex
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/universe TranslationIndex
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main Translation-en_US
Ign [http://archive.canonical.com]("http://archive.canonical.com/") natty/partner Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/main Translation-en
Ign [http://extras.ubuntu.com]("http://extras.ubuntu.com/") natty/main Translation-en
Ign [http://archive.canonical.com]("http://archive.canonical.com/") natty/partner Translation-en
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/restricted Translation-en
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") natty-security/universe Translation-en
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/main Translation-en_US
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/main Translation-en
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/multiverse Translation-en_US
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/restricted Translation-en
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/universe Translation-en_US
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty/universe Translation-en
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/main Translation-en_US
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/main Translation-en
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/multiverse Translation-en_US
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/restricted Translation-en
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/universe Translation-en_US
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-updates/universe Translation-en
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/main Translation-en_US
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/main Translation-en
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/multiverse Translation-en_US
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/multiverse Translation-en
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/restricted Translation-en_US
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/restricted Translation-en
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/universe Translation-en_US
Ign [http://ca.archive.ubuntu.com]("http://ca.archive.ubuntu.com/") natty-backports/universe Translation-en

VALIDSOURCE   Candidate: 1.99~rc1-13ubuntu3
grub-install (GRUB) 1.99~rc1-13ubuntu3
/usr/share/clean/cleancommon-gui.sh: line 135: 12900 Terminated              while true; do
done
internet: connected
internet: connected
Restore the original repositories in /mnt/clean/sda2/etc/apt/sources.list
Force mount all OS partitions for the logs
Unhide boot menu (10 seconds) if Wubi detected
internet: connected
E: Unable to locate package pastebinit
Activate all repositories in /etc/apt/sources.list
dpkg-preconfigure: unable to re-open stdin:
Restore the original repositories in ....
```

Any help would be MUCH appreciated!!

---

### Post by oldfred on 2011-09-27
Welcome to the forums.

Please use code tags to make long script postings easier to read. From a reply or edit (advanced mode) the # in the edit panel adds code tags to highlighted areas. 
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

Are you using UEFI to boot (it looks that way). The boot script does not fully parse an EFI partition to show boot files in the efi partition. You also seem to have the efi boot flag on sda2 which is not correct.

I do not really know UEFI but saved a few links to get you started. Only a few here do know UEFI if that is how you are booting.

EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)

How boot a (U)EFI system natively (without BIOS CSM) using GRUB 2
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Arch is not Ubuntu but has some info on efi and grub2.
Grub2 efi info ArchLinux
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

If you're using EFI mode to boot, you don't need a BIOS Boot Partition, but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

---

### Post by rochte on 2011-09-27
Thank you for the posting instructions and also the information about UEFI booting.  UEFI is apparently what was throwing me off - I don't know beans about it and apparently this install used it as the default.  I'll check the links, do some work and report back.

---

### Post by collisionystm on 2011-09-27
If you are trying to install with multiple hard drives in your computer, unplug all except the one you are installing on and try again. It will work.

---

### Post by srs5694 on 2011-09-27
I think oldfred is probably on the right track in thinking the system boots using UEFI, but I can't be positive of that. In addition to the pointers he provided, I can suggest:


[list]
[*]Use gdisk or a libparted-based tool to set the partition type on /dev/sda2 correctly. It's currently set as an EFI System Partition (ESP), but it clearly is not that; it appears to be a Linux installation partition. In gdisk, you should set its type code to 8300 or to 0700; in a libparted-based tool, you should remove the "boot flag" (which should be set *only* on an ESP). This issue is not what's causing the system to not boot, but correcting it is important so that you don't accidentally trash the Linux installation partition when installing a future OS.
[*]You might consult my [Managing EFI Boot Loaders for Linux](http://www.rodsbooks.com/efi-bootloaders/index.html) Web page, which describes EFI boot loaders in detail. Installing ELILO or Fedora's patched GRUB Legacy may be the quickest way to get the system booting, but be aware that you'll need to do some extra work whenever you upgrade your kernel if you use one of these boot loaders in the long run.
[*]It's possible that the installer didn't install a boot loader at all. If so, installing the grub-efi package should do the trick. It's possible to do this from the installation disc, but I don't know the exact steps offhand. I would recommend instead installing ELILO or GRUB Legacy to get your system to boot in a basic way and then use the normal installation to install grub-efi. The only advantage of doing this over just using ELILO or GRUB Legacy indefinitely is that Ubuntu should automatically handle boot loader updates after kernel upgrades.
[*]As an alternative to fixing your current installation, you could re-install the system. This *should* work, but you've got to be careful to identify the ESP to the boot loader if you use the manual partitioning option. IIRC, you've got to tell the installer to use the ESP as an "EFI boot partition," but I don't recall the exact buttons you click to do this.
[/list]

---

### Post by MAFoElffen on 2011-09-27
> **srs5694 said:**
> I think oldfred is probably on the right track in thinking the system boots using UEFI, but I can't be positive of that. In addition to the pointers he provided, I can suggest:


[LIST]
[*]Use gdisk or a libparted-based tool to set the partition type on /dev/sda2 correctly. It's currently set as an EFI System Partition (ESP), but it clearly is not that; it appears to be a Linux installation partition. In gdisk, you should set its type code to 8300 or to 0700; in a libparted-based tool, you should remove the "boot flag" (which should be set *only* on an ESP). This issue is not what's causing the system to not boot, but correcting it is important so that you don't accidentally trash the Linux installation partition when installing a future OS.
[*]You might consult my [Managing EFI Boot Loaders for Linux]("http://www.rodsbooks.com/efi-bootloaders/index.html") Web page, which describes EFI boot loaders in detail. Installing ELILO or Fedora's patched GRUB Legacy may be the quickest way to get the system booting, but be aware that you'll need to do some extra work whenever you upgrade your kernel if you use one of these boot loaders in the long run.
[*]It's possible that the installer didn't install a boot loader at all. If so, installing the grub-efi package should do the trick. It's possible to do this from the installation disc, but I don't know the exact steps offhand. I would recommend instead installing ELILO or GRUB Legacy to get your system to boot in a basic way and then use the normal installation to install grub-efi. The only advantage of doing this over just using ELILO or GRUB Legacy indefinitely is that Ubuntu should automatically handle boot loader updates after kernel upgrades.
[*]As an alternative to fixing your current installation, you could re-install the system. This *should* work, but you've got to be careful to identify the ESP to the boot loader if you use the manual partitioning option. IIRC, you've got to tell the installer to use the ESP as an "EFI boot partition," but I don't recall the exact buttons you click to do this.
[/LIST]

Of course then there's what the user said and implied-- That he/she thought they did a generic install with default options:
> 
  UEFI is apparently what was throwing me off - [COLOR=Red]I don't know beans about it and apparently this install used it as the default.[/COLOR]

Having said that and srs5694 having suggested a reinstall (as one option), another otpion would be to reinstall with EXT4... Just an observation.

---

### Post by srs5694 on 2011-09-27
> **MAFoElffen said:**
> Of course then there's what the user said and implied-- That he/she thought they did a generic install with default options:

> UEFI is apparently what was throwing me off - [COLOR=Red]I don't know beans about it and apparently this install used it as the default.[/COLOR]

An installation with default options is not inconsistent with a UEFI installation. The installer will boot into either BIOS mode or UEFI mode depending on firmware capabilities, firmware settings, and user actions at boot time, and will then install in whatever mode was used for the boot. The reasons I think this was probably a UEFI installation are:


[list]
[*]The installation disk is 500 GB in size but uses GPT. This can happen either because the disk was completely blank and the installer ran in UEFI mode or because the user pre-partitioned the disk with GPT (which rochte did not mention doing) and then did a BIOS-mode install. Faced with a blank disk, the Ubuntu installer will use MBR, not GPT, on a 500 GB disk.
[*]The disk is partitioned with a tiny ~19 MiB EFI System Partition (ESP). This is consistent with what the Ubuntu installer does when booted in UEFI mode. If the system were installed in BIOS mode, the user would have to have set this up manually, which rochte did not mention doing. (BTW, ~19 MiB really is dinky for an ESP. If re-installing, I recommend manually creating an ESP in the 200-300 MiB range.)
[*]The ESP uses FAT-16, which is consistent with what the Ubuntu installer does in UEFI mode.
[*]GRUB 2 is not installed to the MBR of the disk. This is consistent with a UEFI installation, but Ubuntu normally installs GRUB 2 to the MBR of the disk on a BIOS installation. OTOH, the MBR does contain Syslinux, which I don't believe is normal on a UEFI installation -- but this could be left over from some previous install, or maybe the Ubuntu installer is doing something I just don't know about. In any event, this point is pretty weak evidence one way or the other, but on the whole I think it's more consistent with a UEFI installation than with a BIOS installation.
[/list]


Overall, I'd say that either the Ubuntu installer ran in UEFI mode on an empty disk or rochte made some very peculiar manual partitioning choices before installing Ubuntu in BIOS mode. If the latter, I encourage rochte to describe why those choices were made because a BIOS-mode installation on a GPT disk works best with some slightly different options (such as a BIOS Boot Partition instead of an ESP).

> Having said that and srs5694 having suggested a reinstall (as one  option), another otpion would be to reinstall with EXT4... Just an  observation.

According to the Boot Info Script output, the current installation already uses ext4fs:

> ```
sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

```

Filesystem choice should not affect the system's bootability, although I don't claim to have tested every possibility in Ubuntu, so I can't promise that's true.

---

### Post by oldfred on 2011-09-27
@MAFoElffen
It is not a format issue but a BIOS/UEFI motherboard issue. But your suggestion of reinstalling is a possibility. UEFI is new and grub2 still has some issues. But most new systems have a BIOS boot mode hidden away somewhere for compatibly with older systems.

I have BIOS but used gpt which is a newer improved partitioning system over MBR(msdos). But then you also need a bios_grub partition to install in BIOS mode with gpt.

So OP can work to make UEFI work, some have had better success than others which seems to be more the motherboard's UEFI configurations.
Or change to BIOS mode and install with gpt partiitons.
Or revert to all the old way and use BIOS & MBR.

Lots of choices, sometimes the old way may seem the easiest but at some point we have to convert.

---

