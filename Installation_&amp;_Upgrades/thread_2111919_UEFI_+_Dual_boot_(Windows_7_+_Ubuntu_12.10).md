---
title: "UEFI + Dual boot (Windows 7 + Ubuntu 12.10)"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by blacar on 2013-02-03
Hello,

I've seen several post with different problems related UEFI and dual boot. I've tried several of the answers but still i cannot e able to install Ubuntu in dul boot with windows 7. I hope someone could help me.

The problem i have is that Ubuntu installer does not recognize disk partitions. I hows that disk is empty.

This is on ASUS A55V with 1HDD. booting in UEFI mode. Windows 7 installed

I've downloaded Ubuntu 12.10 and created a USB image that i can boot. I can boot this Ubuntu from USB disk on UEFI mode but even i cannot see any partition in the HDD.

Please help :P

---

### Post by oldfred on 2013-02-03
Welcome to the forums.

Is this also an Ultrabook which has Intel SRT?

Install Boot-Repair into your liveCD and run the BootInfo report.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
    
Another Asus thread.
       ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
       Asus N56VJ-SH71-CD - shows partitions after install
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

    
    
Older info:
       Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)> 
(Phoenix Tiano). The every-other boot problem is a bit decieving: What happens is it hangs on a warm/reboot. Boots work every time from cold/power-up. Yes, a stand-alone install of Win 7 SP1 has the exact same problem as Ubuntu. I suspect this is a Phoenix/Acer issue but who knows.
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg

    

---

### Post by blacar on 2013-02-03
Hi!

Thank you for helping!

It is not an ultrabook.
I cannot follow some other threads because i want to preserve the data in my actual W7 partitions.

The problem is that gparted is not able to deal with the partitions, it shows Error: Unable to satisfy all constraints on the partition.

