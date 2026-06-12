---
title: "Boot-Repair Output"
date: 2016-09-20
forum: Installation &amp; Upgrades
---

### Post by combrink.jc on 2016-09-20
Below is my Boot-repair output file. The program advised me to post to forum and email to boot-repair team. I dit both.
I am new to Linux. Just trying to install ubuntu gnome 14.04 to my PC. Succesfully installed Ubuntu gnome 16.04 from USB made by unetbootin from windows 10. Nothing worked very well and I decided to go to 14.04. Still on 16.04 I downloaded 14.04 ISO and unetbootin again. Made the USB into installer and tried to install. Got error of something like failed to install grub2 to /target. Followed a bunch of advice and methods to get it fixed. Nothing worked so far.

Thank you in advance.

```
ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-09-20__18h45 ===================
boot-repair version : 4ppa38
boot-sav version : 4ppa38
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa38
boot-repair is executed in live-session (Ubuntu 14.04.4 LTS, trusty, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu-gnome.seed boot=casper quiet splash --
ls: cannot access /home/usr/.config: No such file or directory

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda2:Ubuntu 14.04.4 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="1785-E721" TYPE="vfat"
/dev/sda2: UUID="98a797f6-8afd-49fb-9c51-489dcfa317fa" TYPE="ext4"
/dev/sda3: UUID="02ea9d24-b599-45ab-85af-1f42800de678" TYPE="swap"
/dev/sdb2: LABEL="Data" UUID="E6901E5B901E3313" TYPE="ntfs"
/dev/sdc1: LABEL="OKOKOK" UUID="4430-DF4A" TYPE="vfat"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.

Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Microsoft file detected: /mnt/boot-sav/sda1/EFI/Microsoft/Boot/bootx64.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/sda1/EFI/Boot/bootx64.efi
No sda2/etc/default/grub

=================== sda2/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Sep 20 16:46 grub.d
total 76
-rwxr-xr-x 1 root root  9791 Dec 17  2015 00_header
-rwxr-xr-x 1 root root  6058 May 13  2015 05_debian_theme
-rwxr-xr-x 1 root root 11608 Dec 17  2015 10_linux
-rwxr-xr-x 1 root root 10412 Dec 17  2015 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 Dec 17  2015 30_os-prober
-rwxr-xr-x 1 root root  1418 Aug  2 07:27 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec 17  2015 40_custom
-rwxr-xr-x 1 root root   216 Dec 17  2015 41_custom
-rw-r--r-- 1 root root   483 Dec 17  2015 README


/boot/efi detected in the fstab of sda2: UUID=1785-E721   (sda1)

=================== efibootmgr -v
BootCurrent: 0006
Timeout: 0 seconds
BootOrder: 0000,0006,0007,0008
Boot0000* grub    HD(1,800,100000,8c15024d-2ad5-4916-822d-1cce5192fedd)File(EFIgrubgrubx64.efi)
Boot0006* UEFI: SanDisk Cruzer Blade    ACPI(a0341d0,0)PCI(7,0)PCI(0,0)USB(3,0)HD(1,20,1dd17e0,e691dc7c)AMBO
Boot0007* ubuntu    HD(1,800,100000,8c15024d-2ad5-4916-822d-1cce5192fedd)File(EFIUbuntugrubx64.efi)
Boot0008* Windows Boot Manager    HD(1,800,100000,8c15024d-2ad5-4916-822d-1cce5192fedd)File(EFIMicrosoftBootbootmgfw.efi)

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    grubenv-ok    grub1,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sdb2    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb2.

sda    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    no-os,    34 sectors * 512 bytes


=================== parted -l:

Model: ATA TS128GSSD370 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name                  Flags
1      1049kB  538MB  537MB   fat32           EFI System Partition  boot
2      538MB   120GB  119GB   ext4
3      120GB   128GB  8485MB  linux-swap(v1)


Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
1      17.4kB  134MB   134MB                Microsoft reserved partition  msftres
2      135MB   1000GB  1000GB  ntfs         Basic data partition          msftdata


Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdc: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  16.0GB  16.0GB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:128GB:scsi:512:512:gpt:ATA TS128GSSD370;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot;
2:538MB:120GB:119GB:ext4::;
3:120GB:128GB:8485MB:linux-swap(v1)::;

BYT;
/dev/sdb:1000GB:scsi:512:4096:gpt:ATA TOSHIBA DT01ACA1;
1:17.4kB:134MB:134MB::Microsoft reserved partition:msftres;
2:135MB:1000GB:1000GB:ntfs:Basic data partition:msftdata;

BYT;
/dev/sdc:16.0GB:scsi:512:512:msdos:SanDisk Cruzer Blade;
1:16.4kB:16.0GB:16.0GB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
sda   disk          119.2G
sda1  part vfat       512M
sda2  part ext4     110.9G
sda3  part swap       7.9G
sdb   disk          931.5G
sdb1  part            128M
sdb2  part ntfs     931.4G Data
sdc   disk           14.9G
sdc1  part vfat      14.9G OKOKOK
sr0   rom            1024M
loop0 loop squashfs 917.6M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      0  0  0 running
sda1     0  0  0         /mnt/boot-sav/sda1
sda2     0  0  0         /mnt/boot-sav/sda2
sda3     0  0  0         [SWAP]
sdb      1  0  0 running
sdb1     1  0  0
sdb2     1  0  0         /mnt/boot-sav/sdb2
sdc      1  0  1 running
sdc1     1  0  1         /cdrom
sr0      1  0  1 running
loop0    1  1  0         /rofs


=================== mount:
/cow on / type overlay (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdc1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
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
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu-gnome)
/dev/sda1 on /mnt/boot-sav/sda1 type vfat (rw)
/dev/sda2 on /mnt/boot-sav/sda2 type ext4 (rw)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse fw0 hidraw0 hidraw1 hidraw2 hidraw3 hpet hwrng i2c-0 i2c-1 i2c-10 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 input kfd kmsg kvm log mapper mcelog mem memory_bandwidth ndctl0 net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 10 00 fe 03 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 21 e7 85 17 4e  4f 20 4e 41 4d 45 20 20  |..)!...NO NAME  |
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

=================== hexdump -n512 -C /dev/sdb2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 04 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 5f 6c 74 00 00 00 00  |........._lt....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  13 33 1e 90 5b 1e 90 e6  |.........3..[...|
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


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs     789M  1.5M  787M   1% /run
/dev/sdc1      vfat       15G  998M   14G   7% /cdrom
/dev/loop0     squashfs  918M  918M     0 100% /rofs
/cow           overlay   3.9G  116M  3.8G   3% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     3.9G  8.0K  3.9G   1% /tmp
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     3.9G  136K  3.9G   1% /run/shm
none           tmpfs     100M   36K  100M   1% /run/user
/dev/sda1      vfat      511M  7.5M  504M   2% /mnt/boot-sav/sda1
/dev/sda2      ext4      109G  3.8G  100G   4% /mnt/boot-sav/sda2
/dev/sdb2      fuseblk   932G  206G  726G  23% /mnt/boot-sav/sdb2

=================== fdisk -l:

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   250069679   125034839+  ee  GPT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe691dc7c

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    31266815    15633392    c  W95 FAT32 (LBA)



=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of sda2, using the following options:        sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s    use-standard-efi-file rename-ms-efi


/boot/efi added in sda2/fstab
rm /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootmgfw.efi /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootmgfw.efi.grb
rm /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootx64.efi /mnt/boot-sav/sda1/efi/Microsoft/Boot/bootx64.efi.grb
rm /mnt/boot-sav/sda1/efi/Boot/bootx64.efi /mnt/boot-sav/sda1/efi/Boot/bootx64.efi.grb
Mount sda1 on /mnt/boot-sav/sda2/boot/efi
ls sda1/efi: /ubuntu/shimx64.efi /ubuntu/MokManager.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /ubuntu/fwupx64.efi /ubuntu/fw /Microsoft/Boot /grub/grubx64.efi

*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Curacao PRO [Radeon R7 370 / R9 270/370 OEM] [1002:6811]
Subsystem: Gigabyte Technology Co., Ltd Device [1458:226c]
Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series] [1002:aab0]
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1.12,grub-install (GRUB) 2.

chroot /mnt/boot-sav/sda2 efibootmgr -v
BootCurrent: 0006
Timeout: 0 seconds
BootOrder: 0000,0006,0007,0008
Boot0000* grub    HD(1,800,100000,8c15024d-2ad5-4916-822d-1cce5192fedd)File(EFIgrubgrubx64.efi)
Boot0006* UEFI: SanDisk Cruzer Blade    ACPI(a0341d0,0)PCI(7,0)PCI(0,0)USB(3,0)HD(1,20,1dd17e0,e691dc7c)AMBO
Boot0007* ubuntu    HD(1,800,100000,8c15024d-2ad5-4916-822d-1cce5192fedd)File(EFIUbuntugrubx64.efi)
Boot0008* Windows Boot Manager    HD(1,800,100000,8c15024d-2ad5-4916-822d-1cce5192fedd)File(EFIMicrosoftBootbootmgfw.efi)

chroot /mnt/boot-sav/sda2 uname -r
Kernel: 4.2.0-27-generic

Reinstall the grub-efi-amd64-signed of sda2
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0
ls sda1/efi: /ubuntu/shimx64.efi /ubuntu/MokManager.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /ubuntu/fwupx64.efi /ubuntu/fw /Microsoft/Boot /grub/grubx64.efi
df /dev/sda1
cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (& .grb)
df /dev/sda1
cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Microsoft/Boot/bootx64.efi (& .grb)
df /dev/sda1
cp /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/shimx64.efi /mnt/boot-sav/sda2/boot/efi/EFI/Boot/bootx64.efi (& .grb)
ls sda1/efi: /Microsoft/Boot/bootx64.efi.grb /Microsoft/Boot/bootx64.efi /Microsoft/Boot/bootmgfw.efi.grb /Microsoft/Boot/bootmgfw.efi /ubuntu/shimx64.efi /ubuntu/MokManager.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /ubuntu/fwupx64.efi /ubuntu/fw /Microsoft/Boot /grub/grubx64.efi /Boot/bootx64.efi.grb /Boot/bootx64.efi
Add /mnt/boot-sav/sda2/boot/efi efi entries in /mnt/boot-sav/sda2/etc/grub.d/25_custom
Adding custom /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/fwupx64.efi
Adding custom /mnt/boot-sav/sda2/boot/efi/EFI/ubuntu/MokManager.efi

chroot /mnt/boot-sav/sda2 efibootmgr -v
BootCurrent: 0006
Timeout: 0 seconds
BootOrder: 0000,0006,0007,0008
Boot0000* grub    HD(1,800,100000,8c15024d-2ad5-4916-822d-1cce5192fedd)File(EFIgrubgrubx64.efi)
Boot0006* UEFI: SanDisk Cruzer Blade    ACPI(a0341d0,0)PCI(7,0)PCI(0,0)USB(3,0)HD(1,20,1dd17e0,e691dc7c)AMBO
Boot0007* ubuntu    HD(1,800,100000,8c15024d-2ad5-4916-822d-1cce5192fedd)File(EFIUbuntugrubx64.efi)
Boot0008* Windows Boot Manager    HD(1,800,100000,8c15024d-2ad5-4916-822d-1cce5192fedd)File(EFIMicrosoftBootbootmgfw.efi)

chroot /mnt/boot-sav/sda2 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.2.0-42-generic
Found initrd image: /boot/initrd.img-4.2.0-42-generic
Found linux image: /boot/vmlinuz-4.2.0-27-generic
Found initrd image: /boot/initrd.img-4.2.0-27-generic
Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda (128GB) disk!
gawk pastebinit  packages needed
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release](http://archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'restricted/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Package 'gawk' has no installation candidate
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/trusty/Release](http://archive.ubuntu.com/ubuntu/dists/trusty/Release)  Unable to find expected entry 'restricted/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Package 'gawk' has no installation candidate
Could not install gawk pastebinit
Please install the [gawk pastebinit ] packages.  Then try again.
```

---

### Post by oldfred on 2016-09-20
Please use Code tags for longer text. Easy to add with Forum's advanced editor & # icon.
But with Boot-Repair's summary report better to just post link to paste bin site.
And you have not posted entire output, forum may have limited that.
But it seems to even have issues with paste bin?
> Could not install gawk pastebinit
Please install the [gawk pastebinit ] packages.  Then try again.

Was Internet working when you ran report?

What brand/model system?

---

