---
title: "Machine does not boot after failed experiment with Ubuntu"
date: 2019-07-26
forum: Installation &amp; Upgrades
---

### Post by theimp2 on 2019-07-26
I don't recall exactly what I did.. this "failed experiment" took place a  couple of years ago, and rendered my laptop unbootable.  I didn't spend  the time at the time to try and fix it.  Now, I am.

From what I  recall, I may have tried to dual boot Windows with Ubuntu (no idea which version), with the  Ubuntu install residing on a removable USB drive.  

Regardless, here's the situation:
Machine - Dell Inspiron 1520
OS - Windows Vista
OS  disk - n/a.  The machine has a "recovery" partition on the hard drive  instead, which is also not bootable at the present time.

Desired  outcome: I'd just like to get the functionality of my laptop back!  Boot  into windows, without losing the recovery partition or the (relatively  useless) "media direct" that Dell pre-installed.

Here's the output of boot-repair, that I saw was requested for previous booting problems:
```
 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 16392 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       208,844       208,782  de Dell Utility
/dev/sda2    *        208,896    21,180,415    20,971,520   7 NTFS / exFAT / HPFS
/dev/sda3          21,180,416   229,195,775   208,015,360   7 NTFS / exFAT / HPFS
/dev/sda4         229,195,776   234,438,655     5,242,880   f W95 Extended (LBA)
/dev/sda5         229,197,824   234,438,655     5,240,832  dd Dell Media Direct


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 3.8 GiB, 4043308544 bytes, 7897087 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     7,897,086     7,895,039   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/loop7                                              squashfs   
/dev/sda1        07D7-0713                              vfat       DellUtility
/dev/sda2        60D65746D6571C1A                       ntfs       RECOVERY
/dev/sda3        10805AD3805ABEC2                       ntfs       OS
/dev/sda5        C05E-AB4C                              vfat       MEDIADIRECT
/dev/sdb1        9822-956F                              vfat       UBUNTU 18_0
/dev/sr0         48e2169c00000000                       udf        STAR_WARS_REBELS_S2_D2

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul 26 18:04 ata-TSSTcorp_DVD+_-RW_TS-L632D -> ../../sr0
lrwxrwxrwx 1 root root  9 Jul 26 18:06 ata-WDC_WD1200BEVS-75RST0_WD-WXE507156972 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 26 18:06 ata-WDC_WD1200BEVS-75RST0_WD-WXE507156972-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 26 18:08 ata-WDC_WD1200BEVS-75RST0_WD-WXE507156972-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 26 18:08 ata-WDC_WD1200BEVS-75RST0_WD-WXE507156972-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jul 26 18:06 ata-WDC_WD1200BEVS-75RST0_WD-WXE507156972-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jul 26 18:06 ata-WDC_WD1200BEVS-75RST0_WD-WXE507156972-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Jul 26 18:06 usb-Verbatim_Store__n__Go_f301cfe08b67df-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Jul 26 18:06 usb-Verbatim_Store__n__Go_f301cfe08b67df-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Jul 26 18:06 wwn-0x50014ee20058c038 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 26 18:06 wwn-0x50014ee20058c038-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 26 18:08 wwn-0x50014ee20058c038-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 26 18:08 wwn-0x50014ee20058c038-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jul 26 18:06 wwn-0x50014ee20058c038-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Jul 26 18:06 wwn-0x50014ee20058c038-part5 -> ../../sda5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda5/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768
--------------------------------------------------------------------------------

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

set timeout=5
menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
    initrd    /casper/initrd
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd
}
--------------------------------------------------------------------------------

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1

=============================== StdErr Messages: ===============================

File descriptor 63 (pipe:[146243]) leaked on lvs invocation. Parent PID 15213: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 20190726_1806 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: /dev/sr0: unrecognised disk label
boot-repair is executed in live-session (Ubuntu 18.04.2 LTS, bionic, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd quiet splash --- maybe-ubiquity
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:
/dev/sda1:Dell Utility Partition:DellUtility:chain
/dev/sda3:Windows Vista:Windows:chain
/dev/sda5:Microsoft Windows XP Embedded:Windows1:chain

=================== blkid:
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0713" TYPE="vfat" PARTUUID="d0000000-01"
/dev/sda2: LABEL="RECOVERY" UUID="60D65746D6571C1A" TYPE="ntfs" PARTUUID="d0000000-02"
/dev/sda3: LABEL="OS" UUID="10805AD3805ABEC2" TYPE="ntfs" PARTUUID="d0000000-03"
/dev/sda5: LABEL="MEDIADIRECT" UUID="C05E-AB4C" TYPE="vfat" PARTUUID="d0000000-05"
/dev/sdb1: LABEL="UBUNTU 18_0" UUID="9822-956F" TYPE="vfat" PARTUUID="267a172b-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sr0: UUID="48e2169c00000000" LABEL="STAR_WARS_REBELS_S2_D2" TYPE="udf"


1 disks with OS, 3 OS : 0 Linux, 0 MacOS, 2 Windows, 1 unknown type OS.

Windows not detected by os-prober on sda2.

=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    notbiosboot, /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda3.
sda5    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    notbiosboot, /mnt/boot-sav/sda5.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    not-mmc, has-os,    63 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:120GB:scsi:512:512:msdos:ATA WDC WD1200BEVS-7:;
1:32.3kB:107MB:107MB:fat16::diag;
2:107MB:10.8GB:10.7GB:ntfs::boot;
3:10.8GB:117GB:107GB:ntfs::;
4:117GB:120GB:2684MB:::lba;
5:117GB:120GB:2683MB:fat32::;

BYT;
/dev/sdb:4043MB:scsi:512:512:msdos:Verbatim Store 'n' Go:;
1:1049kB:4043MB:4042MB:fat32::boot, lba;

BYT;
/dev/sr0:6949MB:scsi:2048:2048:unknown:TSSTcorp DVD+-RW TS-L632D:;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
loop0 loop squashfs   1.8G
loop1 loop squashfs    91M
loop2 loop squashfs  34.6M
loop3 loop squashfs 140.7M
loop4 loop squashfs   2.3M
loop5 loop squashfs    13M
loop6 loop squashfs  14.5M
loop7 loop squashfs   3.7M
sda   disk          111.8G
sda1  part vfat       102M DellUtility
sda2  part ntfs        10G RECOVERY
sda3  part ntfs      99.2G OS
sda4  part              1K
sda5  part vfat       2.5G MEDIADIRECT
sdb   disk            3.8G
sdb1  part vfat       3.8G UBUNTU 18_0
sr0   rom  udf        6.5G STAR_WARS_REBELS_S2_D2

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
loop1    1  1  0         /snap/core/6350
loop2    1  1  0         /snap/gtk-common-themes/818
loop3    1  1  0         /snap/gnome-3-26-1604/74
loop4    1  1  0         /snap/gnome-calculator/260
loop5    1  1  0         /snap/gnome-characters/139
loop6    1  1  0         /snap/gnome-logs/45
loop7    1  1  0         /snap/gnome-system-monitor/57
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0         /mnt/boot-sav/sda3
sda4     1  0  0
sda5     1  0  0         /mnt/boot-sav/sda5
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
sr0      1  0  1 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=997568k,nr_inodes=249392,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=204008k,mode=755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=26,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=13969)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=204004k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/var/lib/snapd/snaps/core_6350.snap on /snap/core/6350 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_818.snap on /snap/gtk-common-themes/818 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_74.snap on /snap/gnome-3-26-1604/74 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_260.snap on /snap/gnome-calculator/260 type squashfs (ro,nodev,relatime,x-gdu.hide)
tmpfs on /run/user/0 type tmpfs (rw,nosuid,nodev,relatime,size=204004k,mode=700)
/var/lib/snapd/snaps/gnome-characters_139.snap on /snap/gnome-characters/139 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_45.snap on /snap/gnome-logs/45 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_57.snap on /snap/gnome-system-monitor/57 type squashfs (ro,nodev,relatime,x-gdu.hide)
gvfsd-fuse on /run/user/0/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=0,group_id=0)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda5 on /mnt/boot-sav/sda5 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 sda2 sda3 sda4 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 gpiochip0 gpiochip1 hidraw0 hidraw1 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 initctl input kmsg lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sdb sdb1 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 54 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.T.Dell 8.0.....|
00000010  02 00 02 00 00 f8 cc 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  8e 2f 03 00 80 01 29 13  07 d7 07 44 65 6c 6c 55  |./....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 10 00  |tilityFAT16   ..|
00000040  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 33 c0  8e d0 bc 00 07 fc b9 80  |......3.........|
00000060  00 8e d8 be 00 7c b8 00  20 8e c0 33 ff f3 66 a5  |.....|.. ..3..f.|
00000070  ea 75 00 00 20 8e d8 be  cc 01 b8 01 02 b9 01 00  |.u.. ...........|
00000080  b6 00 8a 16 24 00 bb 00  02 cd 13 0f 82 0c 01 80  |....$...........|
00000090  3e c2 03 06 74 0e c6 06  c2 03 06 b8 01 03 cd 13  |>...t...........|
000000a0  0f 82 f7 00 66 0f b7 06  0e 00 66 03 06 1c 00 66  |....f.....f....f|
000000b0  0f b7 0e 16 00 66 d1 e1  66 03 c1 66 a3 46 00 66  |.....f..f..f.F.f|
000000c0  0f b7 0e 11 00 89 0e 52  00 83 c1 0f c1 e9 04 88  |.......R........|
000000d0  0e 40 00 66 03 c1 66 a3  4e 00 b8 00 30 a3 44 00  |.@.f..f.N...0.D.|
000000e0  8e c0 e8 d4 00 33 db b9  0b 00 be e1 01 8b fb f3  |.....3..........|
000000f0  a6 74 0f 83 c3 20 ff 0e  52 00 75 eb be d7 01 e9  |.t... ..R.u.....|
00000100  99 00 26 8b 47 1a a3 54  00 a1 16 00 a3 52 00 66  |..&.G..T.....R.f|
00000110  0f b7 06 0e 00 66 03 06  1c 00 66 a3 46 00 a1 52  |.....f....f.F..R|
00000120  00 3d 40 00 76 02 b0 40  a2 40 00 e8 8b 00 66 0f  |.=@.v..@.@....f.|
00000130  b6 06 40 00 66 01 06 46  00 29 06 52 00 74 09 c1  |..@.f..F.).R.t..|
00000140  e0 05 01 06 44 00 eb d6  c7 06 44 00 70 00 a0 0d  |....D.....D.p...|
00000150  00 a2 40 00 66 0f b7 06  54 00 66 83 e8 02 66 0f  |..@.f...T.f...f.|
00000160  b6 0e 0d 00 66 f7 e1 66  03 06 4e 00 66 a3 46 00  |....f..f..N.f.F.|
00000170  e8 46 00 8b 36 54 00 b8  00 30 d1 e6 73 03 05 00  |.F..6T...0..s...|
00000180  10 8e c0 26 ad 3d f8 ff  73 16 a3 54 00 0f b6 06  |...&.=..s..T....|
00000190  0d 00 c1 e0 09 01 06 42  00 eb b9 e8 0d 00 eb fe  |.......B........|
000001a0  8a 16 24 00 33 ed ea 00  00 70 00 b4 0e ac bb 07  |..$.3....p......|
000001b0  00 cd 10 80 3c 00 75 f3  c3 b4 42 8a 16 24 00 be  |....<.u...B..$..|
000001c0  3e 00 cd 13 72 01 c3 be  cc 01 eb cf 44 69 73 6b  |>...r.......Disk|
000001d0  20 65 72 72 6f 72 00 4e  6f 20 6c 6f 61 64 65 72  | error.No loader|
000001e0  00 44 45 4c 4c 42 49 4f  20 42 49 4e 00 00 00 00  |.DELLBIO BIN....|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 30 03 00  |........?....0..|
00000020  00 00 00 00 80 00 80 00  ff ff 3f 01 00 00 00 00  |..........?.....|
00000030  00 00 0c 00 00 00 00 00  ff ff 13 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  1a 1c 57 d6 46 57 d6 60  |..........W.FW.`|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 30 43 01  |........?....0C.|
00000020  00 00 00 00 80 00 80 00  f0 0f 66 0c 00 00 00 00  |..........f.....|
00000030  00 00 0c 00 00 00 00 00  ff 60 cb 00 00 00 00 00  |.........`......|
00000040  f6 00 00 00 01 00 00 00  c2 be 5a 80 d3 5a 80 10  |..........Z..Z..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 d2 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  40 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |@.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a e9 6a 01  |U...h..fa.....j.|
00000110  90 90 66 60 1e 06 66 a1  11 00 66 03 06 1c 00 1e  |..f`..f...f.....|
00000120  66 68 00 00 00 00 66 50  06 53 68 01 00 68 10 00  |fh....fP.Sh..h..|
00000130  b4 42 8a 16 0e 00 16 1f  8b f4 cd 13 66 59 5b 5a  |.B..........fY[Z|
00000140  66 59 66 59 1f 0f 82 16  00 66 ff 06 11 00 03 16  |fYfY.....f......|
00000150  0f 00 8e c2 ff 0e 16 00  75 bc 07 1f 66 61 c3 a0  |........u...fa..|
00000160  f8 01 e8 08 00 a0 fb 01  e8 02 00 eb fe b4 01 8b  |................|
00000170  f0 ac 3c 00 74 09 b4 0e  bb 07 00 cd 10 eb f2 c3  |..<.t...........|
00000180  0d 0a 41 20 64 69 73 6b  20 72 65 61 64 20 65 72  |..A disk read er|
00000190  72 6f 72 20 6f 63 63 75  72 72 65 64 00 0d 0a 42  |ror occurred...B|
000001a0  4f 4f 54 4d 47 52 20 69  73 20 6d 69 73 73 69 6e  |OOTMGR is missin|
000001b0  67 00 0d 0a 42 4f 4f 54  4d 47 52 20 69 73 20 63  |g...BOOTMGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda5
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 22 18  |.X.MSDOS5.0...".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 a9 0d  |........?....H..|
00000020  00 f8 4f 00 ef 13 00 00  00 00 00 00 02 00 00 00  |..O.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 4c ab 5e c0 44  65 6c 6c 4d 44 33 70 6c  |..)L.^.DellMD3pl|
00000050  61 79 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |ayFAT32   3.....|
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

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  975M     0  975M   0% /dev
tmpfs          tmpfs     200M  2.1M  198M   2% /run
/dev/sdb1      vfat      3.8G  1.9G  1.9G  50% /cdrom
/dev/loop0     squashfs  1.8G  1.8G     0 100% /rofs
/cow           overlay   997M  402M  595M  41% /
tmpfs          tmpfs     997M     0  997M   0% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     997M     0  997M   0% /sys/fs/cgroup
tmpfs          tmpfs     997M  4.0K  997M   1% /tmp
tmpfs          tmpfs     200M   48K  200M   1% /run/user/999
/dev/loop1     squashfs   91M   91M     0 100% /snap/core/6350
/dev/loop2     squashfs   35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop3     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop4     squashfs  2.3M  2.3M     0 100% /snap/gnome-calculator/260
tmpfs          tmpfs     200M  4.0K  200M   1% /run/user/0
/dev/loop5     squashfs   13M   13M     0 100% /snap/gnome-characters/139
/dev/loop6     squashfs   15M   15M     0 100% /snap/gnome-logs/45
/dev/loop7     squashfs  3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/sda1      vfat      102M  7.0M   95M   7% /mnt/boot-sav/sda1
/dev/sda2      fuseblk    10G   10G   46M 100% /mnt/boot-sav/sda2
/dev/sda3      fuseblk   100G   88G   12G  89% /mnt/boot-sav/sda3
/dev/sda5      vfat      2.5G  1.7G  839M  68% /mnt/boot-sav/sda5