Here is the boot-repair log:
```

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bootx64.efi /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.........o9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:  Syslinux looks at sector 3719872 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /casper/vmlinuz.efi.signed /efi/boot/grubx64.efi 
                       /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       411,647       409,600 EFI System partition
/dev/sda2         411,648       673,791       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         673,792   391,383,039   390,709,248 Data partition (Windows/Linux)
/dev/sda4     391,383,040   832,929,791   441,546,752 Data partition (Windows/Linux)
/dev/sda5     925,575,168   976,773,167    51,198,000 Windows Recovery Environment (Windows)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3997 MB, 3997171712 bytes
17 heads, 17 sectors/track, 27013 cylinders, total 7806976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,064     7,806,975     7,798,912   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        12A1-E70F                              vfat       SYSTEM
/dev/sda3        ACEE68DFEE68A376                       ntfs       OS
/dev/sda4        C6A8DA17A8DA0639                       ntfs       DATA
/dev/sda5        D0986D0B986CF180                       ntfs       Recovery
/dev/sdb1        A171-8771                              vfat       FLASH DRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi.signed  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append initrd=/ubninit 

label ubnentry1
menu label ^Try Ubuntu without installing
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash --

label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append initrd=/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append initrd=/ubninit 

label ubnentry6
menu label Try Ubuntu without installing
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

label ubnentry7
menu label Install Ubuntu
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --

label ubnentry8
menu label OEM install (for manufacturers)
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true --

label ubnentry9
menu label Check disc for defects
kernel /casper/vmlinuz.efi.signed
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash --

--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/4778/mounts) leaked on lvscan invocation. Parent PID 12552: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2013-02-03__19h06 ===================
boot-repair version : 3.197~ppa30~quantal
boot-sav version : 3.197~ppa30~quantal
glade2script version : 3.2.2~ppa45~quantal
boot-sav-extra version : 3.197~ppa30~quantal
boot-repair is executed in live-session (Ubuntu 12.10, quantal, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi.signed file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda3:Windows 7 (loader):Windows:chain
/dev/sda5:Windows Recovery Environment (loader):Windows1:chain

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="SYSTEM" UUID="12A1-E70F" TYPE="vfat"
/dev/sda3: LABEL="OS" UUID="ACEE68DFEE68A376" TYPE="ntfs"
/dev/sda4: LABEL="DATA" UUID="C6A8DA17A8DA0639" TYPE="ntfs"
/dev/sda5: LABEL="Recovery" UUID="D0986D0B986CF180" TYPE="ntfs"
/dev/sdb1: LABEL="FLASH DRIVE" UUID="A171-8771" TYPE="vfat"


1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi
=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="yannubuntu@gmail.com"]yannubuntu@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,     not-sepboot,    no-grubenv    nogrub,    no-docgrub,     no-update-grub,    32,    no-boot,    no-os,    is-maybe-EFI,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,     nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,     standard,    not-far,    /mnt/boot-sav/sda1.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,     no-docgrub,    no-update-grub,    32,    no-boot,    is-os,     not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,     haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,     nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda3.
sda4    : sda,    not-sepboot,    no-grubenv    nogrub,     no-docgrub,    no-update-grub,    32,    no-boot,    no-os,     not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,     no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,     nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda4.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,     no-docgrub,    no-update-grub,    32,    no-boot,    is-os,     is-maybe-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,     no-winload,    recovery-or-hidden,    bootmgr,    is-winboot,     nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,     not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda5.

sda    : GPT,    no-BIOS_boot,    has-maybe-EFI,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:


                                                                          
Error: Unable to satisfy all constraints on the partition.

Model: TDKMedia Trans-It Drive (scsi)
Disk /dev/sdb: 3997MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      4129kB  3997MB  3993MB  primary  fat32        boot, lba

=================== parted -lm:


                                                                          
Error: Unable to satisfy all constraints on the partition.

BYT;
/dev/sdb:3997MB:scsi:512:512:msdos:TDKMedia Trans-It Drive;
1:4129kB:3997MB:3993MB:fat32::boot, lba;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/ubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /mnt/boot-sav/sda4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):   alignment_offset bdi capability dev device discard_alignment events  events_async events_poll_msecs ext_range holders inflight power queue  range removable ro sda1 sda2 sda3 sda4 sda5 size slaves stat subsystem  trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device  discard_alignment events events_async events_poll_msecs ext_range  holders inflight power queue range removable ro sdb1 size slaves stat  subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device  discard_alignment events events_async events_poll_msecs ext_range  holders inflight power queue range removable ro size slaves stat  subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus  cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw  ecryptfs fb0 fb1 fd full fuse hidraw0 hpet input kmsg kvm log mapper  mcelog mei mem net network_latency network_throughput null oldmem port  ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5  sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uinput  urandom v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control
Files in /mnt/boot-sav/sda1/efi: /mnt/boot-sav/sda1/efi/ASUS/K55VD.BIN /mnt/boot-sav/sda1/efi/ASUS/K55A.BIN /mnt/boot-sav/sda1/efi/ASUS /mnt/boot-sav/sda1/efi/Boot/bootx64.efi /mnt/boot-sav/sda1/efi/Boot /mnt/boot-sav/sda1/efi/Microsoft/Boot/BCD.LOG2 /mnt/boot-sav/sda1/efi/Microsoft/Boot/BCD.LOG1 /mnt/boot-sav/sda1/efi/Microsoft/Boot/BCD.LOG /mnt/boot-sav/sda1/efi/Microsoft/Boot/BCD /mnt/boot-sav/sda1/efi/Microsoft/Boot/Fonts/wgl4_boot.ttf /mnt/boot-sav/sda1/efi/Microsoft/Boot/Fonts/kor_boot.ttf /mnt/boot-sav/sda1/efi/Microsoft/Boot/Fonts/jpn_boot.ttf /mnt/boot-sav/sda1/efi/Microsoft/Boot/Fonts/cht_boot.ttf /mnt/boot-sav/sda1/efi/Microsoft/Boot/Fonts/chs_boot.ttf /mnt/boot-sav/sda1/efi/Microsoft/Boot/Fonts /mnt/boot-sav/sda1/efi/Microsoft/Boot/BOOTSTAT.DAT /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-TW/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-TW/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-TW/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-TW /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-HK/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-HK/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-HK /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-CN/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-CN/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/zh-CN /mnt/boot-sav/sda1/efi/Microsoft/Boot/tr-TR/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/tr-TR/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/tr-TR /mnt/boot-sav/sda1/efi/Microsoft/Boot/sv-SE/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/sv-SE/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/sv-SE /mnt/boot-sav/sda1/efi/Microsoft/Boot/ru-RU/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ru-RU/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ru-RU/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ru-RU /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-PT/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-PT/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-PT/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-PT /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-BR/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-BR/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pt-BR /mnt/boot-sav/sda1/efi/Microsoft/Boot/pl-PL/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pl-PL/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/pl-PL /mnt/boot-sav/sda1/efi/Microsoft/Boot/nl-NL/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/nl-NL/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/nl-NL/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/nl-NL /mnt/boot-sav/sda1/efi/Microsoft/Boot/nb-NO/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/nb-NO/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/nb-NO /mnt/boot-sav/sda1/efi/Microsoft/Boot/memtest.efi /mnt/boot-sav/sda1/efi/Microsoft/Boot/ko-KR/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ko-KR/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ko-KR /mnt/boot-sav/sda1/efi/Microsoft/Boot/ja-JP/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ja-JP/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/ja-JP /mnt/boot-sav/sda1/efi/Microsoft/Boot/it-IT/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/it-IT/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/it-IT/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/it-IT /mnt/boot-sav/sda1/efi/Microsoft/Boot/hu-HU/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/hu-HU/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/hu-HU /mnt/boot-sav/sda1/efi/Microsoft/Boot/fr-FR/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/fr-FR/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/fr-FR/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/fr-FR /mnt/boot-sav/sda1/efi/Microsoft/Boot/fi-FI/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/fi-FI/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/fi-FI /mnt/boot-sav/sda1/efi/Microsoft/Boot/es-ES/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/es-ES/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/es-ES/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/es-ES /mnt/boot-sav/sda1/efi/Microsoft/Boot/en-US/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/en-US/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/en-US/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/en-US /mnt/boot-sav/sda1/efi/Microsoft/Boot/el-GR/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/el-GR/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/el-GR/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/el-GR /mnt/boot-sav/sda1/efi/Microsoft/Boot/de-DE/memtest.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/de-DE/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/de-DE/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/de-DE /mnt/boot-sav/sda1/efi/Microsoft/Boot/da-DK/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/da-DK/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/da-DK /mnt/boot-sav/sda1/efi/Microsoft/Boot/cs-CZ/bootmgr.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/cs-CZ/bootmgfw.efi.mui /mnt/boot-sav/sda1/efi/Microsoft/Boot/cs-CZ /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootmgr.efi /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootmgfw.efi /mnt/boot-sav/sda1/efi/Microsoft/Boot /mnt/boot-sav/sda1/efi/Microsoft /mnt/boot-sav/sda1/efi

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 04 de 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 40 06 00 11 03 00 00  00 00 00 00 02 00 00 00  |.@..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 0f e7 a1 12 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 0a 00  |........?....H..|
00000020  00 00 00 00 80 00 80 00  ff bf 49 17 00 00 00 00  |..........I.....|
00000030  00 00 0c 00 00 00 00 00  ff 9b 74 01 00 00 00 00  |..........t.....|
00000040  f6 00 00 00 01 00 00 00  76 a3 68 ee df 68 ee ac  |........v.h..h..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  [54 46 53 75 15]("tel:54%2046%2053%2075%2015") b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  [55 16 16 16 68]("tel:55%2016%2016%2016%2068") b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 54 17  |........?.....T.|
00000020  00 00 00 00 80 00 80 00  ff 77 51 1a 00 00 00 00  |.........wQ.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  39 06 da a8 17 da a8 c6  |........9.......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  [54 46 53 75 15]("tel:54%2046%2053%2075%2015") b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  [55 16 16 16 68]("tel:55%2016%2016%2016%2068") b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 2b 37  |........?....(+7|
00000020  00 00 00 00 80 00 80 00  2f 38 0d 03 00 00 00 00  |......../8......|
00000030  00 00 0c 00 00 00 00 00  82 d3 30 00 00 00 00 00  |..........0.....|
00000040  f6 00 00 00 01 00 00 00  80 f1 6c 98 0b 6d 98 d0  |..........l..m..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  [54 46 53 75 15]("tel:54%2046%2053%2075%2015") b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  [55 16 16 16 68]("tel:55%2016%2016%2016%2068") b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  2.9G  104M  2.8G   4% /
udev           devtmpfs   2.9G   12K  2.9G   1% /dev
tmpfs          tmpfs      1.2G  872K  1.2G   1% /run
/dev/sdb1      vfat       3.8G  798M  3.0G  21% /cdrom
/dev/loop0     squashfs   717M  717M     0 100% /rofs
tmpfs          tmpfs      2.9G   24K  2.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      2.9G   80K  2.9G   1% /run/shm
none           tmpfs      100M   44K  100M   1% /run/user
/dev/sda1      vfat       196M   31M  166M  16% /mnt/boot-sav/sda1
/dev/sda3      fuseblk    187G  118G   70G  63% /mnt/boot-sav/sda3
/dev/sda4      fuseblk    211G  152G   60G  72% /mnt/boot-sav/sda4
/dev/sda5      fuseblk     25G   17G  7.6G  70% /mnt/boot-sav/sda5

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7834646f

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdb: 3997 MB, 3997171712 bytes
17 heads, 17 sectors/track, 27013 cylinders, total 7806976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064     7806975     3899456    c  W95 FAT32 (LBA)



=================== Default settings
Recommended-Repair
This setting would restore the [(generic mbr)] MBR in sda, and make it boot on sda3.
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.

```

