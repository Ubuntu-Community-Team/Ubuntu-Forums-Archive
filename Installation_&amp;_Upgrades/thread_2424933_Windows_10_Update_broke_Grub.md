---
title: "Windows 10 Update broke Grub"
date: 2019-08-17
forum: Installation &amp; Upgrades
---

### Post by nyktovus on 2019-08-17
yo, 

My Win10 just ran an update, and it put Grub into rescue mode. Now I cannot boot into either Win10 or Ubuntu 18.04. I am trying to figure out how to repair this, but i was also considering reinstalling a different flavor of ubuntu.. 
should i repair the boot first or just rerun an installer for ubuntu and hope that fixes the issue?

---

### Post by Impavidus on 2019-08-17
Get your live disk (the one with the Ubuntu installer) and choose to try Ubuntu before installing. Then install [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair), create a BootInfo summary and show us the link. That will give us a nice load of diagnostic information.

---

### Post by nyktovus on 2019-08-17
boot info data incoming! just to note. sdb is my data drive.. a 1tb drive just for stashing goods.. all os linux and windows are on sda
sdc is the usb drive i'm booting off. thanx again!!
```

 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Windows 7/8/2012 is installed in the MBR of /dev/sdb.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03 2014-10-06................................................2....0............A20 gate n
    Boot sector info:  Syslinux looks at sector 3178544 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the /multiboot 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg 
                       /multiboot/lubuntu-18.04.2-desktop-amd64/EFI/BOOT/grubx
                       64.efi 
                       /multiboot/xubuntu-18.04.2-desktop-amd64/EFI/BOOT/grubx
                       64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     1,026,047     1,024,000   7 NTFS / exFAT / HPFS
/dev/sda2           1,026,048   262,367,378   261,341,331   7 NTFS / exFAT / HPFS
/dev/sda3         262,369,280   264,058,879     1,689,600  27 Hidden NTFS (Recovery Environment)
/dev/sda4         264,062,974   468,860,927   204,797,954   5 Extended
/dev/sda5         451,561,472   468,860,927    17,299,456  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048 1,953,519,615 1,953,517,568   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 14.7 GiB, 15728640000 bytes, 30720000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048    30,719,999    30,717,952   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       2019-02-10-00-41-03-00                 iso9660    Ubuntu-MATE 18.04.2 LTS amd64
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/sda1        EE44A53844A50485                       ntfs       System Reserved
/dev/sda2        D2EAAD47EAAD28A5                       ntfs       
/dev/sda3        B8944C02944BC21C                       ntfs       
/dev/sda5        205f0637-64e7-4508-bf0e-822e4c7da884   swap       
/dev/sdb1        CA74AC6E74AC5EC7                       ntfs       data
/dev/sdc1        9E6D-7C70                              vfat       MULTIBOOT

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Aug 18 03:50 ata-DREVO_X1_SSD_TX1711902632 -> ../../sda
lrwxrwxrwx 1 root root 10 Aug 18 03:50 ata-DREVO_X1_SSD_TX1711902632-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Aug 18 03:50 ata-DREVO_X1_SSD_TX1711902632-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Aug 18 03:50 ata-DREVO_X1_SSD_TX1711902632-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Aug 18 03:50 ata-DREVO_X1_SSD_TX1711902632-part4 -> ../../sda4
lrwxrwxrwx 1 root root 10 Aug 18 03:50 ata-DREVO_X1_SSD_TX1711902632-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Aug 18 03:50 ata-WDC_WD1002FAEX-00Y9A0_WD-WCAW35400119 -> ../../sdb
lrwxrwxrwx 1 root root 10 Aug 18 03:50 ata-WDC_WD1002FAEX-00Y9A0_WD-WCAW35400119-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 Aug 17 20:48 ata-hp_DVD_A_DH16ABLH_3F8113905767 -> ../../sr0
lrwxrwxrwx 1 root root  9 Aug 18 03:50 usb-General_UDisk-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Aug 18 03:50 usb-General_UDisk-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Aug 18 03:50 wwn-0x50014ee2b2e35b2b -> ../../sdb
lrwxrwxrwx 1 root root 10 Aug 18 03:50 wwn-0x50014ee2b2e35b2b-part1 -> ../../sdb1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /cdrom                   iso9660    (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /isodevice               vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================== sdc1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             syslinux.cfg                                   1

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/4687/mountinfo) leaked on lvs invocation. Parent PID 12739: bash
File descriptor 63 (pipe:[61430]) leaked on lvs invocation. Parent PID 12739: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 20190818_0350 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
boot-repair is executed in live-session (Ubuntu 18.04.2 LTS, bionic, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
file=/cdrom/preseed/ubuntu-mate.seed noprompt boot=casper iso-scan/filename=/multiboot/ubuntu-mate-18.04.2-desktop-amd64/ubuntu-mate-18.04.2-desktop-amd64.iso quiet --
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:
/dev/sda1:Windows 10:Windows:chain

=================== blkid:
/dev/sda1: LABEL="System Reserved" UUID="EE44A53844A50485" TYPE="ntfs" PARTUUID="ab57f763-01"
/dev/sda2: UUID="D2EAAD47EAAD28A5" TYPE="ntfs" PARTUUID="ab57f763-02"
/dev/sda3: UUID="B8944C02944BC21C" TYPE="ntfs" PARTUUID="ab57f763-03"
/dev/sdb1: LABEL="data" UUID="CA74AC6E74AC5EC7" TYPE="ntfs" PARTUUID="7d46cd0e-01"
/dev/sdc1: LABEL="MULTIBOOT" UUID="9E6D-7C70" TYPE="vfat" PARTUUID="12a04c3f-01"
/dev/loop0: UUID="2019-02-10-00-41-03-00" LABEL="Ubuntu-MATE 18.04.2 LTS amd64" TYPE="iso9660" PTUUID="590045af" PTTYPE="dos"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/sda5: UUID="205f0637-64e7-4508-bf0e-822e4c7da884" TYPE="swap" PARTUUID="ab57f763-05"


1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda2.

=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	notbiosboot, /mnt/boot-sav/sda1.
sda2	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/sda2.
sda3	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/sda3.
sdb1	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/sdb1.
sdc1	: sdc,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	notbiosboot, /isodevice.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	not-mmc, no-os,	2048 sectors * 512 bytes
sdc	: not-GPT,	BIOSboot-not-needed,	has-correctEFI, 	liveusb,	not-mmc, no-os,	2048 sectors * 512 bytes


=================== parted -lm:

BYT;
/dev/sda:240GB:scsi:512:512:msdos:ATA DREVO X1 SSD:;
1:1049kB:525MB:524MB:ntfs::boot;
2:525MB:134GB:134GB:ntfs::;
3:134GB:135GB:865MB:ntfs::diag;
4:135GB:240GB:105GB:::;
5:231GB:240GB:8857MB:linux-swap(v1)::;

BYT;
/dev/sdb:1000GB:scsi:512:512:msdos:ATA WDC WD1002FAEX-0:;
1:1049kB:1000GB:1000GB:ntfs::boot;

BYT;
/dev/sdc:15.7GB:scsi:512:512:msdos:General UDisk:;
1:1049kB:15.7GB:15.7GB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
loop0 loop iso9660    1.9G Ubuntu-MATE 18.04.2 LTS amd64
loop1 loop squashfs   1.8G
loop2 loop squashfs    91M
loop3 loop squashfs   7.9M
loop4 loop squashfs  71.7M
loop5 loop squashfs  87.3M
sda   disk          223.6G
sda1  part ntfs       500M System Reserved
sda2  part ntfs     124.6G
sda3  part ntfs       825M
sda4  part              1K
sda5  part swap       8.3G
sdb   disk          931.5G
sdb1  part ntfs     931.5G data
sdc   disk           14.7G
sdc1  part vfat      14.7G MULTIBOOT
sr0   rom            1024M

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  0  0         /cdrom
loop1    1  1  0         /rofs
loop2    1  1  0         /snap/core/6350
loop3    1  1  0         /snap/pulsemixer/23
loop4    1  1  0         /snap/software-boutique/31
loop5    1  1  0         /snap/ubuntu-mate-welcome/220
sda      0  0  0 running
sda1     0  0  0         /mnt/boot-sav/sda1
sda2     0  0  0         /mnt/boot-sav/sda2
sda3     0  0  0         /mnt/boot-sav/sda3
sda4     0  0  0
sda5     0  0  0         [SWAP]
sdb      1  0  0 running
sdb1     1  0  0         /mnt/boot-sav/sdb1
sdc      1  0  1 running
sdc1     1  0  1         /isodevice
sr0      1  0  1 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=6083484k,nr_inodes=1520871,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1221192k,mode=755)
/dev/sdc1 on /isodevice type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/loop1 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=24,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=19007)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=1221188k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/var/lib/snapd/snaps/core_6350.snap on /snap/core/6350 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/pulsemixer_23.snap on /snap/pulsemixer/23 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/software-boutique_31.snap on /snap/software-boutique/31 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/ubuntu-mate-welcome_220.snap on /snap/ubuntu-mate-welcome/220 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 sda2 sda3 sda4 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 dvd dvdrw ecryptfs fb0 fd full fuse gpiochip0 hidraw0 hidraw1 hidraw2 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 initctl input kmsg kvm lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sdb sdb1 sdc sdc1 sg0 sg1 sg2 sg3 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio vfio vga_arbiter vhci vhost-net vhost-vsock zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 9f 0f 00 00 00 00 00  |................|
00000030  aa a6 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  85 04 a5 44 38 a5 44 ee  |...........D8.D.|
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
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 0f 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  92 c0 93 0f 00 00 00 00  |................|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  a5 28 ad ea 47 ad ea d2  |.........(..G...|
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

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 70 a3 0f  |........?....p..|
00000020  00 00 00 00 80 00 80 00  ff c7 19 00 00 00 00 00  |................|
00000030  00 13 01 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  1c c2 4b 94 02 4c 94 b8  |..........K..L..|
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

=================== hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 4f 70 74 00 00 00 00  |.........Opt....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  c7 5e ac 74 6e ac 74 ca  |.........^.tn.t.|
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

=================== hexdump -n512 -C /dev/sdc1
00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 10 f0 0a  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 b8 d4 01 88 3a 00 00  00 00 00 00 02 00 00 00  |.....:..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 70 7c 6d 9e 4e  4f 20 4e 41 4d 45 20 20  |..)p|m.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d f8 50 50 50 50 cd  13 eb 62 8b 55 aa 8b 75  |.M.PPPP...b.U..u|
000000a0  a8 c1 ee 04 01 f2 83 fa  4f 76 31 81 fa b2 07 73  |........Ov1....s|
000000b0  2b f6 45 b4 7f 75 25 38  4d b8 74 20 66 3d 21 47  |+.E..u%8M.t f=!G|
000000c0  50 54 75 10 80 7d b8 ed  75 0a 66 ff 75 ec 66 ff  |PTu..}..u.f.u.f.|
000000d0  75 e8 eb 0f 51 51 66 ff  75 bc eb 07 51 51 66 ff  |u...QQf.u...QQf.|
000000e0  36 1c 7c b4 08 e8 e9 00  72 13 20 e4 75 0f c1 ea  |6.|.....r. .u...|
000000f0  08 42 89 16 1a 7c 83 e1  3f 89 0e 18 7c fb bb aa  |.B...|..?...|...|
00000100  55 b4 41 e8 cb 00 72 10  81 fb 55 aa 75 0a f6 c1  |U.A...r...U.u...|
00000110  01 74 05 c6 06 46 7d 00  66 b8 30 80 30 00 66 ba  |.t...F}.f.0.0.f.|
00000120  00 00 00 00 bb 00 80 e8  0e 00 66 81 3e 1c 80 8e  |..........f.>...|
00000130  c1 80 6a 75 74 e9 f8 02  66 03 06 60 7b 66 13 16  |..jut...f..`{f..|
00000140  64 7b b9 10 00 eb 2b 66  52 66 50 06 53 6a 01 6a  |d{....+fRfP.Sj.j|
00000150  10 89 e6 66 60 b4 42 e8  77 00 66 61 8d 64 10 72  |...f`.B.w.fa.d.r|
00000160  01 c3 66 60 31 c0 e8 68  00 66 61 e2 da c6 06 46  |..f`1..h.fa....F|
00000170  7d 2b 66 60 66 0f b7 36  18 7c 66 0f b7 3e 1a 7c  |}+f`f..6.|f..>.||
00000180  66 f7 f6 31 c9 87 ca 66  f7 f7 66 3d ff 03 00 00  |f..1...f..f=....|
00000190  77 17 c0 e4 06 41 08 e1  88 c5 88 d6 b8 01 02 e8  |w....A..........|
000001a0  2f 00 66 61 72 01 c3 e2  c9 31 f6 8e d6 bc 68 7b  |/.far....1....h{|
000001b0  8e de 66 8f 06 78 00 be  da 7d ac 20 c0 74 09 b4  |..f..x...}. .t..|
000001c0  0e bb 07 00 cd 10 eb f2  31 c0 cd 16 cd 19 f4 eb  |........1.......|
000001d0  fd 8a 16 74 7b 06 cd 13  07 c3 42 6f 6f 74 20 65  |...t{.....Boot e|
000001e0  72 72 6f 72 0d 0a 00 00  00 00 00 00 00 00 00 00  |rror............|
000001f0  00 00 00 00 00 00 00 00  fe 02 b2 3e 18 37 55 aa  |...........>.7U.|
00000200

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  5.9G     0  5.9G   0% /dev
tmpfs          tmpfs     1.2G  1.4M  1.2G   1% /run
/dev/sdc1      vfat       15G  5.8G  9.0G  40% /isodevice
/dev/loop0     iso9660   2.0G  2.0G     0 100% /cdrom
/dev/loop1     squashfs  1.9G  1.9G     0 100% /rofs
/cow           overlay   5.9G  439M  5.4G   8% /
tmpfs          tmpfs     5.9G   35M  5.8G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     5.9G     0  5.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     5.9G  8.0K  5.9G   1% /tmp
tmpfs          tmpfs     1.2G   44K  1.2G   1% /run/user/999
/dev/loop2     squashfs   91M   91M     0 100% /snap/core/6350
/dev/loop3     squashfs  8.0M  8.0M     0 100% /snap/pulsemixer/23
/dev/loop4     squashfs   72M   72M     0 100% /snap/software-boutique/31
/dev/loop5     squashfs   88M   88M     0 100% /snap/ubuntu-mate-welcome/220
/dev/sda1      fuseblk   500M   29M  472M   6% /mnt/boot-sav/sda1
/dev/sda2      fuseblk   125G   22G  103G  18% /mnt/boot-sav/sda2
/dev/sda3      fuseblk   825M  470M  356M  57% /mnt/boot-sav/sda3
/dev/sdb1      fuseblk   932G  327G  606G  36% /mnt/boot-sav/sdb1

=================== fdisk -l:
Disk /dev/loop0: 1.9 GiB, 2053521408 bytes, 4010784 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x590045af

Device       Boot Start     End Sectors  Size Id Type
/dev/loop0p1 *        0 4010783 4010784  1.9G  0 Empty
/dev/loop0p2      16144   21071    4928  2.4M ef EFI (FAT-12/16/32)


Disk /dev/loop1: 1.8 GiB, 1960402944 bytes, 3828912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 91 MiB, 95408128 bytes, 186344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 7.9 MiB, 8294400 bytes, 16200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 71.7 MiB, 75120640 bytes, 146720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 87.3 MiB, 91504640 bytes, 178720 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xab57f763

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048   1026047   1024000   500M  7 HPFS/NTFS/exFAT
/dev/sda2         1026048 262367378 261341331 124.6G  7 HPFS/NTFS/exFAT
/dev/sda3       262369280 264058879   1689600   825M 27 Hidden NTFS WinRE
/dev/sda4       264062974 468860927 204797954  97.7G  5 Extended
/dev/sda5       451561472 468860927  17299456   8.3G 82 Linux swap / Solaris


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7d46cd0e

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1  *     2048 1953519615 1953517568 931.5G  7 HPFS/NTFS/exFAT




Disk /dev/sdc: 14.7 GiB, 15728640000 bytes, 30720000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x12a04c3f

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 30719999 30717952 14.7G  c W95 FAT32 (LBA)




=================== Suggested repair
The default repair of the Boot-Repair utility would restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by yancek on 2019-08-18
If you look at the top of the boot repair output, you will see that it shows Grub boot code in the MBR of the drive and it points to the remaining Grub files necessary to boot on sda6.  sda6 does not exist and the only sign of any Linux system is sda5, the swap partition.  If you have data, you may try to recover it with testdisk otherwise a new install.  Not sure why a windows update would do something like that, unusual.

---

### Post by Impavidus on 2019-08-18
It's a known bug in Windows. Sometimes when Windows updates, it deletes logical Linux partitions. In your case, it deleted /dev/sda6, which was your main Ubuntu partition, containing some code vital to grub, the bootloader. Without the bootloader you can't even start Windows.

All data should still be there on the hard drive. I expect the lost partition was at the start of the extended partition, taking most of the space between sector 264,062,974 and 451,561,472. With a bit of luck, gnu parted or testdisk can recover the lost partition.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I never had to try this myself.

---

### Post by nyktovus on 2019-08-18
ill be honest i have nothing vital on my linux partition and was planning to reinstall anyway before this happened. 

i do however have vital info on windows that i cant lose.. 

can i just reinstall ubuntu and carry on without fear that itll eat my windows data and fix the boot loader?

---

### Post by ubfan1 on 2019-08-18
Should be no problem, the deleted partition is now free space, so a normal install should work.  I like yanck's suggestion, just run a partition tool and restore the partition manually start at 
264,062,974 (start of extended partition), and end at 451,561,471 (one less than start of swap).  Assuming you only have the one root partition that
got deleted.

---

### Post by Impavidus on 2019-08-18
If you have vital information, you need backups. Always.

When you reinstall Ubuntu in the unallocated space (install alongside or something else a.k.a. manual partitioning), it will fix the bootloader and keep Windows undamaged. That is assuming FastStartup is off, which seems to be the case from your BootRepair output. But you should have backups of your vital data anyway. You can use your live disk to access the Windows partition and make those backups on an external drive, if you don't have them already.

BootRepair's default repair should also fix Windows booting.

---

