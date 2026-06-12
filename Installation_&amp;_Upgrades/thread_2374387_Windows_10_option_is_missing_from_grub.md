---
title: "Windows 10 option is missing from grub"
date: 2017-10-15
forum: Installation &amp; Upgrades
---

### Post by dpanchal223 on 2017-10-15
Hi,

I just installed Ubuntu on my Lenovo T470 laptop as a dual boot partition and now my Windows 10 is missing from that option. I'd like to be able to have both when I need it. I tried using Boot-Repair but it didn't seem to work. It did create the paste bin (paste.ubuntu.com/25746461) to explain my issue. I'm not sure how to interpret it or what steps are needed. I have pasted it is below. Any help with this is most appreciated. Thanks.

```
 Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 11oct2017]




============================= Boot Info Summary: ===============================




============================ Drive/Partition Info: =============================


no valid partition table found
"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/nvme0n1                                                       
/dev/nvme0n1p1   4AF7-1D61                              vfat       SYSTEM
/dev/nvme0n1p2                                                     
/dev/nvme0n1p3                                                     
/dev/nvme0n1p4   4C5EF9F15EF9D424                       ntfs       WinRE_DRV
/dev/nvme0n1p5   aedbdf76-1bab-4441-8d64-045698427806   ext4       
/dev/nvme0n1p6   72bbcc78-ec98-4596-9274-cbc7a752b0d5   swap       


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root 13 Oct 15 08:54 nvme-SAMSUNG_MZVLW1T0HMLH-000L7_S35ANX0J506337 -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Oct 15 08:54 nvme-SAMSUNG_MZVLW1T0HMLH-000L7_S35ANX0J506337-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Oct 15 08:54 nvme-SAMSUNG_MZVLW1T0HMLH-000L7_S35ANX0J506337-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Oct 15 08:54 nvme-SAMSUNG_MZVLW1T0HMLH-000L7_S35ANX0J506337-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Oct 15 08:54 nvme-SAMSUNG_MZVLW1T0HMLH-000L7_S35ANX0J506337-part4 -> ../../nvme0n1p4
lrwxrwxrwx 1 root root 15 Oct 15 08:54 nvme-SAMSUNG_MZVLW1T0HMLH-000L7_S35ANX0J506337-part5 -> ../../nvme0n1p5
lrwxrwxrwx 1 root root 15 Oct 15 08:54 nvme-SAMSUNG_MZVLW1T0HMLH-000L7_S35ANX0J506337-part6 -> ../../nvme0n1p6
lrwxrwxrwx 1 root root 13 Oct 15 08:54 nvme-eui.002538b571bb690a -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Oct 15 08:54 nvme-eui.002538b571bb690a-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Oct 15 08:54 nvme-eui.002538b571bb690a-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Oct 15 08:54 nvme-eui.002538b571bb690a-part3 -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 15 Oct 15 08:54 nvme-eui.002538b571bb690a-part4 -> ../../nvme0n1p4
lrwxrwxrwx 1 root root 15 Oct 15 08:54 nvme-eui.002538b571bb690a-part5 -> ../../nvme0n1p5
lrwxrwxrwx 1 root root 15 Oct 15 08:54 nvme-eui.002538b571bb690a-part6 -> ../../nvme0n1p6
lrwxrwxrwx 1 root root  9 Oct 15 08:43 usb-Generic-_SD_MMC_20120501030900000-0:0 -> ../../sda


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/nvme0n1p1   /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/nvme0n1p5   /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)




========= Devices which don't seem to have a corresponding hard drive: =========


sda 




ADDITIONAL INFORMATION :
=================== log of boot-repair 20171015_0854 ===================
boot-repair version : 4ppa59
boot-sav version : 4ppa59
boot-sav-extra version : 4ppa59
glade2script version : 3.2.3~ppa4
Warning: failed to translate partition name
boot-repair is executed in installed-session (Ubuntu 16.04.3 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.10.0-37-generic.efi.signed root=UUID=aedbdf76-1bab-4441-8d64-045698427806 ro quiet splash vt.handoff=7
nvme0n1 (nvme0n1) has unknown type. Please report this message to [email]boot.repair@gmail.com[/email]
nvme0n1 (nvme0n1) has unknown type. Please report this message to [email]boot.repair@gmail.com[/email]
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount /dev/nvme0n1 : Error code 32
mount -r /dev/nvme0n1 /mnt/boot-sav/nvme0n1
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount -r /dev/nvme0n1 : Error code 32
NTFS signature is missing.
Failed to mount '/dev/nvme0n1p3': Invalid argument
The device '/dev/nvme0n1p3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/nvme0n1p3 : Error code 12
mount -r /dev/nvme0n1p3 /mnt/boot-sav/nvme0n1p3
NTFS signature is missing.
Failed to mount '/dev/nvme0n1p3': Invalid argument
The device '/dev/nvme0n1p3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/nvme0n1p3 : Error code 12


=================== os-prober:
/dev/nvme0n1p5:The OS now in use - Ubuntu 16.04.3 LTS CurrentSession:linux
/dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi


=================== blkid:
/dev/nvme0n1p1: LABEL="SYSTEM" UUID="4AF7-1D61" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="73fc0ba1-df96-418d-921b-815fe211522e"
/dev/nvme0n1p4: LABEL="WinRE_DRV" UUID="4C5EF9F15EF9D424" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="3ed00ca7-d78f-4681-bae4-9f01f60344b2"
/dev/nvme0n1p5: UUID="aedbdf76-1bab-4441-8d64-045698427806" TYPE="ext4" PARTUUID="e576745e-1565-40ab-b78f-753c72b4c2b3"
/dev/nvme0n1p6: UUID="72bbcc78-ec98-4596-9274-cbc7a752b0d5" TYPE="swap" PARTUUID="00dfaec9-403e-4f29-9db9-7c4ac6b9ac1c"
/dev/nvme0n1: PTUUID="275b01a3-f11c-4db1-ba68-7b67c908f039" PTTYPE="gpt"
/dev/nvme0n1p2: PARTLABEL="Microsoft reserved partition" PARTUUID="9f1b9f8a-adab-4a4a-846e-3391aedad192"
/dev/nvme0n1p3: PARTLABEL="Basic data partition" PARTUUID="76f6153d-98d8-4c4d-b9f4-6bfa98baa1a9"




1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.


mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount /dev/nvme0n1 : Error code 32
mount -r /dev/nvme0n1 /mnt/boot-sav/nvme0n1
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount -r /dev/nvme0n1 : Error code 32
NTFS signature is missing.
Failed to mount '/dev/nvme0n1p3': Invalid argument
The device '/dev/nvme0n1p3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/nvme0n1p3 : Error code 12
mount -r /dev/nvme0n1p3 /mnt/boot-sav/nvme0n1p3
NTFS signature is missing.
Failed to mount '/dev/nvme0n1p3': Invalid argument
The device '/dev/nvme0n1p3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/nvme0n1p3 : Error code 12


=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Oct 15 02:03 grub.d
total 80
-rwxr-xr-x 1 root root  9791 Jun 20 21:11 00_header
-rwxr-xr-x 1 root root  6258 Mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root 12512 Jun 20 21:11 10_linux
-rwxr-xr-x 1 root root 11082 Jun 20 21:11 20_linux_xen
-rwxr-xr-x 1 root root  1992 Jan 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 Jun 20 21:11 30_os-prober
-rwxr-xr-x 1 root root  1418 Jun 20 21:11 30_uefi-firmware
-rwxr-xr-x 1 root root   283 Oct 15 02:03 40_custom
-rwxr-xr-x 1 root root   216 Jun 20 21:11 41_custom
-rw-r--r-- 1 root root   483 Jun 20 21:11 README




=================== /etc/grub.d/40_custom :


menuentary "Windows 10" {
set root='(hd0,2)'
chainloader +1
}








=================== /etc/default/grub :


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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






/boot/efi detected in the fstab of nvme0n1p5: UUID=4AF7-1D61   (nvme0n1p1)
Presence of EFI/Microsoft file detected: /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi


=================== efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0000,0017,0018,0019,001A,001B,001C,001D,001E,001F,0024
Boot0000* Windows Boot Manager	HD(1,GPT,73fc0ba1-df96-418d-921b-815fe211522e,0x800,0x82000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0001* ubuntu	HD(1,GPT,73fc0ba1-df96-418d-921b-815fe211522e,0x800,0x82000)/File(EFIubuntushimx64.efi)
Boot0010  Setup	FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu	FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0012  Diagnostic Splash Screen	FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013  Lenovo Diagnostics	FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0014  Startup Interrupt Menu	FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0015  Rescue and Recovery	FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0016  MEBx Hot Key	FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
Boot0017* USB CD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0018* USB FDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0019* NVMe0	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a400)
Boot001A* ATA HDD1	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot001B* ATA HDD0	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot001C* USB HDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot001D* PCI LAN	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot001E  Other CD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35406)
Boot001F  Other HDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f606)
Boot0020* IDER BOOT CDROM	PciRoot(0x0)/Pci(0x14,0x0)/USB(11,1)
Boot0021* IDER BOOT Floppy	PciRoot(0x0)/Pci(0x14,0x0)/USB(11,0)
Boot0022* ATA HDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0023* ATAPI CD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)
Boot0024* PCI LAN	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)


=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot enabled.




=================== PARTITIONS & DISKS:
nvme0n1p5	: nvme0n1,	not-sepboot,	grubenv-ok	grub2,	signed grub-efi ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-has-goodEFI,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	notbiosboot, .
nvme0n1p1	: nvme0n1,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	is-correct-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	notbiosboot, /boot/efi.
nvme0n1p4	: nvme0n1,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/nvme0n1p4.
nvme0n1	: nvme0n1,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	is-maybe-EFI,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	notbiosboot, /mnt/boot-sav/nvme0n1.
nvme0n1p3	: nvme0n1,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	notbiosboot, /mnt/boot-sav/nvme0n1p3.


nvme0n1	: GPT,	no-BIOS_boot,	has-correctEFI, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes




=================== parted -lm:


BYT;
/dev/nvme0n1:1024GB:unknown:512:512:gpt:Unknown:;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot, hidden, esp;
2:274MB:290MB:16.8MB::Microsoft reserved partition:msftres;
3:290MB:744GB:744GB::Basic data partition:msftdata;
5:744GB:1007GB:263GB:ext4::;
6:1007GB:1023GB:16.4GB:linux-swap(v1)::;
4:1023GB:1024GB:1049MB:ntfs::hidden, diag;


=================== lsblk:
KNAME     TYPE FSTYPE   SIZE LABEL
nvme0n1   disk        953.9G
nvme0n1p5 part ext4   244.9G
nvme0n1p3 part        692.5G
nvme0n1p1 part vfat     260M SYSTEM
nvme0n1p6 part swap    15.3G
nvme0n1p4 part ntfs    1000M WinRE_DRV
nvme0n1p2 part           16M


KNAME     ROTA RO RM STATE MOUNTPOINT
nvme0n1      0  0  0
nvme0n1p5    0  0  0       /
nvme0n1p3    0  0  0
nvme0n1p1    0  0  0       /boot/efi
nvme0n1p6    0  0  0       [SWAP]
nvme0n1p4    0  0  0       /mnt/boot-sav/nvme0n1p4
nvme0n1p2    0  0  0




=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=8139704k,nr_inodes=2034926,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=1632392k,mode=755)
/dev/nvme0n1p5 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=28,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=1660)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=1632392k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/nvme0n1p4 on /mnt/boot-sav/nvme0n1p4 type fuseblk (rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096)




=================== ls:
/sys/block/nvme0n1 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment eui ext_range holders inflight integrity mq nsid nvme0n1p1 nvme0n1p2 nvme0n1p3 nvme0n1p4 nvme0n1p5 nvme0n1p6 power queue range removable ro size slaves stat subsystem trace uevent wwid
/sys/block/sda (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 ecryptfs fb0 fd full fuse hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 initctl input kmsg lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null nvme0 nvme0n1 nvme0n1p1 nvme0n1p2 nvme0n1p3 nvme0n1p4 nvme0n1p5 nvme0n1p6 port ppp psaux ptmx ptp0 pts random rfkill rtc rtc0 sda sg0 shm snapshot snd stderr stdin stdout tpm0 uhid uinput urandom userio v4l vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control


=================== hexdump -n512 -C /dev/nvme0n1p1
00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 fe 1b  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 08 00 01 02 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 61 1d f7 4a 4e  4f 20 4e 41 4d 45 20 20  |..)a..JNO NAME  |
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


=================== hexdump -n512 -C /dev/nvme0n1p4
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 90 1c 77  |........?......w|
00000020  00 00 00 00 80 00 80 00  ff 3f 1f 00 00 00 00 00  |.........?......|
00000030  55 4d 01 00 00 00 00 00  02 00 00 00 00 00 00 00  |UM..............|
00000040  f6 00 00 00 01 00 00 00  24 d4 f9 5e f1 f9 5e 4c  |........$..^..^L|
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
/dev/nvme0n1p5 ext4      241G  4.7G  225G   3% /
tmpfs          tmpfs     7.8G  320K  7.8G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/nvme0n1p1 vfat      256M   33M  224M  13% /boot/efi
tmpfs          tmpfs     1.6G   52K  1.6G   1% /run/user/1000
/dev/nvme0n1p4 fuseblk  1000M  388M  613M  39% /mnt/boot-sav/nvme0n1p4


=================== fdisk -l:
Disk /dev/nvme0n1: 953.9 GiB, 1024209543168 bytes, 2000409264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 275B01A3-F11C-4DB1-BA68-7B67C908F039


Device              Start        End    Sectors   Size Type
/dev/nvme0n1p1       2048     534527     532480   260M EFI System
/dev/nvme0n1p2     534528     567295      32768    16M Microsoft reserved
/dev/nvme0n1p3     567296 1452806143 1452238848 692.5G Microsoft basic data
/dev/nvme0n1p4 1998360576 2000408575    2048000  1000M Windows recovery environment
/dev/nvme0n1p5 1452806144 1966358527  513552384 244.9G Linux filesystem
/dev/nvme0n1p6 1966358528 1998360575   32002048  15.3G Linux swap


Partition table entries are not in disk order.






=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of nvme0n1p5, using the following options:        nvme0n1p1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s    use-standard-efi-file




/boot/efi added in nvme0n1p5/fstab
nvme0n1p5/boot/efi not empty


*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:5916] (rev 02)
Subsystem: Lenovo Device [17aa:2245]
Kernel driver in use: i915
Kernel modules: i915
*******


grub-install --version
grub-install (GRUB) 2.02~beta2-36ubuntu3.12,grub-install (GRUB) 2.


efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0000,0017,0018,0019,001A,001B,001C,001D,001E,001F,0024
Boot0000* Windows Boot Manager	HD(1,GPT,73fc0ba1-df96-418d-921b-815fe211522e,0x800,0x82000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0001* ubuntu	HD(1,GPT,73fc0ba1-df96-418d-921b-815fe211522e,0x800,0x82000)/File(EFIubuntushimx64.efi)
Boot0010  Setup	FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu	FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0012  Diagnostic Splash Screen	FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013  Lenovo Diagnostics	FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0014  Startup Interrupt Menu	FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0015  Rescue and Recovery	FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0016  MEBx Hot Key	FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
Boot0017* USB CD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0018* USB FDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0019* NVMe0	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a400)
Boot001A* ATA HDD1	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot001B* ATA HDD0	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot001C* USB HDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot001D* PCI LAN	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot001E  Other CD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35406)
Boot001F  Other HDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f606)
Boot0020* IDER BOOT CDROM	PciRoot(0x0)/Pci(0x14,0x0)/USB(11,1)
Boot0021* IDER BOOT Floppy	PciRoot(0x0)/Pci(0x14,0x0)/USB(11,0)
Boot0022* ATA HDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0023* ATAPI CD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)
Boot0024* PCI LAN	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)


uname -r
Kernel: 4.10.0-37-generic


Reinstall the grub-efi-amd64-signed of nvme0n1p5
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0
ls nvme0n1p1/efi: /Microsoft/Recovery/BCD.LOG2 /Microsoft/Recovery/BCD.LOG1 /Microsoft/Recovery/BCD.LOG /Microsoft/Recovery/BCD /Microsoft/Boot/zh-TW /Microsoft/Boot/zh-CN /Microsoft/Boot/winsipolicy.p7b /Microsoft/Boot/updaterevokesipolicy.p7b /Microsoft/Boot/uk-UA /Microsoft/Boot/tr-TR /Microsoft/Boot/sv-SE /Microsoft/Boot/sr-Latn-RS /Microsoft/Boot/sl-SI /Microsoft/Boot/sk-SK /Microsoft/Boot/ru-RU /Microsoft/Boot/ro-RO /Microsoft/Boot/Resources /Microsoft/Boot/qps-ploc /Microsoft/Boot/pt-PT /Microsoft/Boot/pt-BR /Microsoft/Boot/pl-PL /Microsoft/Boot/nl-NL /Microsoft/Boot/nb-NO /Microsoft/Boot/memtest.efi /Microsoft/Boot/lv-LV /Microsoft/Boot/lt-LT /Microsoft/Boot/ko-KR /Microsoft/Boot/kdstub.dll /Microsoft/Boot/kd_0C_8086.dll /Microsoft/Boot/kd_07_1415.dll /Microsoft/Boot/kd_02_8086.dll /Microsoft/Boot/kd_02_19a2.dll /Microsoft/Boot/kd_02_1969.dll /Microsoft/Boot/kd_02_15b3.dll /Microsoft/Boot/kd_02_14e4.dll /Microsoft/Boot/kd_02_1137.dll /Microsoft/Boot/kd_02_10ec.dll /Microsoft/Boot/kd_02_10df.dll /Microsoft/Boot/ja-JP /Microsoft/Boot/it-IT /Microsoft/Boot/hu-HU /Microsoft/Boot/hr-HR /Microsoft/Boot/FveTcg_2.log /Microsoft/Boot/FveTcg_1.log /Microsoft/Boot/FveTcg_0.log /Microsoft/Boot/fr-FR /Microsoft/Boot/fr-CA /Microsoft/Boot/Fonts /Microsoft/Boot/fi-FI /Microsoft/Boot/et-EE /Microsoft/Boot/es-MX /Microsoft/Boot/es-ES /Microsoft/Boot/en-US /Microsoft/Boot/en-GB /Microsoft/Boot/el-GR /Microsoft/Boot/de-DE /Microsoft/Boot/da-DK /Microsoft/Boot/cs-CZ /Microsoft/Boot/boot.stl /Microsoft/Boot/BOOTSTAT.DAT /Microsoft/Boot/bootspaces.dll /Microsoft/Boot/bootmgr.efi /Microsoft/Boot/bootmgfw.efi /Microsoft/Boot/bg-BG /Microsoft/Boot/BCD.LOG2 /Microsoft/Boot/BCD.LOG1 /Microsoft/Boot/BCD.LOG /Microsoft/Boot/BCD /ubuntu/shimx64.efi /ubuntu/mmx64.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /ubuntu/fwupx64.efi /ubuntu/fw /Microsoft/Recovery /Microsoft/Boot /Boot/ReadMe.txt /Boot/License.txt /Boot/LenovoBT.EFI /Boot/bootx64.efi
ls nvme0n1p1: BOOT
EFI  . Please report this message to [email]boot.repair@gmail.com[/email]
df /dev/nvme0n1p1
Save and rename /boot/efi/EFI/Boot/bootx64.efi (/boot/efi/EFI/Boot/bkpbootx64.efi)
cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Boot/bootx64.efi
ls nvme0n1p1/efi: /Microsoft/Recovery/BCD.LOG2 /Microsoft/Recovery/BCD.LOG1 /Microsoft/Recovery/BCD.LOG /Microsoft/Recovery/BCD /Microsoft/Boot/zh-TW /Microsoft/Boot/zh-CN /Microsoft/Boot/winsipolicy.p7b /Microsoft/Boot/updaterevokesipolicy.p7b /Microsoft/Boot/uk-UA /Microsoft/Boot/tr-TR /Microsoft/Boot/sv-SE /Microsoft/Boot/sr-Latn-RS /Microsoft/Boot/sl-SI /Microsoft/Boot/sk-SK /Microsoft/Boot/ru-RU /Microsoft/Boot/ro-RO /Microsoft/Boot/Resources /Microsoft/Boot/qps-ploc /Microsoft/Boot/pt-PT /Microsoft/Boot/pt-BR /Microsoft/Boot/pl-PL /Microsoft/Boot/nl-NL /Microsoft/Boot/nb-NO /Microsoft/Boot/memtest.efi /Microsoft/Boot/lv-LV /Microsoft/Boot/lt-LT /Microsoft/Boot/ko-KR /Microsoft/Boot/kdstub.dll /Microsoft/Boot/kd_0C_8086.dll /Microsoft/Boot/kd_07_1415.dll /Microsoft/Boot/kd_02_8086.dll /Microsoft/Boot/kd_02_19a2.dll /Microsoft/Boot/kd_02_1969.dll /Microsoft/Boot/kd_02_15b3.dll /Microsoft/Boot/kd_02_14e4.dll /Microsoft/Boot/kd_02_1137.dll /Microsoft/Boot/kd_02_10ec.dll /Microsoft/Boot/kd_02_10df.dll /Microsoft/Boot/ja-JP /Microsoft/Boot/it-IT /Microsoft/Boot/hu-HU /Microsoft/Boot/hr-HR /Microsoft/Boot/FveTcg_2.log /Microsoft/Boot/FveTcg_1.log /Microsoft/Boot/FveTcg_0.log /Microsoft/Boot/fr-FR /Microsoft/Boot/fr-CA /Microsoft/Boot/Fonts /Microsoft/Boot/fi-FI /Microsoft/Boot/et-EE /Microsoft/Boot/es-MX /Microsoft/Boot/es-ES /Microsoft/Boot/en-US /Microsoft/Boot/en-GB /Microsoft/Boot/el-GR /Microsoft/Boot/de-DE /Microsoft/Boot/da-DK /Microsoft/Boot/cs-CZ /Microsoft/Boot/boot.stl /Microsoft/Boot/BOOTSTAT.DAT /Microsoft/Boot/bootspaces.dll /Microsoft/Boot/bootmgr.efi /Microsoft/Boot/bootmgfw.efi /Microsoft/Boot/bg-BG /Microsoft/Boot/BCD.LOG2 /Microsoft/Boot/BCD.LOG1 /Microsoft/Boot/BCD.LOG /Microsoft/Boot/BCD /ubuntu/shimx64.efi /ubuntu/mmx64.efi /ubuntu/grubx64.efi /ubuntu/grub.cfg /ubuntu/fwupx64.efi /ubuntu/fw /Microsoft/Recovery /Microsoft/Boot /Boot/ReadMe.txt /Boot/License.txt /Boot/LenovoBT.EFI /Boot/bootx64.efi /Boot/bkpbootx64.efi
ls nvme0n1p1: BOOT
EFI  . Please report this message to [email]boot.repair@gmail.com[/email]
Add /boot/efi efi entries in /etc/grub.d/25_custom
Adding custom /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
Adding custom /boot/efi/EFI/Boot/bkpbootx64.efi
nvme0n1p1/bkpbootx64.efi already added
Adding custom /boot/efi/EFI/ubuntu/fwupx64.efi
Adding custom /boot/efi/EFI/ubuntu/mmx64.efi
nvme0n1p1/bootmgfw.efi already added
Installing for x86_64-efi platform.
Installation finished. No error reported.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :0


efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001,0000,0017,0018,0019,001A,001B,001C,001D,001E,001F,0024
Boot0000* Windows Boot Manager	HD(1,GPT,73fc0ba1-df96-418d-921b-815fe211522e,0x800,0x82000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0001* ubuntu	HD(1,GPT,73fc0ba1-df96-418d-921b-815fe211522e,0x800,0x82000)/File(EFIubuntushimx64.efi)
Boot0010  Setup	FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0011  Boot Menu	FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0012  Diagnostic Splash Screen	FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0013  Lenovo Diagnostics	FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0014  Startup Interrupt Menu	FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0015  Rescue and Recovery	FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0016  MEBx Hot Key	FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
Boot0017* USB CD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0018* USB FDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0019* NVMe0	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,001c199932d94c4eae9aa0b6e98eb8a400)
Boot001A* ATA HDD1	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f601)
Boot001B* ATA HDD0	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot001C* USB HDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot001D* PCI LAN	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot001E  Other CD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35406)
Boot001F  Other HDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f606)
Boot0020* IDER BOOT CDROM	PciRoot(0x0)/Pci(0x14,0x0)/USB(11,1)
Boot0021* IDER BOOT Floppy	PciRoot(0x0)/Pci(0x14,0x0)/USB(11,0)
Boot0022* ATA HDD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0023* ATAPI CD	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)
Boot0024* PCI LAN	VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)


update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.10.0-37-generic
Found initrd image: /boot/initrd.img-4.10.0-37-generic
Found linux image: /boot/vmlinuz-4.10.0-28-generic
Found initrd image: /boot/initrd.img-4.10.0-28-generic
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount /dev/nvme0n1 : Error code 32
mount -r /dev/nvme0n1 /mnt/boot-sav/nvme0n1
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount -r /dev/nvme0n1 : Error code 32
NTFS signature is missing.
Failed to mount '/dev/nvme0n1p3': Invalid argument
The device '/dev/nvme0n1p3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/nvme0n1p3 : Error code 12
mount -r /dev/nvme0n1p3 /mnt/boot-sav/nvme0n1p3
NTFS signature is missing.
Failed to mount '/dev/nvme0n1p3': Invalid argument
The device '/dev/nvme0n1p3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/nvme0n1p3 : Error code 12
Unhide GRUB boot menu in nvme0n1p5/boot/grub/grub.cfg


Boot successfully repaired.


You can now reboot your computer.
Please do not forget to make your BIOS boot on nvme0n1p1/EFI/ubuntu/shimx64.efi file!


If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
```