Here is the boot-repair log:

---

### Post by oldfred on 2013-02-03
Please use code tags for long outputs to make it easier to review and preserve formatting. Better to have posted link.

Nothing major wrong, but I do see this. The MBR still exists just to have an entry so old partition tools do not attempt to overwrite the new gpt table. Your gpt table looks ok, but MBR is wrong.

I might try downloading gdisk and see if it will correct it. You may have to use the w command to write new table. gpt is ok, but I think gdisk may also update MBR table.

gdisk is in repository so you can download into your live version.
sudo apt-get install gdisk

       GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by blacar on 2013-02-05
Hi oldfred,

Thank you for your help,

I am trying ...

```
Command (? for help): p
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): B1142EF0-26CB-4F15-9C42-AFC122E50E2A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 2048-sector boundaries
Total free space is 92647390 sectors (44.2 GiB)

Number  Start (sector)    End (sector)        Size                Code      Name
   1             2048            411647            200.0 MiB     EF00       EFI system partition
   2             411648           673791           128.0 MiB      0C01      Microsoft reserved part
   3             673792           391383039      186.3 GiB       0700     Basic data partition
   4              391383040      832929791     210.5 GiB       0700      Basic data partition
   5              925575168       976773167     24.4 GiB          2700     Basic data partition

Command (? for help): w

Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.
Aborting write of new partition table.

```But ... i do not understand ... secondary partition overlaps last partition?? .. it does not!

