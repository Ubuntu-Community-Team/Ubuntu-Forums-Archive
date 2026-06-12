---
title: "Win 10 Missing from GRUB Menu"
date: 2017-07-23
forum: Installation &amp; Upgrades
---

### Post by gontran2 on 2017-07-23
Home-built Desktop (1st in a decade), attempted dual boot Win 10 and Mint 18.2. Currently shows boot menu, but missing Win 10. I'll try to be brief, while providing details.

**Desktop:** Ryzen 5 1600, MSI B350 Tomahawk mobo, 16GB ram, **M.2 NVME 256GB SSD**, 2TB HDD, generic optical drive.

I built the desktop and successfully installed Win 10 on M.2 SSD. After reading several articles, I turned off fast start, (secure boot appears to be disabled by default on MSI mobos), and my copy of Win 10 **does not show UEFI settings** in advanced power up options.
I shrank the SSD by 100GB, booted with Mint 18.2 DVD and proceeded with manual install on unallocated space. I set 4GB swap, 32GB /root, and the remainder of the 100GB /home, all logical partitions. I made the mistake of setting boot loader device as the one with the Win 10 boot loader. The install went on until i got an error that **boot loader creation had failed**. My options were: Select a new device, Continue without a boot loader, or Cancel installation. Unfortunately the window froze, and there was no response with any option selected, so I powered off and re-booted.

Windows 10 started and ran just fine, with no sign of a boot menu or Linux. So I removed the partition and re-shrank the SSD , and again manually re-installed Linux as before, ("Install Linux Alongside Windows 10" did not list SSD, only HDD) but I left the default location for boot loader. Upon re-boot, Linux comes up, with no GRUB or Windows option.

I ran boot repair (text file below) and **now I have a GRUB menu at start up, but no Windows option. **It is effectively a Linux only system.

I'm not above a complete wipe of the SSD, (disconnect HDD), reinstall Windows and Linux with default auto settings (letting Linux create its own partitions)?
I looked at running gparted as recommended by boot repair, but i'm not an experienced user, and the referenced article mentioned Win 7,8, not Win 10.

Suggestions?

BOOT REPAIR TEXT FOLLOWS:

