---
title: "Cant access or mount drive please help"
date: 2018-07-24
forum: Installation &amp; Upgrades
---

### Post by usman22 on 2018-07-24
PLease help

i have recently tried to make the move from windows to ubuntu, i am very new to it.

i made a partition for ubuntu sepretly from windows 

downloaded ubuntu and booted it of usb drive, when i came to install i must of messed my windows partition up and now am unable to install ubuntu as it is asking me to format the drive to do so 

and cant go back to windows am not too sure if i messed up the file system maybe,

now its telling me that my drive is allocated, am not too sure of what to do please help, ive tried everything to mount it and be able to access it but with no use

is my data lost?

---

### Post by ajgreeny on 2018-07-24
It looks as if you have in some way removed the Windows partition as there are no NTFS partitions showing and all you appear to have is a large amount of unallocated space.

Do not try to do anything else with the disk at the moment but wait for someone who knows more than I do to come along and help you out. 

I believe GPT partition tables are more easily restored than the old ms-dos ones, but unfortunately, I can not help personally with this so just hang fire for now until that person appears here to help.

---

### Post by usman22 on 2018-07-24
thanks much appreciated

---

### Post by yancek on 2018-07-25
The images you posted show one partiton on the SSD which has a FAT32 filesystem.  That is a windows filesystem which hasn't been used on windows systems for over 20 years (W98).  Not sure how that happened.  

Which windows did you have installed?
Was it left hibernated before you began the install of Ubuntu?
Which installation type option did you select from Ubuntu?  Should have used the Something Else option.
Since you can still boot the usb with the Ubuntu installer on it, do that and go to the site below and download and run boot repair according to the instructions on that page.  Use the 2nd option to download the ppa version and select the Create BootInfo Summary option and do NOT try to make any repairs.  When it finishes, it will show you a link which you can post here and hopefully get some help.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you had windows 8 or 10 installed, it would be a good idea to read the Ubuntu documentation at the site below before trying to install again.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by usman22 on 2018-07-25
first of all thanks for the direction 

i had windows 10 (64) installed 
I restarted from windows last and booted into USB 
i used the something else option then made a mess in the partition to install section..
am not too sure i think i did something through grub and changed the system file to fat 32 

i've followed your instructions and downloaded bootrepair

here is the bootinfo file


