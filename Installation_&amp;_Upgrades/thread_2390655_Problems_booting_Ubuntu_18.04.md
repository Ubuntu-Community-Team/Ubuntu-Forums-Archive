---
title: "Problems booting Ubuntu 18.04"
date: 2018-05-01
forum: Installation &amp; Upgrades
---

### Post by kingsleadhat on 2018-05-01
So, I was all happy getting back to Ubuntu after I experienced problems with my Windows 10 (problems I wish to resolve as soon as I go back to my country).
I installed successfully the latest version only 2 days ago, until, while running regularly today, it froze and I could do nothing but force-restarting my device.
However, the system wouldn't restart it in any way. After plugging the installation USB, I could only get to the "Trial" version, disk checking or installing it anew.
I went for the trial once again, after making sure that the disk check option wouldn;t show any error.
Here I followed the steps in a terminal for boot repair.
The operation run smoothly, but at the end I couldn't get a repair button, like this one I've found in the forum.

[https://ibb.co/fqf9m7](https://ibb.co/fqf9m7)

Basically, I only get the button to create a BootInfo summary. 
When re-starting, I get back to the same point. No OS running, if not by USB installation drive, which gives me the same options as before.

I paste the result of the BootRepair I run:

```
 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 14.5 GiB, 15512174592 bytes, 30297216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    30,296,063    30,294,016   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/sda1        0E6C-5FE0                              vfat       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 May  1 06:42 ata-HL-DT-ST_DVDRAM_GUE1N_KWLFBDN0849 -> ../../sr0
lrwxrwxrwx 1 root root  9 May  1 06:50 usb-_USB_Flash_Memory_CC52AF4C82ABCDA18D874BEF-0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 May  1 06:50 usb-_USB_Flash_Memory_CC52AF4C82ABCDA18D874BEF-0:0-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 May  1 06:42 wwn-0x5001480000000000 -> ../../sr0

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

set timeout=5
menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash ---
	initrd	/casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash oem-config/enable=true ---
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash ---
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/14947/mountinfo) leaked on lvs invocation. Parent PID 19877: bash
File descriptor 63 (pipe:[73396]) leaked on lvs invocation. Parent PID 19877: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 20180501_0650 ===================
boot-repair version : 4ppa65
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4
boot-repair is executed in live-session (Ubuntu 18.04 LTS, bionic, Ubuntu, x86_64)
CPU op-mode(s):      32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
ls: cannot access '/home/usr/.config': No such file or directory

=================== os-prober:


=================== blkid:
/dev/sda1: UUID="0E6C-5FE0" TYPE="vfat"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"


=================== efibootmgr -v
BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001
Boot0001* UEFI:  USB Flash Memory1.00	PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x0,0x800,0x1ce4000)..BO

=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.


=================== PARTITIONS & DISKS:



=================== parted -lm:

BYT;
/dev/sda:15.5GB:scsi:512:512:msdos: USB Flash Memory:;
1:1049kB:15.5GB:15.5GB:fat32::boot, lba;

=================== lsblk:
KNAME TYPE FSTYPE    SIZE LABEL
loop0 loop squashfs  1.7G
loop1 loop squashfs 86.6M
loop2 loop squashfs  140M
loop3 loop squashfs  1.6M
loop4 loop squashfs 12.2M
loop5 loop squashfs   21M
loop6 loop squashfs  3.3M
sda   disk          14.5G
sda1  part vfat     14.5G
sr0   rom           1024M

KNAME ROTA RO RM STATE   MOUNTPOINT
loop0    1  1  0         /rofs
loop1    1  1  0         /snap/core/4486
loop2    1  1  0         /snap/gnome-3-26-1604/59
loop3    1  1  0         /snap/gnome-calculator/154
loop4    1  1  0         /snap/gnome-characters/69
loop5    1  1  0         /snap/gnome-logs/25
loop6    1  1  0         /snap/gnome-system-monitor/36
sda      1  0  1 running
sda1     1  0  1         /cdrom
sr0      1  0  1 running


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=1951884k,nr_inodes=487971,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=394616k,mode=755)
/dev/sda1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
/cow on / type overlay (rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow/upper,workdir=/cow/work)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=13976)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=394612k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/var/lib/snapd/snaps/core_4486.snap on /snap/core/4486 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_59.snap on /snap/gnome-3-26-1604/59 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_154.snap on /snap/gnome-calculator/154 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_69.snap on /snap/gnome-characters/69 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_25.snap on /snap/gnome-logs/25 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_36.snap on /snap/gnome-system-monitor/36 type squashfs (ro,nodev,relatime,x-gdu.hide)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  acpi_thermal_rel autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 dvd dvdrw ecryptfs fb0 fd full fuse hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-15 i2c-16 i2c-17 i2c-18 i2c-19 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout tpm0 tpmrm0 uhid uinput urandom userio v4l vfio vga_arbiter vhci vhost-net vhost-vsock video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs          tmpfs     386M  1.7M  384M   1% /run
/dev/sda1      vfat       15G  3.6G   11G  25% /cdrom
/dev/loop0     squashfs  1.8G  1.8G     0 100% /rofs
/cow           overlay   1.9G  352M  1.6G  19% /
tmpfs          tmpfs     1.9G   26M  1.9G   2% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     1.9G   40K  1.9G   1% /tmp
tmpfs          tmpfs     386M   48K  386M   1% /run/user/999
/dev/loop1     squashfs   87M   87M     0 100% /snap/core/4486
/dev/loop2     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop3     squashfs  1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop4     squashfs   13M   13M     0 100% /snap/gnome-characters/69
/dev/loop5     squashfs   21M   21M     0 100% /snap/gnome-logs/25
/dev/loop6     squashfs  3.4M  3.4M     0 100% /snap/gnome-system-monitor/36

=================== fdisk -l:
Disk /dev/loop0: 1.7 GiB, 1831378944 bytes, 3576912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.6 MiB, 90759168 bytes, 177264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 140 MiB, 146841600 bytes, 286800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 1.6 MiB, 1691648 bytes, 3304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 12.2 MiB, 12804096 bytes, 25008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 21 MiB, 22003712 bytes, 42976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 3.3 MiB, 3411968 bytes, 6664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 14.5 GiB, 15512174592 bytes, 30297216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 30296063 30294016 14.5G  c W95 FAT32 (LBA)


Error: no partitions
Gtk-Message: 06:50:58.807: GtkDialog mapped without a transient parent. This is discouraged.


=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by viaciofano on 2018-05-01
I believe there is a bug when reinstalling over a previous version. Did you change the start up to encryption? I found an issue with the start up and went back to install an earlier version. This worked for me.

---

