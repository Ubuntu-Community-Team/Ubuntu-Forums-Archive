---
title: "Dual Boot install Win10 / Ubuntu on Alienware 15 R2"
date: 2016-02-09
forum: Installation &amp; Upgrades
---

### Post by Pryzm on 2016-02-09
Hello,

I'm a french (sorry for my english ^^) and owner of a new Alienware 15 R2 (Win10 pre-installed). I use Ubuntu for many years now, but this time I have some trouble during install.

Indeed, my new laptop is composed by 1 SSD (256 Go, where Windows is installed and UEFI recovery too) and 1 HD (1To). I want to install Ubuntu (last version LTS : 14.04.3) in dual-boot but I have some troubles :
- When I create LiveUSB and boot on it (UEFI mode), Ubuntu didn't recognize Windows installation. So I cancelled because I didn't want to erase Windows partition. Here is my partition table :
[[IMG]http://img15.hostingpics.net/thumbs/mini_887839harddrive.png[/IMG]]("http://www.hostingpics.net/viewer.php?id=887839harddrive.png")
- I've read on some doc that it need to disabled some boot option (FastBoot, SecureBoot) to install it, but after disabled SecureBoot, no change appear, except the fact that Windows didn't want to boot. Here is my full Boot menu with options :
[[IMG]http://img15.hostingpics.net/thumbs/mini_216451IMG20160206144746.jpg[/IMG]]("http://www.hostingpics.net/viewer.php?id=216451IMG20160206144746.jpg")[[IMG]http://img15.hostingpics.net/thumbs/mini_119550IMG20160206144755.jpg[/IMG]]("http://www.hostingpics.net/viewer.php?id=119550IMG20160206144755.jpg")[[IMG]http://img15.hostingpics.net/thumbs/mini_948088IMG20160206144803.jpg[/IMG]]("http://www.hostingpics.net/viewer.php?id=948088IMG20160206144803.jpg")[[IMG]http://img15.hostingpics.net/thumbs/mini_749031IMG20160206144816.jpg[/IMG]]("http://www.hostingpics.net/viewer.php?id=749031IMG20160206144816.jpg")
- I'v ask some help on Ubuntu french forums, and ask me my boot-info. Here it is :
```

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 59002 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       264,191       262,144 Microsoft Reserved Partition (Windows)
/dev/sda2         264,192 1,892,083,711 1,891,819,520 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.5 GB, 15482298368 bytes
64 heads, 32 sectors/track, 14765 cylinders, total 30238864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    30,238,719    30,238,688   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       5dae763a-2a5a-de46-a700-5479bd62c804   ext2       casper-rw
/dev/loop1                                              squashfs   
/dev/sda2        7630F46230F42AAF                       ntfs       DATA
/dev/sdb1        0CFF-342E                              vfat       UUI

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Feb  7 06:25 ata-HGST_HTS721010A9E630_JR10004M0RX2HF -> ../../sda
lrwxrwxrwx 1 root root 10 Feb  7 06:24 ata-HGST_HTS721010A9E630_JR10004M0RX2HF-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  7 06:27 ata-HGST_HTS721010A9E630_JR10004M0RX2HF-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Feb  7 06:25 usb-UDISK_PDU09_16G_A6I2.0_785745438aa018-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb  7 06:24 usb-UDISK_PDU09_16G_A6I2.0_785745438aa018-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Feb  7 06:25 wwn-0x5000cca8a8ca6993 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb  7 06:24 wwn-0x5000cca8a8ca6993-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  7 06:27 wwn-0x5000cca8a8ca6993-part2 -> ../../sda2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/4072/mounts) leaked on lvs invocation. Parent PID 9088: bash
File descriptor 63 (pipe:[28412]) leaked on lvs invocation. Parent PID 9088: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-info 2016-02-07__06h25 ===================
boot-info version : 4ppa35
boot-sav version : 4ppa35
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa35
boot-info is executed in live-session (Ubuntu 14.04.3 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
ls: cannot access /home/usr/.config: No such file or directory

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:


=================== blkid:
/dev/loop0: LABEL="casper-rw" UUID="5dae763a-2a5a-de46-a700-5479bd62c804" TYPE="ext2"
/dev/loop1: TYPE="squashfs"
/dev/sda2: LABEL="DATA" UUID="7630F46230F42AAF" TYPE="ntfs"
/dev/sdb1: LABEL="UUI" UUID="0CFF-342E" TYPE="vfat"


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== efibootmgr -v
BootCurrent: 1005
Timeout: 0 seconds
BootOrder: 0000,0003,0004,1005
Boot0000* Windows Boot Manager    HD(1,800,fa000,39e3883c-0eda-4308-988c-3e5ceda6f3e6)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0003* Onboard NIC (IPV4)    ACPI(a0341d0,0)PCI(1c,4)PCI(0,0)MAC(f8cab8531c89,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0004* Onboard NIC (IPV6)    ACPI(a0341d0,0)PCI(1c,4)PCI(0,0)MAC(f8cab8531c89,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.


=================== PARTITIONS & DISKS:
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.

sda    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
1      1049kB  135MB  134MB               Microsoft reserved partition  msftres
2      135MB   969GB  969GB  ntfs         Basic data partition          msftdata


Model: UDISK PDU09_16G A6I2.0 (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  15.5GB  15.5GB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:gpt:ATA HGST HTS721010A9;
1:1049kB:135MB:134MB::Microsoft reserved partition:msftres;
2:135MB:969GB:969GB:ntfs:Basic data partition:msftdata;

BYT;
/dev/sdb:15.5GB:scsi:512:512:msdos:UDISK PDU09_16G A6I2.0;
1:16.4kB:15.5GB:15.5GB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sda   disk          931.5G
sda1  part            128M
sda2  part ntfs     902.1G DATA
sdb   disk           14.4G
sdb1  part vfat      14.4G UUI
loop0 loop ext2         2G casper-rw
loop1 loop squashfs 962.1M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0
sda2     1  0  0         /mnt/boot-sav/sda2
sdb      1  0  1 running
sdb1     1  0  1         /cdrom
loop0    1  0  0
loop1    1  0  0         /rofs


=================== mount:
/cow on / type overlay (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop1 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hpet i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 input kmsg kvm log mapper mcelog media0 mem memory_bandwidth net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 04 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff df c2 70 00 00 00 00  |...........p....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  af 2a f4 30 62 f4 30 76  |.........*.0b.0v|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/cow           overlay   2.0G  338M  1.6G  18% /
udev           devtmpfs  5.9G   12K  5.9G   1% /dev
tmpfs          tmpfs     1.2G  1.6M  1.2G   1% /run
/dev/sdb1      vfat       15G  3.0G   12G  21% /cdrom
/dev/loop1     squashfs  963M  963M     0 100% /rofs
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     5.9G   32K  5.9G   1% /tmp
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     5.9G   76K  5.9G   1% /run/shm
none           tmpfs     100M   32K  100M   1% /run/user
/dev/sda2      fuseblk   903G   86G  818G  10% /mnt/boot-sav/sda2

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa2f4f0e7

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 15.5 GB, 15482298368 bytes
64 heads, 32 sectors/track, 14765 cylinders, total 30238864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002492b

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    30238719    15119344    c  W95 FAT32 (LBA)


No OS or WinEFI system
gui-tab-other.sh: line 94: _checkbutton_repairfilesystems: command not found


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.





```
It appear that the SSD disk is not recognize by the boot-info. Someone on the forum told me Ubuntu didn't recognize my SDD and there is no trick anymore... :-/
- Moreover, when I boot on liveUSB, I have trouble with wifi/ethernet wich is not recognize. I follow [this tuto]("http://blog.hyperexpert.com/how-to-get-killer-wireless-ac-1525-working-with-ubuntu/") to enable it, but it remains non working... :-(. Here is the lshw command :
```

ubuntu@ubuntu:~$ sudo lshw -class network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:3b:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:dd300000-dd33ffff ioport:d000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:3c:00.0
       version: 3a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:dd200000-dd201fff



```


So I don't want to give up this installation even if it seems tricky, but I'm a bit lost in all of this. Can someone could help me with my installation, to have dual-boot Win10 / Ubuntu please ?

Don't hesitate to ask me some more info if you need,

Thanks in advance,

Pryzm.

---

### Post by oldfred on 2016-02-09
Is SSD the new NMVe device? Or M.2?
 gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

Script shows Secure boot on in UEFI, better to have it off.
And you need to turn off Windows fast start up or always on hibernation.
Only use Windows own partition tools to shrink the NTFS partition, and reboot immediately so it can run chkdsk.

Grub will not dual boot Windows if secure boot is on. And only dual boots if installed in same boot mode or UEFI in your case.
Linux also only mounts NTFS that is not hibernated nor needs chkdsk.


 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

More info & links in the link below in my signature.

---

### Post by Pryzm on 2016-02-09
Thank you for your response.

Yes, the SSD is NVMe. Here are the full references :
SSD : NVMe PM951 NVMe SAMSU
HD : HGST HTS721010A9E630

You said "gparted should be at least version 0.24.0-1 to recognize NVMe devices". Does that means I need to boot on LiveUSB, upgrade Gparted on it with the latest version, reboot and choose "Install Ubuntu" and it will recognize Windows installed on SSD and permit to install "next to it" ?

---

I disabled "FastBoot" from Windows Regedit and "SecureBoot" from Setup menu. I run the liveUSB to boot-info. It seems that it didn't reconize the SSD neither. Does this command use Gparted and need to upgrade it too ? Here is the new boot-info :
```

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 59002 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       264,191       262,144 Microsoft Reserved Partition (Windows)
/dev/sda2         264,192 1,892,083,711 1,891,819,520 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 15.5 GB, 15482298368 bytes
64 heads, 32 sectors/track, 14765 cylinders, total 30238864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    30,238,719    30,238,688   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       5dae763a-2a5a-de46-a700-5479bd62c804   ext2       casper-rw
/dev/loop1                                              squashfs   
/dev/nvme0n1p1   0A7C-6C5A                              vfat       ESP
/dev/nvme0n1p3   5480E64780E62EE4                       ntfs       OS
/dev/nvme0n1p4   C05A6FBF5A6FB138                       ntfs       WINRETOOLS
/dev/nvme0n1p5   FA5C70645C701D97                       ntfs       Image
/dev/sda2        7630F46230F42AAF                       ntfs       DATA
/dev/sdb1        0CFF-342E                              vfat       UUI

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Feb  9 17:35 ata-HGST_HTS721010A9E630_JR10004M0RX2HF -> ../../sda
lrwxrwxrwx 1 root root 10 Feb  9 17:33 ata-HGST_HTS721010A9E630_JR10004M0RX2HF-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  9 17:35 ata-HGST_HTS721010A9E630_JR10004M0RX2HF-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Feb  9 17:35 usb-UDISK_PDU09_16G_A6I2.0_785745438aa018-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb  9 17:33 usb-UDISK_PDU09_16G_A6I2.0_785745438aa018-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Feb  9 17:35 wwn-0x5000cca8a8ca6993 -> ../../sda
lrwxrwxrwx 1 root root 10 Feb  9 17:33 wwn-0x5000cca8a8ca6993-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  9 17:35 wwn-0x5000cca8a8ca6993-part2 -> ../../sda2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/4612/mounts) leaked on lvs invocation. Parent PID 11431: bash
File descriptor 63 (pipe:[37355]) leaked on lvs invocation. Parent PID 11431: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-info 2016-02-09__17h35 ===================
boot-info version : 4ppa35
boot-sav version : 4ppa35
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa35
boot-info is executed in live-session (Ubuntu 14.04.3 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
ls: cannot access /home/usr/.config: No such file or directory

WARNING: GPT (GUID Partition Table) detected on '/dev/nvme0n1'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/nvme0n1p1@/efi/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi

=================== blkid:
/dev/loop0: LABEL="casper-rw" UUID="5dae763a-2a5a-de46-a700-5479bd62c804" TYPE="ext2"
/dev/loop1: TYPE="squashfs"
/dev/nvme0n1p1: LABEL="ESP" UUID="0A7C-6C5A" TYPE="vfat"
/dev/nvme0n1p3: LABEL="OS" UUID="5480E64780E62EE4" TYPE="ntfs"
/dev/nvme0n1p4: LABEL="WINRETOOLS" UUID="C05A6FBF5A6FB138" TYPE="ntfs"
/dev/nvme0n1p5: LABEL="Image" UUID="FA5C70645C701D97" TYPE="ntfs"
/dev/sda2: LABEL="DATA" UUID="7630F46230F42AAF" TYPE="ntfs"
/dev/sdb1: LABEL="UUI" UUID="0CFF-342E" TYPE="vfat"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on nvme0n1p3.

WARNING: GPT (GUID Partition Table) detected on '/dev/nvme0n1'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/nvme0n1'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/nvme0n1p1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/nvme0n1p1/EFI/Boot/bootx64.efi

=================== efibootmgr -v
BootCurrent: 1009
Timeout: 0 seconds
BootOrder: 0000,0003,0004,1009,0005,0006,0007,0008
Boot0000* Windows Boot Manager    HD(1,800,fa000,39e3883c-0eda-4308-988c-3e5ceda6f3e6)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0003* Onboard NIC (IPV4)    ACPI(a0341d0,0)PCI(1c,4)PCI(0,0)MAC(f8cab8531c89,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0004* Onboard NIC (IPV6)    ACPI(a0341d0,0)PCI(1c,4)PCI(0,0)MAC(f8cab8531c89,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0005* NetWork    BIOS(4,0,00)..GO..NO........o.N.e.t.W.o.r.k.........................rN.D+..,.;..........@..Gd-.;.A..MQ..L.Q.u.a.l.c.o.m.m. .A.t.h.e.r.o.s. .B.o.o.t........BO
Boot0006* Second HDD    BIOS(5,0,00)..GO..NO..........S.e.c.o.n.d. .H.D.D....................A...........................%8L..C.....F..Gd-.;.A..MQ..L.P.M.9.5.1. .N.V.M.e. .S.A.M.S.U.N.G. .2.5.6.G.B........BO
Boot0007* Hard Drive    BIOS(1,0,00)..GO..NO..........H.a.r.d. .D.r.i.v.e....................A..................1.N........>.;......F..Gd-.;.A..MQ..L.P.1.:. .H.G.S.T. .H.T.S.7.2.1.0.1.0.A.9.E.6.3.0........BO
Boot0008* USB Storage Device    BIOS(2,0,00)..GO..NO........_.U.S.B. .S.t.o.r.a.g.e. .D.e.v.i.c.e....................A.......................2..Gd-.;.A..MQ..L.7.8.5.7.4.5.4.3.8.a.a.0.1.8........BO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
nvme0n1p1    : nvme0n1,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/nvme0n1p1.
nvme0n1p3    : nvme0n1,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/nvme0n1p3.
nvme0n1p4    : nvme0n1,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/nvme0n1p4.
nvme0n1p5    : nvme0n1,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/nvme0n1p5.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.

nvme0n1    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes
sda    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
1      1049kB  135MB  134MB               Microsoft reserved partition  msftres
2      135MB   969GB  969GB  ntfs         Basic data partition          msftdata


Model: UDISK PDU09_16G A6I2.0 (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  15.5GB  15.5GB  primary  fat32        boot, lba


Model: Unknown (unknown)
Disk /dev/nvme0n1: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                          Flags
1      1049kB  525MB  524MB   fat32        EFI system partition          boot
2      525MB   660MB  134MB                Microsoft reserved partition  msftres
3      660MB   242GB  242GB   ntfs         Basic data partition          msftdata
4      242GB   243GB  472MB   ntfs                                       hidden, diag
5      243GB   256GB  13.2GB  ntfs                                       hidden, diag

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:gpt:ATA HGST HTS721010A9;
1:1049kB:135MB:134MB::Microsoft reserved partition:msftres;
2:135MB:969GB:969GB:ntfs:Basic data partition:msftdata;

BYT;
/dev/sdb:15.5GB:scsi:512:512:msdos:UDISK PDU09_16G A6I2.0;
1:16.4kB:15.5GB:15.5GB:fat32::boot, lba;

BYT;
/dev/nvme0n1:256GB:unknown:512:512:gpt:Unknown;
1:1049kB:525MB:524MB:fat32:EFI system partition:boot;
2:525MB:660MB:134MB::Microsoft reserved partition:msftres;
3:660MB:242GB:242GB:ntfs:Basic data partition:msftdata;
4:242GB:243GB:472MB:ntfs::hidden, diag;
5:243GB:256GB:13.2GB:ntfs::hidden, diag;

=================== lsblk:
KNAME     TYPE FSTYPE     SIZE LABEL
sda       disk          931.5G
sda1      part            128M
sda2      part ntfs     902.1G DATA
sdb       disk           14.4G
sdb1      part vfat      14.4G UUI
loop0     loop ext2         2G casper-rw
loop1     loop squashfs 962.1M
nvme0n1   disk          238.5G
nvme0n1p1 part vfat       500M ESP
nvme0n1p2 part            128M
nvme0n1p3 part ntfs     225.1G OS
nvme0n1p4 part ntfs       450M WINRETOOLS
nvme0n1p5 part ntfs      12.3G Image

KNAME     ROTA RO RM STATE   MOUNTPOINT
sda          1  0  0 running
sda1         1  0  0
sda2         1  0  0         /mnt/boot-sav/sda2
sdb          1  0  1 running
sdb1         1  0  1         /cdrom
loop0        1  0  0
loop1        1  0  0         /rofs
nvme0n1      0  0  0
nvme0n1p1    0  0  0         /mnt/boot-sav/nvme0n1p1
nvme0n1p2    0  0  0
nvme0n1p3    0  0  0         /mnt/boot-sav/nvme0n1p3
nvme0n1p4    0  0  0         /mnt/boot-sav/nvme0n1p4
nvme0n1p5    0  0  0         /mnt/boot-sav/nvme0n1p5


=================== mount:
/cow on / type overlay (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (rw,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop1 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/nvme0n1p1 on /mnt/boot-sav/nvme0n1p1 type vfat (rw)
/dev/nvme0n1p3 on /mnt/boot-sav/nvme0n1p3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/nvme0n1p4 on /mnt/boot-sav/nvme0n1p4 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/nvme0n1p5 on /mnt/boot-sav/nvme0n1p5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/nvme0n1 (filtered):  alignment_offset bdi capability dev device discard_alignment ext_range holders inflight mq nvme0n1p1 nvme0n1p2 nvme0n1p3 nvme0n1p4 nvme0n1p5 power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hpet i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 input kmsg kvm log mapper mcelog media0 mem memory_bandwidth net network_latency network_throughput null nvme0 nvme0n1 nvme0n1p1 nvme0n1p2 nvme0n1p3 nvme0n1p4 nvme0n1p5 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdb1 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom usb v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/nvme0n1p1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 3e 18  |.X.MSDOS5.0...>.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 a0 0f 00 e1 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 5a 6c 7c 0a 4e  4f 20 4e 41 4d 45 20 20  |..)Zl|.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/nvme0n1p3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 13 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff f7 22 1c 00 00 00 00  |..........".....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  e4 2e e6 80 47 e6 80 54  |............G..T|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/nvme0n1p4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a0 36 1c  |........?.....6.|
00000020  00 00 00 00 80 00 80 00  ff 0f 0e 00 00 00 00 00  |................|
00000030  00 96 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  38 b1 6f 5a bf 6f 5a c0  |........8.oZ.oZ.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/nvme0n1p5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 b0 44 1c  |........?.....D.|
00000020  00 00 00 00 80 00 80 00  ff 7f 8a 01 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  97 1d 70 5c 64 70 5c fa  |..........pdp.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 04 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff df c2 70 00 00 00 00  |...........p....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  af 2a f4 30 62 f4 30 76  |.........*.0b.0v|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/nvme0n1'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/cow           overlay   2.0G  349M  1.6G  19% /
udev           devtmpfs  5.9G   12K  5.9G   1% /dev
tmpfs          tmpfs     1.2G  1.6M  1.2G   1% /run
/dev/sdb1      vfat       15G  3.0G   12G  21% /cdrom
/dev/loop1     squashfs  963M  963M     0 100% /rofs
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     5.9G   32K  5.9G   1% /tmp
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     5.9G   76K  5.9G   1% /run/shm
none           tmpfs     100M   32K  100M   1% /run/user
/dev/nvme0n1p1 vfat      496M   24M  473M   5% /mnt/boot-sav/nvme0n1p1
/dev/nvme0n1p3 fuseblk   226G   53G  173G  24% /mnt/boot-sav/nvme0n1p3
/dev/nvme0n1p4 fuseblk   450M  330M  121M  74% /mnt/boot-sav/nvme0n1p4
/dev/nvme0n1p5 fuseblk    13G   12G  680M  95% /mnt/boot-sav/nvme0n1p5
/dev/sda2      fuseblk   903G   86G  817G  10% /mnt/boot-sav/sda2

=================== fdisk -l:

Disk /dev/nvme0n1: 256.1 GB, 256060514304 bytes
256 heads, 63 sectors/track, 31009 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x242a7656

Device Boot      Start         End      Blocks   Id  System
/dev/nvme0n1p1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa2f4f0e7

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 15.5 GB, 15482298368 bytes
64 heads, 32 sectors/track, 14765 cylinders, total 30238864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002492b

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    30238719    15119344    c  W95 FAT32 (LBA)


No OS or WinEFI system
gui-tab-other.sh: line 94: _checkbutton_repairfilesystems: command not found


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems  fix-windows-boot


=================== User settings
The settings chosen by the user will not act on the boot.





```

When I disable SecureBoot, Windows don't want to boot anymore, it shows this error : INACCESSIBLE_BOOT_DEVICE. Does this mean that Grub will boot Windows even if SecureBoot is disabled and Windows refuse to boot ?

---

Thanks for your links, but I'm sorry I don't understand all of it, which link do I need to follow to install it ?

I'm sorry, I don't understand much about partition, hardware, UEFI and Ubuntu tricks ^^'
Thanks for reply,

Pryzm.

---

### Post by oldfred on 2016-02-09
You may just need 16.04. Normally not recommended until released in April, but I have it installed and it works for UEFI with standard drive. But since still in development, you should not rely on it. It may temporarily break as sometimes updates cause issues or get out of sync. You become a developer/tester if you install 16.04.

But with 15.10 you have a limited life and may have to update kernels & drives to what is now in 16.04 anyway. And 14.04 will have a newer version in a week or so which should be similar to 15.10.

I also download the latest copy of gparted ISO from gparted and use that. I typically do not have to, but sometime just like to have another ISO to boot. But I use grub2's loopmount to directly boot several ISO from one flash drive, so I do not have to have lots of flash drives (but somehow I do).

---

### Post by Pryzm on 2016-02-09
Thanks for your reply.

I began to read this tutorial you gave me : [http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html) (new version for Ubuntu 15.10) and it seems to be working ! Indeed, the wifi is active and the SSD seems to be recognize by the boot-info. Here it is : [http://paste.ubuntu.com/15003572/](http://paste.ubuntu.com/15003572/)

What do you think about 15.10 ? Is it really difficult to upgrade to 16.04 when it will be released (incompatibilities, ...) ?
Actually, I need Ubuntu for my work and it difficult for me to wait 2 months. But If in 2 months it will be a nightmare to change to 16.04, I prefer to wait...

---

### Post by oldfred on 2016-02-09
I upgraded from 6.06 thru 9.04 and back then there were lots of nVidia driver issues. Not that there still are not some.
Many have upgrade work. But the key is to remove all proprietary drivers and ppas before the upgrade. And do though houseclean before update. And have system fully updated an working well before upgrade.

I now prefer clean installs, but rotate / (root) partitions on SSD. And have another install or two on HDD. But I do not have Windows on SSD taking lots of space. I like to have a working install on every drive and even a full install on a larger flash drive.

---

### Post by Pryzm on 2016-02-09
I'll try to install 15.10 and prey to migrate easily in 16.10 :-)
In worst case, I think I could do clean install of 16.10 by deleting 15.10 (but always keeping Win10).

I'll follow the tuto you gave. Thanks for all your responses ! I'll be back if I have troubles with it ^^

---

### Post by Pryzm on 2016-02-11
Hello,

I followed the tutorial you gave me : [http://www.everydaylinuxuser.com/201...alongside.html]("http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html") (new version for Ubuntu 15.10) and the installation did fine alongside of Windows10 (and SecureBoot disabled).

So Ubuntu was installed next to Windows on the SSD drive. I shrink Windos partition to 40Gb, and the LiveUSB installer create one partition of 30Go to Ubuntu, and one partition of 10Go, probably for the swap).


After reboot, I  ran efibootmgr on liveUSB to reorder the boot menu, but I was surprised  because Ubuntu was before Windows (and moreover, the actual boot 1009  doesn't exist in the table ?). Here it is :
BootCurrent: 1009
Timeout: 0 seconds
BootOrder: 0001,0000,0003,0004,1009,0005,0006,0007,0008
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0003* Onboard NIC (IPV4)
Boot0004* Onboard NIC (IPV6)
Boot0005* NetWork
Boot0006* Second HDD
Boot0007* Hard Drive
Boot0008* USB Storage Device


So  I reboot, but the PC boot directly on Windows, without any grub screen.  I tried to force boot on ubuntu from the Boot Menu, but I get the error  "Selected boot device failed. Press any key to reboot the system."

Here is my boot-info : [http://paste.ubuntu.com/15019122/](http://paste.ubuntu.com/15019122/)

Can you help me to get a proper dual boot please ?

Thanks in advance,

Pryzm.

---

### Post by oldfred on 2016-02-11
You do need to turn off fast start in Windows, it leaves all NTFS partitions mounted from Linux point of view:

>  Failed to mount '/dev/sda2': Opération non permise
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume



If having issues and Ubuntu is first in UEFI boot order, it may be like a lot of other systems. They modify UEFI to include description as part of boot. And UEFI specification says specifically not to do that. And of course the only valid description is "Windows". But there are several work arounds. Most dual booting copy shimx64.efi to be bootx64.efi which is the hard drive boot entry. It looks like the hard drive entry you have is not the fallback entry, so you may need to add it to UEFI also.

 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

        sudo efibootmgr -v

Not  sure of details of your mount for NMVe device?
This is standard, but you need NMVE version.

 sudo mount -t vfat /dev/sda2 /mnt
sudo cp /mnt/EFI/ubuntu/shimx64.efi /mnt/EFI/Boot/bootx64.efi

Maybe?
sudo mount -t vfat  /dev/nvme0n1p1 /mnt

You want to end up with 
/EFI/Boot/bootx64.efi that really is shimx64.efi in the ESP.

Then create a hard drive boot entry in UEFI.
This assumes drive is sda, not sure how it works again with NVMe?

 sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"

If entry not in efibootmgr -v we may have to use the more specific entry with drive & partition.

---

### Post by Pryzm on 2016-02-12
It's really weird because I had already disabled fastBoot in WIndows (by disabling Hibernate, and disabling FastBoot in the registry...). I checked that in Windows, then I reboot and boot in liveUSB. I ran another boot-info, and it was different, I don't understand. Here it is :
[http://paste.ubuntu.com/15022911/](http://paste.ubuntu.com/15022911/)

I noticed many things :

In  "=================== PARTITIONS & DISKS:", there is  :
```
nvme0n1p6    : nvme0n1,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi 
```
This is the partition of ssd where Ubuntu is installed. But in the global details of the SSD :
```
nvme0n1    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32, 
```; It says there is "no-grubenv", is it logical ?


The suggest repair part :
It says to default boot repair, but I've already done that and it change nothing. The "final advice" is to modify directly the entry in the boot Windows, does it sounds good and easy ?

You gave me command to create efi file, but according to the boot-info, this files already exist :
```
Presence of EFI/Microsoft file detected: /mnt/boot-sav/nvme0n1p1/EFI/Microsoft/Boot/bootmgfw.efi Presence of EFI/Boot file detected: /mnt/boot-sav/nvme0n1p1/EFI/Boot/bootx64.efi
```

Thanks to help me, I'm really lost in all of it and I need to know what to do exactly.

Pryzm.


_**EDIT :**_

I tried what you said to do. The efibootmgr add the UEFI Hard Drive, and it appear in efibootmgr -v :
```

ubuntu@ubuntu:/mnt/EFI/Boot$ sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"
BootCurrent: 1009
Timeout: 0 seconds
BootOrder: 0002,0001,0000,0003,0004,1009,0005,0006,0007,0008
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0003* Onboard NIC (IPV4)
Boot0004* Onboard NIC (IPV6)
Boot0005* NetWork
Boot0006* Second HDD
Boot0007* Hard Drive
Boot0008* USB Storage Device
Boot0002* UEFI Hard drive

ubuntu@ubuntu:/mnt/EFI/Boot$ sudo efibootmgr -v
BootCurrent: 1009
Timeout: 0 seconds
BootOrder: 0002,0001,0000,0003,0004,1009,0005,0006,0007,0008
Boot0000* Windows Boot Manager    HD(1,GPT,39e3883c-0eda-4308-988c-3e5ceda6f3e6,0x800,0xfa000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0002* UEFI Hard drive    HD(1,GPT,5aa70335-7817-4b76-9253-5922ce9da98c,0x800,0x40000)/File(\EFI\Boot\bootx64.efi)
Boot0003* Onboard NIC (IPV4)    PciRoot(0x0)/Pci(0x1c,0x4)/Pci(0x0,0x0)/MAC(f8cab8531c89,0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)..BO
Boot0004* Onboard NIC (IPV6)    PciRoot(0x0)/Pci(0x1c,0x4)/Pci(0x0,0x0)/MAC(f8cab8531c89,0)/IPv6([::]:<->[::]:,0,0)..BO
Boot0005* NetWork    BBS(PCMCIA,,0x0)..GO..NO........o.N.e.t.W.o.r.k.........................rN.D+..,.\;..........@..Gd-.;.A..MQ..L.Q.u.a.l.c.o.m.m. .A.t.h.e.r.o.s. .B.o.o.t........BO
Boot0006* Second HDD    BBS(USB,,0x0)..GO..NO..........S.e.c.o.n.d. .H.D.D....................A...........................%8L..C.....F..Gd-.;.A..MQ..L.P.M.9.5.1. .N.V.M.e. .S.A.M.S.U.N.G. .2.5.6.G.B........BO
Boot0007* Hard Drive    BBS(Floppy,,0x0)..GO..NO..........H.a.r.d. .D.r.i.v.e....................A..................1.N........>.;......F..Gd-.;.A..MQ..L.P.1.:. .H.G.S.T. .H.T.S.7.2.1.0.1.0.A.9.E.6.3.0........BO
Boot0008* USB Storage Device    BBS(HD,,0x0)..GO..NO........[.U.S.B. .S.t.o.r.a.g.e. .D.e.v.i.c.e....................A..........................Gd-.;.A..MQ..L.8.1.2.8.2.2.2.2.2.7.8.9........BO

```
But this change nothing in the boot. Windows always boot only and no boot menu appear. When I tried to boot manually on "UEFI Hard Drive", it was the same error message that in ubuntu boot option : "Selected boot device failed. Press any key to reboot the system."

_**EDIT 2 :**_

I tried to do the advice gave in the boot-info : "bcdedit /set {bootmgr} path \EFI\...\grub*.efi" ut it actually broke my mbr and Windows didn't want to boot anymore... I repaired it with the Win10 repair disk.

---

### Post by oldfred on 2016-02-12
I have seen many primarily Windows users edit BCD.
But I think you then boot into Windows and when you choose the ubuntu BCD entry you totally reboot into Ubuntu. UEFI has a one time reboot that then seems to work.

Is /EFI/Boot/bootx64.efi a copy of Windows /efi/Microsoft/Boot/bootmgfw.efi or a copy of /EFI/ubuntu/shimx64.efi. It normally is the Windows file. Or did you copy shim to be bootx64? You can check file sizes to see which is which.

And then can you boot the Hard drive entry? Using one time boot key, often f10 or f12, check manual.

It looks like boot order default is now UEFI hard drive, ubuntu, Windows.
And it still boots only Windows?

Have you updated UEFI? and checked on Alienware's site/forum?
I thought Alienware was part of Dell and Dell just works without any work arounds at all. About the only vendor that has not modified UEFI to make it difficult.

---

### Post by Pryzm on 2016-02-16
I finally succed to install dual boot configuration on my Alienware 15 R2, but it take me so long. I'll try to explain what I did for the others if needed.

First, as I said, my laptop came with Windows 10 pre installed (with lot of Alienware stuff). It has 2 drives : 1 SSD (256 Go - where Windows was installed) and 1 HD (1To for DATA). I decided to install Ubuntu 14.10 in dual boot for work with a liveUSB and I wanted to keep Windows for gaming and others stuff.
I back-up my data, shrink Windows partition (with the Windows tool) and create a liveUSB Ubuntu 14.10.

**First attempt - Ubuntu 14.10, SecureBoot on, UEFI mode (Windows 10 pre installed)**

The liveUSB didn't recognize my SSD drive, so it didn't propose me to "install alongside Windows" and all I can do was to install Ubuntu on 1 To. Moreover, booting on liveUSB to try Ubuntu was too bad because some features didn't work : SSD not found and wifi not working (even Ethernet !).

**Second attempt - Ubuntu 15.10, SecureBoot off, UEFI mode (Windows 10 pre installed)**

After reading some documentation and discussion with some people on ubuntu forums (french and international), I decided to test a liveUSB Ubuntu 15.10 (because new version had more compatibility with NVMe SSD - which is my case) and to desactivate "SecureBoot" and Windows "FastBoot" (which had some incompatibility with linux install).
After creating and booting on liveUSB, the wifi/ethernet worked well and my SSD seemed to be recognize.
I installed Ubuntu "alongside Windows" over the SSD. The installation was fine, I followed "How To Install Ubuntu Linux Alongside Windows 10 (UEFI)" tutorial from everydaylinuxuser.com. My ubuntu UEFI entry was automaticaly the first.

So I reboot. After reboot, no grub menu appeared. PC boot only on Windows, and I have this error "INACCESSIBLE_BOOT_DEVICE" when Windows was loading.
In fact, Windows was only accessible when "SecureBoot" was enabled. I try to manually boot on UEFI ubuntu (in setup menu) but the get the error "Selected boot device failed. Press any key to reboot the system.". Ubuntu didn't want to boot, even if it was SecureBoot disabled or enabled.
I tried to rename .efi files (copy the grub efi file instead of /EFI/Boot/bootx64.efi but it didn't change anything.

So I tried to install rEFInd. I tested it with rEFInd USB flash drive image. After booting on USB, refind menu appeared with some Windows and linux icon.
There was 2 different ways :
    SecureBoot disabled : Ubuntu did boot (Finally ! \o/) but Windows didn't want to
    SecureBoot enabled : Windows did boot but booting on rEFInd USB didn't work
    
So, it was a bit complicated to boot from one to another OS, which forced me to :
- boot with a USB at anytime (I didn't try to install rEFInd on laptop because I thought that with SecureBoot enabled, refind was broken and it didn't permit me to boot on Windows anymore)
- disable/enabled SecureBoot for every switch

**Third attempt - Ubuntu 15.10, SecureBoot off, legacy mode (new install of Windows 10)**

I began to thought that the problem was Windows install in UEFI. It was to difficult for me to boot in the conditions previously said, so I decided to reinstall all my system.
I downloaded MediaCreationTool.exe (the Windows 10 creation tool from Microsoft) and I created a install USB of "Windows 10 Famille Unilingue" (my laptop came with a "Windows 10 Famille"). I disabled SecureBoot and change boot mode to BIOS (legacy).
I erased all my SSD partitions (UEFI, backup, etc.) and split the SSD in 2 partitions. : 1 for Windows and the other for Ubuntu. I was able to install Windows and Ubuntu in the same drive SSD.
But, after two installs, laptop continued to boot only on Windows. I couldn't choose "ubuntu" directly from the setup menu because it was in legacy mode and not evena UEFI mode (I could only boot on "Hard drive"). It tried to boot-repair with a liveUSB Ubuntu but it didn't do anything.

**Fourth attempt - Ubuntu 15.10, SecureBoot off, UEFI mode (new install of Windows 10)**

So I tried to reinstall all my OS in EUFI mode, but with SecureBoot disabled.
The installations were fine. But after the installation, again, laptop only boot on Windows (and oddly, the manually boot on Ubuntu EUFI entry from setup menu didn't work - same error as previously) and boot-repair gave me nothing.
I use refind USB, and it showed me Windows and Ubuntu efi files. The 2 OS were booting with it ! It's close !

But after installing rEFind, the PC only boot in Windows... In fact, I read some PC don't care about other efi files and boot only on Windows (/efi/Microsoft/Boot/bootmgfw.efi) so I copy rEFInd efi file to /efi/Microsoft/Boot/bootmgfw.efi (the "old" /efi/Microsoft/Boot/bootmgfw.efi was copied to another location to keep one efi file to boot on Windows).
And this worked well. Boot shows up rEfInd menu and allow me to choose Windows" or "Ubuntu" (after cleanup some efi files :))



So, the installation of this dual boot was tricky and forced me to completely reinstall Windows because of some points :
- Ubuntu 14.10 had some issues with my hardware (SSD and wifi/ethernet card)
- pre installed Windows only work with SecureBoot, but Ubuntu wasn't able to recognize my SSD in SecureBoot
- my laptop only wants to boot to Windows by using this efi file : /efi/Microsoft/Boot/bootmgfw.efi

I specify that Alienware doesn't support linux install (message on alienware forum) which didn't help ^^


Now, I have a proper dual boot but I need to work on some others issues :
- my new installed Windows doesn't want to activate :/
- when I plug another HDMI screen on Ubuntu, it didn't work on the second screen ("Frequencies not supported") but in Windows it's ok. I tried some tricks with Compiz and xrandr, but it didn't work at all... DO you have any idea ?
- On Ubuntu, battery life is lower than Windows, and the "Hard drive light" constantly flash. Is the HD or SSD constantly used ? How to know ?

EDIT : for the wonstant use of hard drive (probably SSD :/), it seems to be journaling which write on disk all the time. I tried to google it, but I didn't find any solutions. Do you have ?

---

### Post by oldfred on 2016-02-16
You may want separate threads on both video & drive issues.

If booting with Intel that may need one kind of fix, if booting with nVidia then different fixes. Can you control what you boot with in UEFI? Post details in new thread.

Journal just records writes. But reads normally update a timestamp. With SSD, we change defaults to noatime in fstab. On my hard drive is use relatime.
I think this is current. If you need more info start a new thread on drive issues.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by gehiks on 2016-11-05
Do you have any updates on that issue?
What did you do in the end?
Have you heard of or found a way to keep the pre installed win 10?

Thanks,

Gêhïks

---

