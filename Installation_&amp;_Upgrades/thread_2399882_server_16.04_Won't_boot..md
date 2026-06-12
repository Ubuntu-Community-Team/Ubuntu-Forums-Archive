---
title: "server 16.04 Won't boot."
date: 2018-08-30
forum: Installation &amp; Upgrades
---

### Post by wlraider70 on 2018-08-30
I had a power outage and now it seems that I can't boot.

I ran "boot-repair" and it says. 


```
 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by TheFu on 2018-08-30
Looks like the VM file and partition table was totally corrupted.  I don't know how to recover from that except to restore from backups.  I've never seen anything like the corruption of the partition table posted.

---

### Post by wlraider70 on 2018-08-30
I restored from a backup and still have issues. I reran the boot-repair, this time I had automatic options, but they failed.

```


 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: unknown filesystem type ''.

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: unknown filesystem type ''.
mount: /mnt/BootInfo/sda2: unknown filesystem type ''.

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: unknown filesystem type ''.
mount: /mnt/BootInfo/sda2: unknown filesystem type ''.
mount: /mnt/BootInfo/sda3: unknown filesystem type ''.

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/sda1: unknown filesystem type ''.
mount: /mnt/BootInfo/sda2: unknown filesystem type ''.
mount: /mnt/BootInfo/sda3: unknown filesystem type ''.
mount: /mnt/BootInfo/sda4: unknown filesystem type ''.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 133 GiB, 142807662592 bytes, 278921216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.
/dev/sda1     ? 1,852,793,632 3,672,036,755 1,819,243,124  69 Unknown
/dev/sda2     ? 1,936,026,985 3,755,203,720 1,819,176,736  6f Unknown
/dev/sda3     ? 1,919,247,465 3,738,098,568 1,818,851,104  65 Novell Netware 386
/dev/sda4     ?   543,452,769 2,245,123,539 1,701,670,771  6f Unknown

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda3
/dev/sda1 overlaps with /dev/sda4
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda2 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda4
/dev/sda3 ends after the last sector of /dev/sda
/dev/sda3 overlaps with /dev/sda4
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 32 GiB, 34359738368 bytes, 67108864 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sr0         2017-10-29-00-56-18-00                 iso9660    Boot-Repair-Disk 64bit
/dev/zram0       d4837fe5-a265-4be3-bcb4-a1370b9cdbe0   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root 9 Aug 30 23:48 ata-QEMU_DVD-ROM_QM00003 -> ../../sr0
lrwxrwxrwx 1 root root 9 Aug 30 23:48 scsi-0QEMU_QEMU_HARDDISK_drive-scsi0 -> ../../sda
lrwxrwxrwx 1 root root 9 Aug 30 23:48 scsi-0QEMU_QEMU_HARDDISK_drive-scsi1 -> ../../sdb

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sda