```
Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================


============================ Drive/Partition Info: =============================

no valid partition table found
"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/nvme0n1                                                       
/dev/nvme0n1p1   12EC6F44EC6F20E9                       ntfs       
/dev/nvme0n1p5   9e9086f4-289a-4cbc-9e66-3059bdde6fc5   swap       
/dev/nvme0n1p6   f29ed565-307a-4504-9c2e-20ef08aaf97a   ext4       
/dev/nvme0n1p7   2d2e6311-fa74-42aa-a715-c19e5e7c7ae5   ext4       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Jul 23 17:41 ata-ATAPI_iHAS124_F_3524728_2F8624510694 -> ../../sr0
lrwxrwxrwx 1 root root 13 Jul 23 17:48 nvme-WDC_WDS256G1X0C-00ENX0_172438432264 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Jul 23 17:48 nvme-WDC_WDS256G1X0C-00ENX0_172438432264-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Jul 23 17:48 nvme-WDC_WDS256G1X0C-00ENX0_172438432264-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Jul 23 17:48 nvme-WDC_WDS256G1X0C-00ENX0_172438432264-part5 -> ../../nvme0n1p5
lrwxrwxrwx 1 root root 15 Jul 23 17:48 nvme-WDC_WDS256G1X0C-00ENX0_172438432264-part6 -> ../../nvme0n1p6
lrwxrwxrwx 1 root root 15 Jul 23 17:48 nvme-WDC_WDS256G1X0C-00ENX0_172438432264-part7 -> ../../nvme0n1p7
lrwxrwxrwx 1 root root 13 Jul 23 17:48 nvme-eui.1724384322640001001b444a4449c9b5 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Jul 23 17:48 nvme-eui.1724384322640001001b444a4449c9b5-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Jul 23 17:48 nvme-eui.1724384322640001001b444a4449c9b5-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Jul 23 17:48 nvme-eui.1724384322640001001b444a4449c9b5-part5 -> ../../nvme0n1p5
lrwxrwxrwx 1 root root 15 Jul 23 17:48 nvme-eui.1724384322640001001b444a4449c9b5-part6 -> ../../nvme0n1p6
lrwxrwxrwx 1 root root 15 Jul 23 17:48 nvme-eui.1724384322640001001b444a4449c9b5-part7 -> ../../nvme0n1p7

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/nvme0n1p6   /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/nvme0n1p7   /home                    ext4       (rw,relatime,data=ordered)


=============================== StdErr Messages: ===============================

File descriptor 9 (/proc/4545/mounts) leaked on lvs invocation. Parent PID 15621: bash
File descriptor 63 (pipe:[46856]) leaked on lvs invocation. Parent PID 15621: bash

ADDITIONAL INFORMATION :
=================== log of boot-repair 2017-07-23__17h48 ===================
boot-repair version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version :
File descriptor 9 (/proc/4545/mounts) leaked on lvs invocation. Parent PID 6376: /bin/sh
boot-repair is executed in installed-session (Linux Mint 18.2 Sonya, sonya, LinuxMint, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.8.0-53-generic root=UUID=f29ed565-307a-4504-9c2e-20ef08aaf97a ro quiet splash vt.handoff=7
nvme0n1 (nvme0n1) has unknown type. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
nvme0n1 (nvme0n1) has unknown type. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Windows is hibernated, refused to mount.
Failed to mount '/dev/nvme0n1p1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/nvme0n1p1 /mnt/boot-sav/nvme0n1p1
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount /dev/nvme0n1 : Error code 32
mount -r /dev/nvme0n1 /mnt/boot-sav/nvme0n1
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount -r /dev/nvme0n1 : Error code 32

=================== os-prober:
/dev/nvme0n1p6:The OS now in use - Linux Mint 18.2 Sonya CurrentSession:linux

=================== blkid:
/dev/nvme0n1p1: UUID="12EC6F44EC6F20E9" TYPE="ntfs" PARTUUID="ba7107e1-01"
/dev/nvme0n1p5: UUID="9e9086f4-289a-4cbc-9e66-3059bdde6fc5" TYPE="swap" PARTUUID="ba7107e1-05"
/dev/nvme0n1p6: UUID="f29ed565-307a-4504-9c2e-20ef08aaf97a" TYPE="ext4" PARTUUID="ba7107e1-06"
/dev/nvme0n1p7: UUID="2d2e6311-fa74-42aa-a715-c19e5e7c7ae5" TYPE="ext4" PARTUUID="ba7107e1-07"
/dev/nvme0n1: PTUUID="ba7107e1" PTTYPE="dos"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount /dev/nvme0n1 : Error code 32
mount -r /dev/nvme0n1 /mnt/boot-sav/nvme0n1
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount -r /dev/nvme0n1 : Error code 32
Windows not detected by os-prober on nvme0n1p1.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Jun 28 11:31 grub.d
total 96
-rwxr-xr-x 1 root root  9791 May 11 06:32 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root  1180 Oct 25  2014 06_mint_theme
-rwxr-xr-x 1 root root 12552 May 11 06:32 10_linux
-rwxr-xr-x 1 root root 10634 Oct  1  2012 10_lupin
-rwxr-xr-x 1 root root 11082 May 11 06:32 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 11 06:32 30_os-prober
-rwxr-xr-x 1 root root  1418 May 11 06:32 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 11 06:32 40_custom
-rwxr-xr-x 1 root root   216 May 11 06:32 41_custom
-rw-r--r-- 1 root root   483 May 11 06:32 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== UEFI/Legacy mode:
This installed-session is not in EFI-mode.
EFI in dmesg.
[    0.000000] ACPI: UEFI 0x00000000DD577D98 000042 (v01                 00000000      00000000)
SecureBoot disabled.


=================== PARTITIONS & DISKS:
nvme0n1p6    : nvme0n1,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
nvme0n1p1    : nvme0n1,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/nvme0n1p1.
nvme0n1p7    : nvme0n1,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /home.
nvme0n1    : nvme0n1,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/nvme0n1.

nvme0n1    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: Unknown (unknown)
Disk /dev/nvme0n1: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type      File system     Flags
1      1049kB  149GB  149GB   primary   ntfs
2      149GB   256GB  107GB   extended
5      149GB   153GB  4095MB  logical   linux-swap(v1)
6      153GB   186GB  32.8GB  logical   ext4
7      186GB   256GB  70.5GB  logical   ext4

=================== parted -lm:

BYT;
/dev/nvme0n1:256GB:unknown:512:512:msdos:Unknown:;
1:1049kB:149GB:149GB:ntfs::;
2:149GB:256GB:107GB:::;
5:149GB:153GB:4095MB:linux-swap(v1)::;
6:153GB:186GB:32.8GB:ext4::;
7:186GB:256GB:70.5GB:ext4::;

=================== lsblk:
KNAME     TYPE FSTYPE   SIZE LABEL
sr0       rom          1024M
nvme0n1   disk        238.5G
nvme0n1p5 part swap     3.8G
nvme0n1p1 part ntfs   138.5G
nvme0n1p6 part ext4    30.5G
nvme0n1p2 part            1K
nvme0n1p7 part ext4    65.7G

KNAME     ROTA RO RM STATE   MOUNTPOINT
sr0          1  0  1 running
nvme0n1      0  0  0
nvme0n1p5    0  0  0         [SWAP]
nvme0n1p1    0  0  0         /mnt/boot-sav/nvme0n1p1
nvme0n1p6    0  0  0         /
nvme0n1p2    0  0  0
nvme0n1p7    0  0  0         /home


=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8168540k,nr_inodes=2042135,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1644824k,mode=755)
/dev/nvme0n1p6 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (rw,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb,release_agent=/run/cgmanager/agents/cgm-release-agent.hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids,release_agent=/run/cgmanager/agents/cgm-release-agent.pids)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event,release_agent=/run/cgmanager/agents/cgm-release-agent.perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset,clone_children)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=18178)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/nvme0n1p7 on /home type ext4 (rw,relatime,data=ordered)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
cgmfs on /run/cgmanager/fs type tmpfs (rw,relatime,size=100k,mode=755)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1644824k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/nvme0n1p1 on /mnt/boot-sav/nvme0n1p1 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


=================== ls:
/sys/block/nvme0n1 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment eui ext_range holders inflight integrity mq nsid nvme0n1p1 nvme0n1p2 nvme0n1p5 nvme0n1p6 nvme0n1p7 power queue range removable ro size slaves stat subsystem trace uevent uuid wwid
/sys/block/sr0 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 dvd dvdrw ecryptfs fb0 fd full fuse gpiochip0 gpiochip1 hidraw0 hidraw1 hidraw2 hpet hugepages hwrng i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-15 i2c-16 i2c-17 i2c-18 i2c-19 i2c-2 i2c-20 i2c-21 i2c-22 i2c-23 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 initctl input kmsg lightnvm log lp0 mapper mcelog mem memory_bandwidth mqueue net network_latency network_throughput null nvme0 nvme0n1 nvme0n1p1 nvme0n1p2 nvme0n1p5 nvme0n1p6 nvme0n1p7 parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sg0 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb userio vfio vga_arbiter vhci vhost-net zero
ls /dev/mapper:  control
ls: cannot access '': No such file or directory

=================== hexdump -n512 -C /dev/nvme0n1p1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 17 4f 11 00 00 00 00  |..........O.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  e9 20 6f ec 44 6f ec 12  |......... o.Do..|
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

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.8G     0  7.8G   0% /dev
tmpfs          tmpfs     1.6G  9.4M  1.6G   1% /run
/dev/nvme0n1p6 ext4       30G  4.9G   24G  18% /
tmpfs          tmpfs     7.9G   38M  7.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/nvme0n1p7 ext4       65G   78M   62G   1% /home
cgmfs          tmpfs     100K     0  100K   0% /run/cgmanager/fs
tmpfs          tmpfs     1.6G   24K  1.6G   1% /run/user/1000
/dev/nvme0n1p1 fuseblk   139G   20G  119G  15% /mnt/boot-sav/nvme0n1p1

=================== fdisk -l:
Disk /dev/nvme0n1: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xba7107e1

Device         Boot     Start       End   Sectors   Size Id Type
/dev/nvme0n1p1           2048 290398207 290396160 138.5G  7 HPFS/NTFS/exFAT
/dev/nvme0n1p2      290400254 500117503 209717250   100G  5 Extended
/dev/nvme0n1p5      290400256 298397695   7997440   3.8G 82 Linux swap / Solaris
/dev/nvme0n1p6      298399744 362397695  63997952  30.5G 83 Linux
/dev/nvme0n1p7      362399744 500117503 137717760  65.7G 83 Linux



=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub2 of nvme0n1p6 into the MBR of nvme0n1.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 1
WinSE in nvme0n1p1
/mnt/boot-sav/nvme0n1p1/ may need repair.
/mnt/boot-sav/nvme0n1p1/bootmgr may need repair.
Unhide GRUB boot menu in nvme0n1p6/etc/default/grub

*******lspci -nnk | grep -iA3 vga
23:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM206 [GeForce GTX 950] [10de:1402] (rev a1)
Subsystem: eVga.com. Corp. GM206 [GeForce GTX 950] [3842:2951]
Kernel driver in use: nouveau
Kernel modules: nvidiafb, nouveau
23:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fba] (rev a1)
Subsystem: eVga.com. Corp. Device [3842:2951]
Kernel driver in use: snd_hda_intel
Kernel modules: snd_hda_intel
24:00.0 Non-Essential Instrumentation [1300]: Advanced Micro Devices, Inc. [AMD] Device [1022:145a]
*******

grub-install --version
grub-install.real (GRUB) 2.02~beta2-36ubuntu3.9+linuxmint1,grub-install.

Reinstall the GRUB of nvme0n1p6 into the MBR of nvme0n1
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/nvme0n1: exit code of grub-install /dev/nvme0n1:0

update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.8.0-53-generic
Found initrd image: /boot/initrd.img-4.8.0-53-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
File descriptor 9 (/proc/4545/mounts) leaked on lvs invocation. Parent PID 12364: /bin/sh
File descriptor 63 (pipe:[46856]) leaked on lvs invocation. Parent PID 12364: /bin/sh
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount /dev/nvme0n1 : Error code 32
mount -r /dev/nvme0n1 /mnt/boot-sav/nvme0n1
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount -r /dev/nvme0n1 : Error code 32
Unhide GRUB boot menu in nvme0n1p6/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.


The boot files of [The OS now in use - Linux Mint 18.2 Sonya] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
pastebinit  packages needed
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
dpkg-preconfigure: unable to re-open stdin: No such file or directory
W: --force-yes is deprecated, use one of the options starting with --allow instead.
```