=================== fdisk -l:
Disk /dev/loop0: 1.8 GiB, 1905045504 bytes, 3720792 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 91 MiB, 95408128 bytes, 186344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.7 MiB, 147496960 bytes, 288080 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xd0000000

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1              63    208844    208782  102M de Dell Utility
/dev/sda2  *       208896  21180415  20971520   10G  7 HPFS/NTFS/exFAT
/dev/sda3        21180416 229195775 208015360 99.2G  7 HPFS/NTFS/exFAT
/dev/sda4       229195776 234438655   5242880  2.5G  f W95 Ext'd (LBA)
/dev/sda5       229197824 234438655   5240832  2.5G dd unknown


Disk /dev/sdb: 3.8 GiB, 4043308544 bytes, 7897087 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x267a172b

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *     2048 7897086 7895039  3.8G  c W95 FAT32 (LBA)




=================== Suggested repair
The default repair of the Boot-Repair utility would restore the [(generic mbr)] MBR in sda, and make it boot on sda3.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot


=================== User settings
The settings chosen by the user will not act on the boot.





```

---

### Post by theimp2 on 2019-07-26
I'll add that the specific error I get on boot up right now is:
> 
BOOTMGR is missing
Press Ctrl+Alt+Del to restart


---

### Post by ajgreeny on 2019-07-26
It looks as if you could repair the boot of your Vista by allowing Boot-Repair to reinstate the Windows boot files by restoring the [(generic mbr)] MBR in sda, and make it boot on sda3.

However, Vista lost any support some time ago so will be a security risk particularly if connected to the internet so in many ways you would be better advised to consider installing one of the Ubuntu family (I suggest Xubuntu as it has a desktop layout similar to Vista) or another distro of your choice.

---

### Post by TheFu on 2019-07-26
Also, might work if you eject the Star Wars DVD and try to boot.

I don't see anything in there related to any Linux - except that you have a flash drive.  Unplug that.

Then use normal Windows troubleshooting to fix whatever is wrong, assuming anything actually is.  I'm not convinced that anything is actually wrong.

---

### Post by oldfred on 2019-07-26
With Windows, you have to have a primary NTFS partition with the boot flag and the Windows boot files in that partition. 
Use gparted on Ubuntu live installer & move boot flag to sda3.
I do not think you can even boot your XP, but maybe with booting on primary partition it might let you boot an install on a logical partition.

You show no Linux install, just Windows. As ajgreeny says your Windows are all obsolete and should not be used on Internet. 
Even Windows 7 will now expire next Jan 2020.

---

### Post by theimp2 on 2019-07-26
> **ajgreeny said:**
> It looks as if you could repair the boot of your Vista by allowing Boot-Repair to reinstate the Windows boot files by restoring the [(generic mbr)] MBR in sda, and make it boot on sda3.

However, Vista lost any support some time ago so will be a security risk particularly if connected to the internet so in many ways you would be better advised to consider installing one of the Ubuntu family (I suggest Xubuntu as it has a desktop layout similar to Vista) or another distro of your choice.
Thanks, this worked, as far as I can tell.

Regarding Vista.. yeah, this machine will remain air-gapped.  For now, all I want to do is perform a specific task that I can't on my other machines (they lack the necessary hardware).  For the future..  TBD.

---