```
 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]



============================= Boot Info Summary: ===============================


 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sda.


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 32792 of /dev/sda1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys


ubuntu-vg-root: ________________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/LVM/ubuntu-vg-root: unknown filesystem type ''.


ubuntu-vg-swap_1: ______________________________________________________________


    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/LVM/ubuntu-vg-root: unknown filesystem type ''.
mount: /mnt/BootInfo/LVM/ubuntu-vg-swap_1: unknown filesystem type ''.


============================ Drive/Partition Info: =============================


Drive: sda _____________________________________________________________________
Disk /dev/sda: 7.5 GiB, 8010194944 bytes, 15644912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos


Partition  Boot  Start Sector    End Sector  # of Sectors  Id System


/dev/sda1    *          2,048    15,644,911    15,642,864   c W95 FAT32 (LBA)




"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/nvme0n1                                                       
/dev/nvme0n1p1   909F-F258                              vfat       VFAT
/dev/sda1        0653-E545                              vfat       UBUNTU 18_0


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root 13 Jul 25 16:08 nvme-INTEL_SSDPEKKW512G7_BTPY65050PRT512F -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Jul 25 16:08 nvme-INTEL_SSDPEKKW512G7_BTPY65050PRT512F-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 13 Jul 25 16:08 nvme-eui.0000000001000000e4d25c27d2934d01 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Jul 25 16:08 nvme-eui.0000000001000000e4d25c27d2934d01-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root  9 Jul 25 16:08 usb-Kingston_DataTraveler_G3_001CC07CEDA4FB91992923D3-0:0 -> ../../sda
lrwxrwxrwx 1 root root 10 Jul 25 16:08 usb-Kingston_DataTraveler_G3_001CC07CEDA4FB91992923D3-0:0-part1 -> ../../sda1


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


============================== sda1/syslinux.cfg: ==============================


--------------------------------------------------------------------------------
DEFAULT loadconfig


LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/
--------------------------------------------------------------------------------


=================== sda1: Location of files loaded by Grub: ====================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             boot/grub/grub.cfg                             1


================= sda1: Location of files loaded by Syslinux: ==================


           GiB - GB             File                                 Fragment(s)


            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1


=============================== StdErr Messages: ===============================


File descriptor 9 (/proc/31957/mountinfo) leaked on lvs invocation. Parent PID 5490: bash
File descriptor 63 (pipe:[150239]) leaked on lvs invocation. Parent PID 5490: bash
File descriptor 9 (/proc/31957/mountinfo) leaked on lvchange invocation. Parent PID 5723: bash
File descriptor 63 (pipe:[150239]) leaked on lvchange invocation. Parent PID 5723: bash
File descriptor 9 (/proc/31957/mountinfo) leaked on lvchange invocation. Parent PID 5723: bash
File descriptor 63 (pipe:[150239]) leaked on lvchange invocation. Parent PID 5723: bash
File descriptor 9 (/proc/31957/mountinfo) leaked on lvchange invocation. Parent PID 5723: bash
File descriptor 63 (pipe:[150239]) leaked on lvchange invocation. Parent PID 5723: bash
File descriptor 9 (/proc/31957/mountinfo) leaked on lvchange invocation. Parent PID 5723: bash
File descriptor 63 (pipe:[150239]) leaked on lvchange invocation. Parent PID 5723: bash


ADDITIONAL INFORMATION :
=================== log of boot-repair 20180725_1608 ===================
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
/dev/nvme0n1p1: LABEL="VFAT" UUID="909F-F258" TYPE="vfat" PARTUUID="5c5f7b4b-01"
/dev/sda1: LABEL="UBUNTU 18_0" UUID="0653-E545" TYPE="vfat" PARTUUID="28ab763a-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/nvme0n1: PTUUID="5c5f7b4b" PTTYPE="dos"


Presence of EFI/Microsoft file detected: /mnt/boot-sav/nvme0n1p1/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /mnt/boot-sav/nvme0n1p1/EFI/Boot/bootx64.efi


=================== efibootmgr -v
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,2001,2002,2003
Boot0000* Linux	HD(1,MBR,0x28ab763a,0x800,0xeeb0f0)/File(EFIBootgrubx64.efi)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC


=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.




=================== PARTITIONS & DISKS:
nvme0n1p1	: nvme0n1,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/nvme0n1p1.


nvme0n1	: not-GPT,	BIOSboot-not-needed,	has-correctEFI, 	not-usb,	not-mmc, no-os,	2048 sectors * 512 bytes




=================== parted -lm:


BYT;
/dev/sda:8010MB:scsi:512:512:msdos:Kingston DataTraveler G3:;
1:1049kB:8010MB:8009MB:fat32::boot, lba;


BYT;
/dev/nvme0n1:512GB:nvme:512:512:msdos:NVMe Device:;
1:1049kB:512GB:512GB:fat32::boot;


=================== lsblk:
KNAME     TYPE FSTYPE    SIZE LABEL
loop0     loop squashfs  1.7G
loop1     loop squashfs 86.6M
loop2     loop squashfs  140M
loop3     loop squashfs  1.6M
loop4     loop squashfs 12.2M
loop5     loop squashfs   21M
loop6     loop squashfs  3.3M
sda       disk           7.5G
sda1      part vfat      7.5G UBUNTU 18_0
nvme0n1   disk           477G
nvme0n1p1 part vfat      477G VFAT


KNAME     ROTA RO RM STATE   MOUNTPOINT
loop0        1  1  0         /rofs
loop1        1  1  0         /snap/core/4486
loop2        1  1  0         /snap/gnome-3-26-1604/59
loop3        1  1  0         /snap/gnome-calculator/154
loop4        1  1  0         /snap/gnome-characters/69
loop5        1  1  0         /snap/gnome-logs/25
loop6        1  1  0         /snap/gnome-system-monitor/36
sda          1  0  1 running
sda1         1  0  1         /cdrom
nvme0n1      0  0  0 live
nvme0n1p1    0  0  0         /mnt/boot-sav/nvme0n1p1




=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=3995204k,nr_inodes=998801,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=803280k,mode=755)
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
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=24,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=15847)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
mqueue on /dev/mqueue type mqueue (rw,relatime)
tracefs on /sys/kernel/debug/tracing type tracefs (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev,relatime)
tmpfs on /run/user/999 type tmpfs (rw,nosuid,nodev,relatime,size=803276k,mode=700,uid=999,gid=999)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=999,group_id=999)
/var/lib/snapd/snaps/core_4486.snap on /snap/core/4486 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-26-1604_59.snap on /snap/gnome-3-26-1604/59 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_154.snap on /snap/gnome-calculator/154 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_69.snap on /snap/gnome-characters/69 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_25.snap on /snap/gnome-logs/25 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-system-monitor_36.snap on /snap/gnome-system-monitor/36 type squashfs (ro,nodev,relatime,x-gdu.hide)
/dev/nvme0n1p1 on /mnt/boot-sav/nvme0n1p1 type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)




=================== ls:
/sys/block/nvme0n1 (filtered):  alignment_offset bdi capability dev device discard_alignment ext_range hidden holders inflight integrity mq nguid nsid nvme0n1p1 power queue range removable ro size slaves stat subsystem trace uevent uuid wwid
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range hidden holders inflight integrity power queue range removable ro sda1 size slaves stat subsystem trace uevent
/dev (filtered):  acpi_thermal_rel autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 ecryptfs fb0 fd full fuse gpiochip0 hidraw0 hidraw1 hidraw2 hidraw3 hidraw4 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null nvme0 nvme0n1 nvme0n1p1 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sg0 shm snapshot snd stderr stdin stdout tpm0 tpmrm0 uhid uinput urandom usb userio v4l vfio vga_arbiter vhci vhost-net vhost-vsock video0 zero
ls /dev/mapper:  control


=================== hexdump -n512 -C /dev/nvme0n1p1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 58 f2 9f 90 56  46 41 54 20 20 20 20 20  |..)X...VFAT     |
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


=================== df -Th:


Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs          tmpfs     785M  1.9M  783M   1% /run
/dev/sda1      vfat      7.5G  1.8G  5.7G  25% /cdrom
/dev/loop0     squashfs  1.8G  1.8G     0 100% /rofs
/cow           overlay   3.9G  3.0G  918M  77% /
tmpfs          tmpfs     3.9G  8.1M  3.9G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs          tmpfs     3.9G   52M  3.8G   2% /tmp
tmpfs          tmpfs     785M   60K  785M   1% /run/user/999
/dev/loop1     squashfs   87M   87M     0 100% /snap/core/4486
/dev/loop2     squashfs  141M  141M     0 100% /snap/gnome-3-26-1604/59
/dev/loop3     squashfs  1.7M  1.7M     0 100% /snap/gnome-calculator/154
/dev/loop4     squashfs   13M   13M     0 100% /snap/gnome-characters/69
/dev/loop5     squashfs   21M   21M     0 100% /snap/gnome-logs/25
/dev/loop6     squashfs  3.4M  3.4M     0 100% /snap/gnome-system-monitor/36
/dev/nvme0n1p1 vfat       96M   49M   48M  51% /mnt/boot-sav/nvme0n1p1


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




Disk /dev/nvme0n1: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5c5f7b4b


Device         Boot Start        End    Sectors  Size Id Type
/dev/nvme0n1p1 *     2048 1000214527 1000212480  477G  7 HPFS/NTFS/exFAT




Disk /dev/sda: 7.5 GiB, 8010194944 bytes, 15644912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x28ab763a


Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 15644911 15642864  7.5G  c W95 FAT32 (LBA)




No OS or WinEFI system




=================== Suggested repair
The default repair of the Boot-Repair utility would not act on the boot.




=================== User settings
The settings chosen by the user will not act on the boot.

```