some days ago i used windows partition manager to shrink and make space between partition 4 and 5 so you can see there is a gap from      832929791 to      925575167 what i plan tu use for Ubuntu.

Do you see something else?

I do not understand what-s happening.

Thank you very much
Best regards,

---

### Post by blacar on 2013-02-05
So could this be the reason!?!?

> It is because GPT needs to store a backup copy in the last 33 sectors of  the disk. So you need to resize your last partition to make at least 33  sectors free space. I have tried, and 1 MiB is free space is enough. (1  MiB unallocated space)

---

### Post by blacar on 2013-02-05
Yes! ... this is the reason!

I ve shrinked the windows 7 recovery partition and now i was able to install Ubuntu normally. gparted and all other tools recognize my partitions now.

My problem now is that i cannot start windows 7  :O

... illl try again repairint the boot

This is my new boot-repair info

[http://paste.ubuntu.com/1613884/](http://paste.ubuntu.com/1613884/)

---

### Post by oldfred on 2013-02-05
We have seen several times where Windows does not handle gpt partitions correctly. It seems to not see the location of the back up partition table.

If you changed sizes of NTFS partitions you have to run chkdsk. If it is the boot partition Windows normally does that automatically, but you may have to manually do it for other NTFS partitions. You can only run chkdsk from the Windows repair console.

---

