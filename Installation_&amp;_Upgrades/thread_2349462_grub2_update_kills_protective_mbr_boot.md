---
title: "grub2 update kills protective mbr boot"
date: 2017-01-15
forum: Installation &amp; Upgrades
---

### Post by efiLabs on 2017-01-15
a friendly but slightly desperate hello :

did recent kubuntu 1604 LTS update / upgrade containing grub2 update ... now system won't boot anymore

AMD64 with 300 GB intel SSD (/boot sda1, / sda2) and two 3 TB drives in raid1 (/home / usr_local, sdb, sdc)

the intel 300 GB SSD forced a protective mbr / gpt setup upon the kubuntu 1604 LTS install, which causes all these boot issues, the raid1 (home, usr_local) runs fine for 2 years now, only the SSD looses sometimes boot-ability after a clonezilla backup SSD swap with an external 2nd identical backup drive ... i somehow fixed it always, but don't remember details)

now i can't trace anything to fix to the following error messages produced by running boot-info

boot-repair can't fix it and complains about an additional > 1MB partition, which i don't have and which wasn't necessary before ... IT WORKED, only the kubuntu grub system update killed it ... so boot-repair won't help

here are a few excerpts for the boot info :

Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector
317944 of the same hard drive for core.img, but core.img can not be found
at this location

contrary to this 1st message the following2nd message seems to contain this core.img

Grub2 (v2.00) is installed in the boot sector of sda1
and looks at sector 309712 of the same hard drive for
core.img. core.img is at this location and looks for (,gpt1)/grub

i suspect that the mbr / gpt got altered to boot from sda2 now instead of sda1, but i can't trace or verify sectors 317944 and 309712 for validity

are there any tools or tricks available to dive a bit deeper into this or just simply fix it


i stripped parts of the debug info since i had problems submitting this report