---

### Post by yancek on 2018-07-25
I don't really see anything in boot repair that would explain the problem.  There is really no information on the SSD except one brief reference.  I haven't used SSD's so I'm not really familiar with the naming conventions and I also don't use LVM which you have.  There is mention of a Microsoft EFI file being found and some other info on EFI.   I hope you have good backups.

> now am unable to install ubuntu as it is asking me to format the drive 

What is the 'it' you are referring to, the Ubuntu installer?

---

### Post by usman22 on 2018-07-25
in the screenshot i attached is the ubuntu installer running . as i reach the partitioning stage of the installation to go further i need to format then mount the unallocated disk space to continue so i know i definitely don't want to do that and there for i cant fully install ubuntu. i was thinking maybe remove disk ,stick it into an external hd case and try access through a windows pc if i run out of options

---

### Post by yancek on 2018-07-25
> /dev/nvme0n1p1   909F-F258                              vfat       VFAT

The above shows the blkid output from boot repair which shows a partition on your SSD.  It is the only partition I see on the SSD.  It is a vfat windows partition which is/was most likely the windows EFI partition.  This seems to be confirmed by the section shown below which is also from your boot repair.  That's the windows efi boot file.

> Presence of EFI/Microsoft file detected: /mnt/boot-sav/nvme0n1p1/EFI/Microsoft/Boot/bootmgfw.efi

Just below the above is the output of efibootmgr which shows several efi entries, none for windows.  There is also information showing it is not a GPT drive which it should be with windows EFI.  Additionaly, near the bottom of boot repair it shows "Disklabel type: dos" and should be GPT.  Further on the boot repair output shows the same partition on the SSD as an ntfs fielsystem?:

> /dev/nvme0n1p1 *     2048 1000214527 1000212480  477G  7 HPFS/NTFS/exFAT

Not sure what to make of it all.  My understanding of an LVM install which is what you appear to have done is that it needs a separate boot partition and that it overwrites the disk it is installed to.  If you don't have backups and want to try to recover data, I would suggest downloading and using testdisk from the Ubuntu install usb.

---

### Post by usman22 on 2018-07-25
ok

---

### Post by usman22 on 2018-07-30
anyone out there to give me some more direction please

---

### Post by usman22 on 2018-08-21
still hanging in here

---

