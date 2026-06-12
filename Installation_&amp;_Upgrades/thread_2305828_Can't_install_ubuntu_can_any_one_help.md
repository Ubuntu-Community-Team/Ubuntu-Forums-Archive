---
title: "Can't install ubuntu can any one help ?"
date: 2015-12-09
forum: Installation &amp; Upgrades
---

### Post by wasntme on 2015-12-09
There is link.

[http://paste.ubuntu.com/13865615/](http://paste.ubuntu.com/13865615/)
```
 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 59568 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 14.6 GiB, 15631122432 bytes, 30529536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             32    30,529,535    30,529,504   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mmcblk0                                                       
/dev/mmcblk0p1   D3CA-7B42                              vfat       
/dev/mmcblk0p2   6ecb8d1a-f0bd-4038-8efe-62d9e1a07717   ext2       
/dev/mmcblk0p3   d09e392b-5605-4287-9a1a-c08847c0ce0d   crypto_LUKS 
/dev/sda1        1814-1A49                              vfat       UUI

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root 13 Dec  9 18:22 mmc-BGND3R_0x0083b81f -> ../../mmcblk0
lrwxrwxrwx 1 root root 15 Dec  9 18:22 mmc-BGND3R_0x0083b81f-part1 -> ../../mmcblk0p1
lrwxrwxrwx 1 root root 15 Dec  9 18:22 mmc-BGND3R_0x0083b81f-part2 -> ../../mmcblk0p2
lrwxrwxrwx 1 root root 15 Dec  9 18:22 mmc-BGND3R_0x0083b81f-part3 -> ../../mmcblk0p3
lrwxrwxrwx 1 root root  9 Dec  9 18:30 usb-SanDisk_Cruzer_Force_4C530012871020110283-0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 Dec  9 18:30 usb-SanDisk_Cruzer_Force_4C530012871020110283-0:0-part1 -> ../../sda1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash ---
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true ---
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash ---
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/4868/mounts) leaked on lvs invocation. Parent PID 12361: bash
File descriptor 63 (pipe:[48077]) leaked on lvs invocation. Parent PID 12361: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-12-09__18h27 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
Error: /dev/mmcblk0rpmb: unrecognised disk label
Warning: Error fsyncing/closing /dev/mmcblk0rpmb: Input/output error
Error: /dev/mmcblk0boot0: unrecognised disk label
Error: /dev/mmcblk0boot1: unrecognised disk label
Error: /dev/mmcblk0rpmb: unrecognised disk label
Warning: Error fsyncing/closing /dev/mmcblk0rpmb: Input/output error
Error: /dev/mmcblk0boot0: unrecognised disk label
Error: /dev/mmcblk0boot1: unrecognised disk label
boot-repair is executed in live-session (Ubuntu 15.10, wily, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash ---
ls: cannot access /home/usr/.config: No such file or directory
mmcblk0 (sda) has unknown type. Please report this message to boot.repair@gmail.com
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/mmcblk0p3 : Error code 32
mount -r /dev/mmcblk0p3 /mnt/boot-sav/mmcblk0p3
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/mmcblk0p3 : Error code 32
mount: /dev/mmcblk0 is already mounted or /mnt/boot-sav/mmcblk0 busy
mount /dev/mmcblk0 : Error code 32
mount -r /dev/mmcblk0 /mnt/boot-sav/mmcblk0
mount: /dev/mmcblk0 is already mounted or /mnt/boot-sav/mmcblk0 busy
mount -r /dev/mmcblk0 : Error code 32
cat: /sys/block/mmcblk0/mmcblk0boot0/start: No such file or directory
cat: /sys/block/mmcblk0/mmcblk0boot1/start: No such file or directory
cat: /sys/block/mmcblk0/mmcblk0rpmb/start: No such file or directory

=================== os-prober:


=================== blkid:
/dev/mmcblk0p1: UUID="D3CA-7B42" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="f2e9082d-1337-4b5d-871b-0602c267a46a"
/dev/mmcblk0p2: UUID="6ecb8d1a-f0bd-4038-8efe-62d9e1a07717" TYPE="ext2" PARTUUID="94ef2c72-c3c3-424e-ac4c-4eaecc01c93e"
/dev/sda1: LABEL="UUI" UUID="1814-1A49" TYPE="vfat"
/dev/loop0: TYPE="squashfs"
/dev/mmcblk0p3: UUID="d09e392b-5605-4287-9a1a-c08847c0ce0d" TYPE="crypto_LUKS" PARTUUID="1b4b0b74-049d-4387-b0d8-8180ecc7faba"
/dev/mmcblk0: PTUUID="6d049023-5213-4fc2-97fa-eec325c3f00c" PTTYPE="gpt"

mount: unknown filesystem type 'crypto_LUKS'
mount /dev/mmcblk0p3 : Error code 32
mount -r /dev/mmcblk0p3 /mnt/boot-sav/mmcblk0p3
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/mmcblk0p3 : Error code 32
mount: /dev/mmcblk0 is already mounted or /mnt/boot-sav/mmcblk0 busy
mount /dev/mmcblk0 : Error code 32
mount -r /dev/mmcblk0 /mnt/boot-sav/mmcblk0
mount: /dev/mmcblk0 is already mounted or /mnt/boot-sav/mmcblk0 busy
mount -r /dev/mmcblk0 : Error code 32

=================== mmcblk0p2recordfail=1/grub/grubenv :
recordfail=1




=================== efibootmgr -v
BootCurrent: 0006
Timeout: 2 seconds
BootOrder: 0001,0006,0007,0000
Boot0000* Windows Boot Manager    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu    HD(1,GPT,f2e9082d-1337-4b5d-871b-0602c267a46a,0x800,0x100000)/File(EFIUBUNTUSHIMX64.EFI)
Boot0006* UEFI: SanDisk Cruzer Force 1.27, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/USB(1,0)/HD(1,MBR,0x0,0x20,0x1d1d7e0)..BO
Boot0007* ubuntu    HD(1,GPT,f2e9082d-1337-4b5d-871b-0602c267a46a,0x800,0x100000)/File(EFIUBUNTUGRUBX64.EFI)..BO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.


=================== PARTITIONS & DISKS:
mmcblk0p1    : mmcblk0,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/mmcblk0p1.
mmcblk0p2    : mmcblk0,    is-sepboot,    grubenv-ng    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/ubuntu/6ecb8d1a-f0bd-4038-8efe-62d9e1a07717.
mmcblk0p3    : mmcblk0,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/mmcblk0p3.
mmcblk0    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/mmcblk0.

mmcblk0    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    no-os,    1 sectors * 512 bytes
sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     usb-disk,    no-os,    32 sectors * 512 bytes


=================== parted -l:

Model: SanDisk Cruzer Force (scsi)
Disk /dev/sda: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  15.6GB  15.6GB  primary  fat32        boot, lba


Model: Generic SD/MMC Storage Card (sd/mmc)
Disk /dev/mmcblk0rpmb: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Model: Generic SD/MMC Storage Card (sd/mmc)
Disk /dev/mmcblk0boot0: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Model: Generic SD/MMC Storage Card (sd/mmc)
Disk /dev/mmcblk0boot1: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Model: MMC BGND3R (sd/mmc)
Disk /dev/mmcblk0: 31.3GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name                  Flags
1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
2      538MB   794MB   256MB   ext2
3      794MB   31.3GB  30.5GB

=================== parted -lm:

BYT;
/dev/sda:15.6GB:scsi:512:512:msdos:SanDisk Cruzer Force:;
1:16.4kB:15.6GB:15.6GB:fat32::boot, lba;

BYT;
/dev/mmcblk0rpmb:4194kB:sd/mmc:512:512:unknown:Generic SD/MMC Storage Card:;

BYT;
/dev/mmcblk0boot0:4194kB:sd/mmc:512:512:unknown:Generic SD/MMC Storage Card:;

BYT;
/dev/mmcblk0boot1:4194kB:sd/mmc:512:512:unknown:Generic SD/MMC Storage Card:;

BYT;
/dev/mmcblk0:31.3GB:sd/mmc:512:512:gpt:MMC BGND3R:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:794MB:256MB:ext2::;
3:794MB:31.3GB:30.5GB:::;

=================== lsblk:
KNAME        TYPE FSTYPE       SIZE LABEL MODEL            UUID
sda          disk             14.6G       Cruzer Force
sda1         part vfat        14.6G UUI                    1814-1A49
loop0        loop squashfs     1.1G
mmcblk0rpmb  disk                4M
mmcblk0boot0 disk                4M
mmcblk0boot1 disk                4M
mmcblk0      disk             29.1G
mmcblk0p1    part vfat         512M                        D3CA-7B42
mmcblk0p2    part ext2         244M                        6ecb8d1a-f0bd-4038-8efe-62d9e1a07717
mmcblk0p3    part crypto_LUKS 28.4G                        d09e392b-5605-4287-9a1a-c08847c0ce0d

KNAME        ROTA RO RM STATE   MOUNTPOINT
sda             1  0  1 running
sda1            1  0  1         /cdrom
loop0           1  1  0         /rofs
mmcblk0rpmb     0  0  0
mmcblk0boot0    0  1  0
mmcblk0boot1    0  1  0
mmcblk0         0  0  0
mmcblk0p1       0  0  0         /mnt/boot-sav/mmcblk0p1
mmcblk0p2       0  0  0         /media/ubuntu/6ecb8d1a-f0bd-4038-8efe-62d9e1a07717
mmcblk0p3       0  0  0


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=963640k,nr_inodes=240910,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=195308k,mode=755)
/dev/sda1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=23,pgrp=1,timeout=0,minproto=5,maxproto=5,direct)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=195308k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/dev/mmcblk0p2 on /media/ubuntu/6ecb8d1a-f0bd-4038-8efe-62d9e1a07717 type ext2 (rw,nosuid,nodev,relatime,uhelper=udisks2)
/dev/mmcblk0p1 on /mnt/boot-sav/mmcblk0p1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=================== ls:
/sys/block/mmcblk0 (filtered):  alignment_offset bdi capability dev device discard_alignment ext_range force_ro holders inflight mmcblk0boot0 mmcblk0boot1 mmcblk0p1 mmcblk0p2 mmcblk0p3 mmcblk0rpmb power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/mmcblk0boot0 (filtered):  alignment_offset bdi capability dev device discard_alignment ext_range force_ro holders inflight power queue range removable ro ro_lock_until_next_power_on size slaves stat subsystem trace uevent
/sys/block/mmcblk0boot1 (filtered):  alignment_offset bdi capability dev device discard_alignment ext_range force_ro holders inflight power queue range removable ro ro_lock_until_next_power_on size slaves stat subsystem trace uevent
/sys/block/mmcblk0rpmb (filtered):  alignment_offset bdi capability dev device discard_alignment ext_range force_ro holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/dev (filtered):  acpi_thermal_rel autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg kvm log mapper mcelog media0 mei0 mem memory_bandwidth mmcblk0 mmcblk0boot0 mmcblk0boot1 mmcblk0p1 mmcblk0p2 mmcblk0p3 mmcblk0rpmb mqueue ndctl0 net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sg0 shm snapshot snd stderr stdin stdout tpm0 uhid uinput urandom v4l vfio vga_arbiter vhci vhost-net video0 xconsole zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/mmcblk0p1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  10 00 04 00 00 08 00 00  |................|
00000020  00 00 10 00 fe 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 42 7b ca d3 4e  4f 20 4e 41 4d 45 20 20  |..)B{..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  942M     0  942M   0% /dev
tmpfs          tmpfs     191M  9.6M  182M   5% /run
/dev/sda1      vfat       15G  1.1G   14G   8% /cdrom
/dev/loop0     squashfs  1.1G  1.1G     0 100% /rofs
/cow           overlay   954M   80M  875M   9% /
tmpfs          tmpfs     954M   80K  954M   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     954M     0  954M   0% /sys/fs/cgroup
tmpfs          tmpfs     954M  1.1M  953M   1% /tmp
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     191M   92K  191M   1% /run/user/999
/dev/mmcblk0p2 ext2      237M  109M  116M  49% /media/ubuntu/6ecb8d1a-f0bd-4038-8efe-62d9e1a07717
/dev/mmcblk0p1 vfat      511M  3.4M  508M   1% /mnt/boot-sav/mmcblk0p1

=================== fdisk -l:
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.1 GiB, 1130688512 bytes, 2208376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk0: 29.1 GiB, 31268536320 bytes, 61071360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6D049023-5213-4FC2-97FA-EEC325C3F00C

Device           Start      End  Sectors  Size Type
/dev/mmcblk0p1    2048  1050623  1048576  512M EFI System
/dev/mmcblk0p2 1050624  1550335   499712  244M Linux filesystem
/dev/mmcblk0p3 1550336 61069311 59518976 28.4G Linux filesystem




Disk /dev/mmcblk0boot1: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk0boot0: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 14.6 GiB, 15631122432 bytes, 30529536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *       32 30529535 30529504 14.6G  c W95 FAT32 (LBA)


No OS or WinEFI system
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
/boot detected. Please check the options.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
No OS or WinEFI system

=================== Recommended repair
The default repair of the Boot-Repair utility will not act on the MBR.
Additional repair will be performed:  repair-filesystems


Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var
umount: /media/ubuntu/6ecb8d1a-f0bd-4038-8efe-62d9e1a07717: mountpoint not found

fsck -fyM /dev/mmcblk0p1
fsck from util-linux 2.26.2
fsck.fat 3.0.28 (2015-05-16)
/dev/mmcblk0p1: 6 files, 864/130812 clusters

fsck -fyM /dev/mmcblk0p2
fsck from util-linux 2.26.2
e2fsck 1.42.12 (29-Aug-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/mmcblk0p2: 298/62496 files (22.1% non-contiguous), 118706/249856 blocks

fsck -fyM /dev/mmcblk0p3
fsck from util-linux 2.26.2

fsck -fyM /dev/mmcblk0
fsck from util-linux 2.26.2
e2fsck 1.42.12 (29-Aug-2014)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/mmcblk0

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
or
e2fsck -b 32768 <device>

mount: unknown filesystem type 'crypto_LUKS'
mount /dev/mmcblk0p3 : Error code 32
mount -r /dev/mmcblk0p3 /mnt/boot-sav/mmcblk0p3
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/mmcblk0p3 : Error code 32
mount: /dev/mmcblk0 is already mounted or /mnt/boot-sav/mmcblk0 busy
mount /dev/mmcblk0 : Error code 32
mount -r /dev/mmcblk0 /mnt/boot-sav/mmcblk0
mount: /dev/mmcblk0 is already mounted or /mnt/boot-sav/mmcblk0 busy
mount -r /dev/mmcblk0 : Error code 32

Boot successfully repaired.

You can now reboot your computer.
```

---

### Post by oldfred on 2015-12-09
I do not know LVM nor encrypted installs.
And it looks like you installed to a memory card.
Some computers will not boot from memory cards, can you normally use a memory card to boot?
Does your UEFI show memory card as bootable device?

Part of issue may be that flash drive as sda.
Grub normally installs to drive seen as sda as most systems have sda as first drive.

Is this one of those mini systems or tablets? And is it 64 bit?

---

### Post by wasntme on 2015-12-10
when i install Ubuntu and click Restart when it ask Ubuntu can't start.
I don't know why USB is sda. I can't change it or i can't find how to change.
Laptop system is in 64 bit.

---

### Post by wasntme on 2015-12-10
when i install Ubuntu and click Restart when it ask Ubuntu can't start.
I don't know why USB is sda. I can't change it or i can't find how to change.
Laptop system is in 64 bit.

---

### Post by oldfred on 2015-12-10
The real issue is does your computer boot from memory cards?

Many newer ones do, but you have to go into UEFI/BIOS and select that. And if older computer you may be able to use memory cards for data, but not boot from them.

---

### Post by sudodus on 2015-12-10
> **oldfred said:**
> The real issue is does your computer boot from memory cards?

Many newer ones do, but you have to go into UEFI/BIOS and select that. And if older computer you may be able to use memory cards for data, but not boot from them.

+1 (I agree)

It depends on the card reader too. Some card readers make the card 'look like' any USB drive, and booting works. Other card readers work to read and write data in a running operating system, but they are not recognized for booting.

---

### Post by wasntme on 2015-12-10
Memory card you mean USB ?

When i install Ubuntu it installs into /dev/mmcblk0. In GParted i see mmcblk0 (it's my hdd i think) and i see second one /dev/sda (it's my usb) when i remove my usb it's disappear.
[IMG]http://i.stack.imgur.com/kepiA.jpg[/IMG]
Image is not mine. in my Boot Option #1 is my USB. Don't understand how to change it. Do I need to change it ? There is no UEFI settings or something.

Sorry for my bad English.

---

### Post by wasntme on 2015-12-10
Guys just tried to install Ubuntu without LVM and any encrypt and it's woorks perfect. Can't use encrypt without LVM. For good security enough to encrypt my home folder?

---

### Post by sudodus on 2015-12-10
I think **/dev/mmcblk0** is the card reader. Does the computer boot from it? Is this correct?

```
=================== parted -l:

Model: **SanDisk Cruzer Force (scsi)**
Disk **/dev/sda: 15.6GB**
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  15.6GB  15.6GB  primary  fat32        boot, lba

[COLOR="#cc0000"]***Is the red text describing the same 4 GB card, or are there three of them?***

Model: **Generic SD/MMC Storage Card (sd/mmc)**
Disk **/dev/mmcblk0rpmb: 4194kB**
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Model: Generic SD/MMC Storage Card (sd/mmc)
Disk /dev/mmcblk0boot0: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Model: Generic SD/MMC Storage Card (sd/mmc)
Disk /dev/mmcblk0boot1: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:
[/COLOR]
Model: **MMC BGND3R (sd/mmc)**
Disk **/dev/mmcblk0: 31.3GB**
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name                  Flags
1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
2      538MB   794MB   256MB   ext2
3      794MB   31.3GB  30.5GB
```

---

### Post by sudodus on 2015-12-10
> **wasntme said:**
> Guys just tried to install Ubuntu without LVM and any encrypt and it's woorks perfect. Can't use encrypt without LVM. For good security enough to encrypt my home folder?

Yes, it is probably good enough with encrypted home, if you have also a working encrypted swap. And I think you need version 15.10 for that purpose. I'm afraid there are problems with encrypted swap in 14.04 LTS.

---

### Post by wasntme on 2015-12-10
> **sudodus said:**
> I think **/dev/mmcblk0** is the card reader. Does the computer boot from it? Is this correct?

```
=================== parted -l:

Model: **SanDisk Cruzer Force (scsi)**
Disk **/dev/sda: 15.6GB**
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  15.6GB  15.6GB  primary  fat32        boot, lba

[COLOR=#cc0000]***Is the red text describing the same 4 GB card, or are there three of them?***

Model: **Generic SD/MMC Storage Card (sd/mmc)**
Disk **/dev/mmcblk0rpmb: 4194kB**
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Model: Generic SD/MMC Storage Card (sd/mmc)
Disk /dev/mmcblk0boot0: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

Model: Generic SD/MMC Storage Card (sd/mmc)
Disk /dev/mmcblk0boot1: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:
[/COLOR]
Model: **MMC BGND3R (sd/mmc)**
Disk **/dev/mmcblk0: 31.3GB**
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name                  Flags
1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
2      538MB   794MB   256MB   ext2
3      794MB   31.3GB  30.5GB
```


Really i don't know. Now computer boots normally when i installed without LVM.

---

### Post by wasntme on 2015-12-10
> **sudodus said:**
> Yes, it is probably good enough with encrypted home, if you have also a working encrypted swap. And I think you need version 15.10 for that purpose. I'm afraid there are problems with encrypted swap in 14.04 LTS.

Yes i'm using 15.10. Can you please give me more info about encryption for swap? i can do it in GParted or no?

---

### Post by wasntme on 2015-12-10
Now i installed Ubuntu only with Encrypt my home folder and again it won't start. I don't understand, what did i do wrong?

---

### Post by sudodus on 2015-12-10
Maybe the software to install encryption wants a regular mass storage device **/dev/sdx**, where x is the drive letter, a or b or c ..., and here you install into  **/dev/mmcblk0**.

I don't know but I have no other explanation. I think it would work better if you install into another USB pendrive, that would be either /dev/sda or /dev/sdb, (or if you install from the card reader /dev/mmcblk0 to the pendrive /dev/sda, if you can make /dev/mmcblk0 into a live drive with the iso file).

---