---

### Post by oldfred on 2017-10-15
Pastebin link
[https://paste.ubuntu.com/25746461/](https://paste.ubuntu.com/25746461/)

You have new NVMe drive which script does not fully parse.

But it looks like you left Windows fast start up on which is just hibernation.
The Linux NTFS driver will not mount hibernated Windows to prevent damage.

Can you boot Windows directly from UEFI boot menu, often f10 or f12 check your manual.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by dpanchal223 on 2017-10-15
Ok I've turned off the Windows fast startup. Do I run the Boot-Repair once more in Ubuntu from there? Will that correct the problem in Grub? I tried UEFI boot menu but it didn't have the Windows 10 option. I had to go through Windows Boot manager to get to Windows.

---

### Post by oldfred on 2017-10-15
If you can boot into Ubuntu run this:
sudo update-grub

Do not understand. System boots via UEFI, you would not get a Windows  boot manager unless that was from UEFI??

From Ubuntu post this as your UEFI entries:
sudo efibootmgr -v

---

### Post by dpanchal223 on 2017-10-15
Hi,

I tried that and am getting the same issue still. I ran the boot-repair once more (paste.ubuntu.com/25749907) and it looks like its giving me the same issue. Apparently it says near lines 530,
"[COLOR=#000000]NTFS signature is missing.[/COLOR]Failed to mount [COLOR=#BB4444]'/dev/nvme0n1p3'[/COLOR]: Invalid argument
The device [COLOR=#BB4444]'/dev/nvme0n1p3'[/COLOR] doesn[COLOR=#BB4444]'t seem to have a valid NTFS.[/COLOR]
[COLOR=#BB4444]Maybe the wrong device is used? Or the whole disk instead of a[/COLOR]
[COLOR=#BB4444]partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?[/COLOR] [COLOR=#BB4444]mount /dev/nvme0n1p3 : Error code 12[/COLOR] "

It doesn't see an NTFS signature for the windows partition. How would I address this?

---

### Post by oldfred on 2017-10-16
You show no UUID on p2 & p3.
It is normal to not have UUID and report to show error on Windows system reserved partition as it is a required, but unformatted partition.
       Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)

But if main Windows NTFS partition has error, then that should be fixed.
Signature often is the NTFS partition boot sector. It either is erased or damaged. (Some install grub to NTFS partition erasing the Windows required data).
But NTFS has a backup.

See if this works.
       
 You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