```

Boot Info Script cfd9efe + Boot-Repair extra info [Boot-Info 26Apr2016]
============================= Boot Info Summary: ===============================
=> Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector
317944 of the same hard drive for core.img, but core.img can not be found
at this location.
=> libparted MBR boot code is installed in the MBR of /dev/sdb.
=> libparted MBR boot code is installed in the MBR of /dev/sdc.
=> Syslinux MBR (4.04-4.07) is installed in the MBR of /dev/sdd.
sda1: __________________________________________________________________________
File system: ext4
Boot sector type: Grub2 (v1.99-2.00)
Boot sector info: Grub2 (v2.00) is installed in the boot sector of sda1
and looks at sector 309712 of the same hard drive for
core.img. core.img is at this location and looks for
(,gpt1)/grub. It also embeds following components:
modules
-------------------------------------------------------
fshelp ext2 part_gpt biosdisk
-------------------------------------------------------
Operating System:
Boot files: /grub/grub.cfg /grub/i386-pc/core.img
sda2: __________________________________________________________________________
File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 16.04.1 LTS
Boot files: /etc/fstab
sdb1: __________________________________________________________________________
File system: linux_raid_member
Boot sector type: -
Boot sector info:
sdb2: __________________________________________________________________________
File system: linux_raid_member
Boot sector type: -
Boot sector info:
sdc1: __________________________________________________________________________
File system: linux_raid_member
Boot sector type: -
Boot sector info:
sdc2: __________________________________________________________________________
File system: linux_raid_member
Boot sector type: -
Boot sector info:
sdd1: __________________________________________________________________________
File system: vfat
Boot sector type: SYSLINUX 4.07 2013-07-25
Boot sector info: Syslinux looks at sector 14709808 of /dev/sdd1 for
its second stage. SYSLINUX is installed in the /uui
directory. No errors found in the Boot Parameter Block.
Operating System:
Boot files: /boot/grub/grub.cfg /casper/vmlinuz.efi
/EFI/BOOT/grubx64.efi
============================ Drive/Partition Info: =============================
Drive: sda _____________________________________________________________________
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Partition Boot Start Sector End Sector # of Sectors Id System
/dev/sda1 1 468,862,127 468,862,127 ee GPT
GUID Partition Table detected.
Partition Attrs Start Sector End Sector # of Sectors System
/dev/sda1 2,048 1,050,623 1,048,576 EFI System partition
/dev/sda2 1,050,624 468,860,927 467,810,304 Data partition (Linux)
Attributes: R=Required, N=No Block IO, B=Legacy BIOS Bootable, +=More bits set
Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Partition Boot Start Sector End Sector # of Sectors Id System
/dev/sdb1 16,065 2,150,428,769 2,150,412,705 83 Linux
/dev/sdb2 2,150,428,770 5,860,528,064 3,710,099,295 83 Linux
Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Partition Boot Start Sector End Sector # of Sectors Id System
/dev/sdc1 63 2,150,412,704 2,150,412,642 83 Linux
/dev/sdc2 2,150,412,705 5,860,528,064 3,710,115,360 83 Linux
Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 7.2 GiB, 7740641280 bytes, 15118440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Partition Boot Start Sector End Sector # of Sectors Id System
/dev/sdd1 * 2,048 15,116,287 15,114,240 b W95 FAT32
"blkid" output: ________________________________________________________________
Device UUID TYPE LABEL
/dev/loop0 squashfs
/dev/sda1 64783d52-b6a7-4c1a-82eb-b86dcb7229ce ext4
/dev/sda2 666c7b86-8bb8-448b-8386-72af7f36d11b ext4
/dev/sdb1 6596d6b1-9892-5dd8-0d75-2946ce8169de linux_raid_member davinci:1
/dev/sdb2 f4e2d428-1ef8-34fb-9150-ca01b7b522fc linux_raid_member davinci:2
/dev/sdc1 6596d6b1-9892-5dd8-0d75-2946ce8169de linux_raid_member davinci:1
/dev/sdc2 f4e2d428-1ef8-34fb-9150-ca01b7b522fc linux_raid_member davinci:2
/dev/sdd1 7E29-89CF vfat UUI
========================= "ls -l /dev/disk/by-id" output: ======================
total 0
lrwxrwxrwx 1 root root 9 Jan 15 02:36 ata-ASUS_DRW-24B1ST_i_DBD0CL090828 -> ../../sr0
lrwxrwxrwx 1 root root 9 Jan 15 02:43 ata-INTEL_SSDSC2BW240A4_CVDA340605PJ2403GN -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 15 02:43 ata-INTEL_SSDSC2BW240A4_CVDA340605PJ2403GN-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan 15 02:43 ata-INTEL_SSDSC2BW240A4_CVDA340605PJ2403GN-part2 -> ../../sda2
lrwxrwxrwx 1 root root 9 Jan 15 02:43 ata-ST3000DM001-1CH166_Z1F3ZBKM -> ../../sdb
lrwxrwxrwx 1 root root 10 Jan 15 02:43 ata-ST3000DM001-1CH166_Z1F3ZBKM-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jan 15 02:43 ata-ST3000DM001-1CH166_Z1F3ZBKM-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 9 Jan 15 02:43 ata-ST3000DM001-1CH166_Z1F41XNH -> ../../sdc
lrwxrwxrwx 1 root root 10 Jan 15 02:43 ata-ST3000DM001-1CH166_Z1F41XNH-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Jan 15 02:43 ata-ST3000DM001-1CH166_Z1F41XNH-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 9 Jan 15 02:43 usb-13fe_USB_DISK_2.0_C5005665C2585272-0:0 -> ../../sdd
lrwxrwxrwx 1 root root 10 Jan 15 02:43 usb-13fe_USB_DISK_2.0_C5005665C2585272-0:0-part1 -> ../../sdd1
lrwxrwxrwx 1 root root 9 Jan 15 02:43 wwn-0x5000c500651a1c00 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jan 15 02:43 wwn-0x5000c500651a1c00-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Jan 15 02:43 wwn-0x5000c500651a1c00-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 9 Jan 15 02:43 wwn-0x5000c5006527e599 -> ../../sdc
lrwxrwxrwx 1 root root 10 Jan 15 02:43 wwn-0x5000c5006527e599-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Jan 15 02:43 wwn-0x5000c5006527e599-part2 -> ../../sdc2
lrwxrwxrwx 1 root root 9 Jan 15 02:43 wwn-0x55cd2e404b8418d0 -> ../../sda
lrwxrwxrwx 1 root root 10 Jan 15 02:43 wwn-0x55cd2e404b8418d0-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jan 15 02:43 wwn-0x55cd2e404b8418d0-part2 -> ../../sda2
================================ Mount points: =================================
Device Mount_Point Type Options
/dev/loop0 /rofs squashfs (ro,noatime)
/dev/sdd1 /cdrom vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
============================= sda1/grub/grub.cfg: ==============================
=================== sda1: Location of files loaded by Grub: ====================
GiB - GB File Fragment(s)
0.137794495 = 0.147955712 grub/grub.cfg 1
0.147705078 = 0.158597120 grub/i386-pc/core.img 1
0.234119415 = 0.251383808 vmlinuz-4.4.0-57-generic 1
0.027084351 = 0.029081600 vmlinuz-4.4.0-59-generic 1
0.407222748 = 0.437252096 initrd.img-4.4.0-57-generic 3
0.291061401 = 0.312524800 initrd.img-4.4.0-59-generic 3
=============================== sda2/etc/fstab: ================================
--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda2 during installation
UUID=666c7b86-8bb8-448b-8386-72af7f36d11b / ext4 errors=remount-ro 0 1
# /boot was on /dev/sda1 during installation
UUID=64783d52-b6a7-4c1a-82eb-b86dcb7229ce /boot ext4 defaults 0 2
# swap was on /dev/sda3 during installation
#UUID=f288e447-5ec8-4aa6-8de6-00d1fa4e2a63 none swap sw 0 0
# /home connect to /dev/md1
/dev/md/1 /home ext4 defaults 0 2
# /usr/local connect to /dev/md2
/dev/md/2 /usr/local ext4 defaults 0 2
--------------------------------------------------------------------------------
=========================== sdd1/boot/grub/grub.cfg: ===========================
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
menuentry "Start Kubuntu" {
set gfxpayload=keep
linux /casper/vmlinuz.efi file=/cdrom/preseed/kubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper maybe-ubiquity quiet splash ---
initrd /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
set gfxpayload=keep
linux /casper/vmlinuz.efi file=/cdrom/preseed/kubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true ---
initrd /casper/initrd.lz
}
menuentry "Check disc for defects" {
set gfxpayload=keep
linux /casper/vmlinuz.efi cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash ---
initrd /casper/initrd.lz
}
--------------------------------------------------------------------------------
=================== sdd1: Location of files loaded by Grub: ====================
GiB - GB File Fragment(s)
?? = ?? boot/grub/grub.cfg 1
=============================== StdErr Messages: ===============================
File descriptor 9 (/proc/10717/mounts) leaked on lvs invocation. Parent PID 20051: bash
File descriptor 63 (pipe:[121465]) leaked on lvs invocation. Parent PID 20051: bash
ADDITIONAL INFORMATION :
=================== log of boot-info 2017-01-15__02h43 ===================
boot-info version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
BLKID BEFORE RAID ACTIVATION:
/dev/sda1: UUID="64783d52-b6a7-4c1a-82eb-b86dcb7229ce" TYPE="ext4" PTTYPE="dos" PARTUUID="2352ef23-ab2d-499c-be1b-ba7646376712"
/dev/sda2: UUID="666c7b86-8bb8-448b-8386-72af7f36d11b" TYPE="ext4" PARTUUID="942b4b32-ba6b-476e-bea3-9482f4fbbc3a"
/dev/sdc1: UUID="6596d6b1-9892-5dd8-0d75-2946ce8169de" UUID_SUB="f99a705c-3f36-16ed-3eda-9a40f733c339" LABEL="davinci:1" TYPE="linux_raid_member" PARTUUID="000e8815-01"
/dev/sdc2: UUID="f4e2d428-1ef8-34fb-9150-ca01b7b522fc" UUID_SUB="585728f5-77e9-0845-752e-2f422dcdec0d" LABEL="davinci:2" TYPE="linux_raid_member" PARTUUID="000e8815-02"
/dev/sdd1: LABEL="UUI" UUID="7E29-89CF" TYPE="vfat" PARTUUID="4e199a42-01"
/dev/loop0: TYPE="squashfs"
/dev/sdb1: UUID="6596d6b1-9892-5dd8-0d75-2946ce8169de" UUID_SUB="2cf3fe2b-ea46-559e-9590-1797780d1eb7" LABEL="davinci:1" TYPE="linux_raid_member" PARTUUID="000c5ac9-01"
/dev/sdb2: UUID="f4e2d428-1ef8-34fb-9150-ca01b7b522fc" UUID_SUB="d542ed98-e58f-c3ef-924b-fc7ab31b861c" LABEL="davinci:2" TYPE="linux_raid_member" PARTUUID="000c5ac9-02"
dmraid -si -c: no raid disks
No DMRAID disk.
RAID detected. You may want to retry after installing the [mdadm] packages. (sudo apt-get install -y --force-yes mdadm --no-install-recommends)
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Warning: no DMRAID nor MD_ARRAY.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
boot-info is executed in live-session (Ubuntu 16.04.1 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s): 32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/kubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper maybe-ubiquity quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory
Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
=================== os-prober:
/dev/sda2:Ubuntu 16.04.1 LTS (16.04):Ubuntu:linux
=================== blkid:
/dev/sda1: UUID="64783d52-b6a7-4c1a-82eb-b86dcb7229ce" TYPE="ext4" PTTYPE="dos" PARTUUID="2352ef23-ab2d-499c-be1b-ba7646376712"
/dev/sda2: UUID="666c7b86-8bb8-448b-8386-72af7f36d11b" TYPE="ext4" PARTUUID="942b4b32-ba6b-476e-bea3-9482f4fbbc3a"
/dev/sdc1: UUID="6596d6b1-9892-5dd8-0d75-2946ce8169de" UUID_SUB="f99a705c-3f36-16ed-3eda-9a40f733c339" LABEL="davinci:1" TYPE="linux_raid_member" PARTUUID="000e8815-01"
/dev/sdc2: UUID="f4e2d428-1ef8-34fb-9150-ca01b7b522fc" UUID_SUB="585728f5-77e9-0845-752e-2f422dcdec0d" LABEL="davinci:2" TYPE="linux_raid_member" PARTUUID="000e8815-02"
/dev/sdd1: LABEL="UUI" UUID="7E29-89CF" TYPE="vfat" PARTUUID="4e199a42-01"
/dev/loop0: TYPE="squashfs"
/dev/sdb1: UUID="6596d6b1-9892-5dd8-0d75-2946ce8169de" UUID_SUB="2cf3fe2b-ea46-559e-9590-1797780d1eb7" LABEL="davinci:1" TYPE="linux_raid_member" PARTUUID="000c5ac9-01"
/dev/sdb2: UUID="f4e2d428-1ef8-34fb-9150-ca01b7b522fc" UUID_SUB="d542ed98-e58f-c3ef-924b-fc7ab31b861c" LABEL="davinci:2" TYPE="linux_raid_member" PARTUUID="000c5ac9-02"
1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
The size of this disk is 2.7 TiB (3000592982016 bytes). DOS partition table format can not be used on drives for volumes larger than 2199023255040 bytes for 512-byte sectors. Use GUID partition table format (GPT).
The size of this disk is 2.7 TiB (3000592982016 bytes). DOS partition table format can not be used on drives for volumes larger than 2199023255040 bytes for 512-byte sectors. Use GUID partition table format (GPT).
Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
=================== sda2/etc/grub.d/ :
drwxr-xr-x 3 root root 4096 Jan 10 21:06 grub.d
total 80
-rwxr-xr-x 1 root root 9791 Jun 17 2016 00_header
-rwxr-xr-x 1 root root 6258 Mar 15 2016 05_debian_theme
-rwxr-xr-x 1 root root 12261 Jun 17 2016 10_linux
-rwxr-xr-x 1 root root 11082 Jun 17 2016 20_linux_xen
-rwxr-xr-x 1 root root 1992 Jan 28 2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 Jun 17 2016 30_os-prober
-rwxr-xr-x 1 root root 1418 Jun 17 2016 30_uefi-firmware
-rwxr-xr-x 1 root root 214 Jun 17 2016 40_custom
-rwxr-xr-x 1 root root 216 Jun 17 2016 41_custom
drwxr-xr-x 4 root root 4096 Aug 18 00:44 backup
-rw-r--r-- 1 root root 483 Jun 17 2016 README
=================== sda2/etc/default/grub :
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
# info -f grub -n 'Simple configuration'
GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL="console"
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"
# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"
# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
/boot detected in the fstab of sda2: UUID=64783d52-b6a7-4c1a-82eb-b86dcb7229ce (sda1)

/dev/sda2 1050624 468860927 467810304 223.1G Linux filesystem
Disk /dev/sdb: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x000c5ac9
Device Boot Start End Sectors Size Id Type
/dev/sdb1 16065 2150428769 2150412705 1T 83 Linux
/dev/sdb2 2150428770 5860528064 3710099295 1.7T 83 Linux
Disk /dev/sdc: 2.7 TiB, 3000592982016 bytes, 5860533168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x000e8815
Device Boot Start End Sectors Size Id Type
/dev/sdc1 63 2150412704 2150412642 1T 83 Linux
/dev/sdc2 2150412705 5860528064 3710115360 1.7T 83 Linux
Disk /dev/sdd: 7.2 GiB, 7740641280 bytes, 15118440 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4e199a42
Device Boot Start End Sectors Size Id Type
/dev/sdd1 * 2048 15116287 15114240 7.2G b W95 FAT32
(debug) reinstall grub2 place-in-all-MBRs no-BIOS_boot (sda2)
=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to enable-raid) and reinstall the grub2 of sda2 into the MBRs of all disks (except USB without OS), using the following options: sda1/boot,
Additional repair would be performed: unhide-bootmenu-10s
=================== Blockers in case of suggested repair
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
=================== Advice in case of suggested repair
The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?
=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sda (240GB) disk!
=================== User settings
The settings chosen by the user will not act on the boot.

```

---

### Post by yancek on 2017-01-15
You have a mixed MBR/UEFI install.  At the top, the bootinfoscript shows Grub boot code in the MBR.  The output further down clearly shows an EFI partition (sda1) so you should not have any boot code in the MBR and the BIOS should be set to boot EFI.  At the bottom of the output, it indicates the boot of the PC is in EFI mode but no EFI partition was detected even though and EFI shows clearly near the beginning of the output (sda1).  Maybe you could try running boot repair again selecting to Create BootInfo Summary and then post a link to that output here as instructed rather than uploading to this site.

More details are probably needed and hopefully someone will be able to assist.

---

### Post by oldfred on 2017-01-15
You clearly show the ESP - efi system partition as sda1, but Boot-Repair says it cannot find it.
It may also need repair.

       [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185) 

Grub could be forced to install into a PBR or MBR but has to use blocklists which are unreliable. Maybe it does not let you do that anymore.

With gpt partitioning you can boot in either UEFI or BIOS boot mode, but need the correct supporting partition.
I normally add both the ESP & the bios_grub to every new or totally reformatted drive and larger flash drives as first two partitions.
UEFI suggest ESP be first partition, but Windows often makes it second or third. Grub says bios_grub can be anywhere on drive.

      
 Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)

---