---

### Post by oldfred on 2017-07-23
Please use code tags with long text or teminal output.
Easy to do with Forum advanced editor and # icon.

Moved to Mint sub-forum since not offical Ubuntu flavor.

You have installed Windows in the 35 year old BIOS/MBR configuration, not the newer UEFI/gpt configuration.
Windows and Ubuntu (I assume Mint) install in the same mode as you boot install media. Or if you boot flash drive in UEFI mode, then you install in UEFI mode.
If in BIOS boot mode, Secure boot must be off. UEFI can have it either on or off. Many systems just call UEFI Secure Boot the "Windows" mode, and Secure boot off is then "Other". 

If you just installed, I would suggest reinstalling Windows is UEFI boot mode. But if you want to keep the old BIOS/MBR configuration, you then must install Mint in BIOS mode. If Mint on second drive, you can still use gpt and even include an ESP - efi system partition. But for BIOS boot you need a bios_grub partition. If UEFI, Ubuntu grub only installs to the ESP on sda, and since sda/NVMe drive is BIOS it does not have an ESP.
And Windows will not boot in UEFI mode from MBR(msdos) drive. Ubuntu could, but not a normal configuration. 
Windows will not boot in BIOS mode from a gpt partitioned drive, but Ubuntu can without issue.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help) 
            UEFI/BIOS gpt/MBR explanation - see post by Rod Smith
[http://askubuntu.com/questions/500359/efi-boot-partition-and-biosgrub-partition](http://askubuntu.com/questions/500359/efi-boot-partition-and-biosgrub-partition)

---