00000000  65 73 20 74 6f 20 74 68  65 20 63 68 65 63 6b 62  |es to the checkb|
00000010  6f 78 20 74 6f 20 74 61  6b 65 20 65 66 66 65 63  |ox to take effec|
00000020  74 2e 22 2c 0a 20 20 20  20 20 20 22 6d 65 73 73  |t.",.      "mess|
00000030  61 67 65 22 3a 20 22 48  75 6c 75 2e 63 6f 6d 20  |age": "Hulu.com |
00000040  e0 aa a8 e0 ab 80 20 e0  aa a6 e0 aa b0 e0 ab 87  |...... .........|
00000050  e0 aa 95 20 e0 aa ac e0  aa be e0 aa 9c e0 ab 81  |... ............|
00000060  e0 aa 8f 20 e0 aa b5 e0  aa bf e0 aa a1 e0 aa bf  |... ............|
00000070  e0 aa 93 e0 aa 9d 20 e0  aa aa e0 ab 8d e0 aa b2  |...... .........|
00000080  e0 ab 87 20 e0 aa a8 e0  aa be 20 e0 aa a5 e0 aa  |... ...... .....|
00000090  be e0 aa af 20 e0 aa a4  e0 ab 8b 20 28 e0 aa a4  |.... ...... (...|
000000a0  e0 aa ae e0 aa be e0 aa  b0 e0 aa be 20 e0 aa ac  |............ ...|
000000b0  e0 ab 8d e0 aa b0 e0 aa  be e0 aa 89 e0 aa 9d e0  |................|
000000c0  aa b0 20 e0 aa aa e0 ab  81 e0 aa a8 e0 aa 83 e0  |.. .............|
000000d0  aa b6 e0 aa b0 e0 ab 82  20 e0 aa 9c e0 aa b0 e0  |........ .......|
000000e0  ab 82 e0 aa b0 e0 ab 80  20 e0 aa 9b e0 ab 87 29  |........ ......)|
000000f0  22 0a 20 20 20 7d 2c 0a  20 20 20 22 79 65 73 22  |".   },.   "yes"|
00000100  3a 20 7b 0a 20 20 20 20  20 20 22 64 65 73 63 72  |: {.      "descr|
00000110  69 70 74 69 6f 6e 22 3a  20 22 41 20 70 6f 73 69  |iption": "A posi|
00000120  74 69 76 65 20 72 65 73  70 6f 6e 73 65 20 74 6f  |tive response to|
00000130  20 61 20 71 75 65 73 74  69 6f 6e 22 2c 0a 20 20  | a question",.  |
00000140  20 20 20 20 22 6d 65 73  73 61 67 65 22 3a 20 22  |    "message": "|
00000150  e0 aa b9 e0 aa be 22 0a  20 20 20 7d 2c 0a 20 20  |......".   },.  |
00000160  20 22 79 6f 75 5f 63 61  6e 5f 73 6c 69 64 65 5f  | "you_can_slide_|
00000170  74 6f 5f 63 68 61 6e 67  65 22 3a 20 7b 0a 20 20  |to_change": {.  |
00000180  20 20 20 20 22 64 65 73  63 72 69 70 74 69 6f 6e  |    "description|
00000190  22 3a 20 22 49 6e 73 74  72 75 63 74 69 6f 6e 73  |": "Instructions|
000001a0  20 66 6f 72 20 68 6f 77  20 74 6f 20 75 73 65 20  | for how to use |
000001b0  74 68 65 20 77 68 69 74  65 6c 69 73 74 65 72 20  |the whitelister |
000001c0  73 6c 69 64 65 72 20 63  6f 6e 74 72 6f 6c 73 2e  |slider controls.|
000001d0  20 53 6f 6d 65 74 69 6d  65 73 20 6f 6e 6c 79 20  | Sometimes only |
000001e0  6f 6e 65 20 73 6c 69 64  65 72 20 77 69 6c 6c 20  |one slider will |
000001f0  73 68 6f 77 2c 20 61 6e  64 20 73 6f 6d 65 74 69  |show, and someti|
00000200

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 20180830_2348 ===================
boot-repair version : 4ppa62
boot-sav version : 4ppa62
boot-sav-extra version : 4ppa62
glade2script version : 3.2.3~ppa4
Error: /dev/sda: unrecognised disk label
Error: /dev/sdb: unrecognised disk label
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: Invalid partition table - recursive partition on /dev/sr0.
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 1oct2017, zesty, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:


=================== blkid:
/dev/sr0: UUID="2017-10-29-00-56-18-00" LABEL="Boot-Repair-Disk 64bit" TYPE="iso9660" PTUUID="6b8b4567" PTTYPE="dos"
/dev/loop0: TYPE="squashfs"
/dev/zram0: UUID="d4837fe5-a265-4be3-bcb4-a1370b9cdbe0" TYPE="swap"


=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:



=================== parted -lm:

BYT;
/dev/sda:143GB:scsi:512:512:unknown:QEMU QEMU HARDDISK:;

BYT;
/dev/sdb:34.4GB:scsi:512:512:unknown:QEMU QEMU HARDDISK:;

BYT;
/dev/sr0:742MB:scsi:2048:2048:unknown:QEMU QEMU DVD-ROM:;

BYT;
/dev/zram0:4184MB:unknown:4096:4096:loop:Unknown:;
1:0.00B:4184MB:4184MB:linux-swap(v1)::;

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL
loop0 loop squashfs 629.3M
sda   disk            133G
sdb   disk             32G
sr0   rom  iso9660    708M Boot-Repair-Disk 64bit
zram0 disk            3.9G

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
sda      1  0  0 running
sdb      1  0  0 running
sr0      1  0  1 running /cdrom
zram0    0  0  0         [SWAP]


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4058700k,nr_inodes=1014675,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=817180k,mode=755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime,nojoliet,check=s,map=n,blocksize=2048)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=31,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=11898)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=817176k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu_dma_latency cuse disk dvd ecryptfs fd full fuse hidraw0 hpet hugepages hwrng i2c-0 initctl input kmsg lightnvm log mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sdb serial sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom userio v4l vfio vga_arbiter vhci vhost-net vhost-vsock video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     799M  9.0M  790M   2% /run
/dev/sr0       iso9660   708M  708M     0 100% /cdrom
/dev/loop0     squashfs  630M  630M     0 100% /rofs
/cow           overlay   3.9G  4.0M  3.9G   1% /
tmpfs          tmpfs     3.9G     0  3.9G   0% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     3.9G  4.0K  3.9G   1% /tmp
tmpfs          tmpfs     799M  4.0K  799M   1% /run/user/999

=================== fdisk -l:
Disk /dev/loop0: 629.3 MiB, 659873792 bytes, 1288816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 133 GiB, 142807662592 bytes, 278921216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdb: 32 GiB, 34359738368 bytes, 67108864 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/zram0: 3.9 GiB, 4183945216 bytes, 1021471 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Error: no partitions

** (zenity:5596): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.

```

---

### Post by TheFu on 2018-08-31
Check the storage for problems on the host.
How did you restore from a backup?  Was it at the whole disk level?

---

### Post by wlraider70 on 2018-08-31
it was only a snapshot... All I had. The host FS checks out; it is booting and running properly.

---

### Post by TheFu on 2018-08-31
LVM snapshot?

---

