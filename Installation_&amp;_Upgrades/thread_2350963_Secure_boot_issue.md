---
title: "Secure boot issue"
date: 2017-01-29
forum: Installation &amp; Upgrades
---

### Post by plissken2 on 2017-01-29
[COLOR=#000000][FONT=Tahoma]Hello everybody i just joined the forum :)[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]I'm writing because i'm having some issues in getting Ubuntu GNOME 16.10 Working with Secure Boot enabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]I've a Dell Xps13 3360 bought with Windows pre installed.[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]I installed Ubuntu removing windows but i can't get it to work with Secure Boot enabled as shimx64.efi is needed to launch GRUB but it's absent.[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]At the moment i'm using my computer with Secure boot disabled.[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]Has anyone experencied this kind of issue?[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]P.S For my job (web development) I need Virtual box, so if i'll manage to get Secure Boot working what do i need to do to use it with secure boot?[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]Thank you for you attention[/FONT][/COLOR]

---

### Post by oldfred on 2017-01-29
If you installed with Secure boot on, it should have installed in Secure boot mode.
But with Secure Boot on, most systems require you to allow USB boot with another setting in UEFI, as that is not normally secure.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by plissken2 on 2017-01-29
Hi!
thank you for your answer!
this is the output of the tool you suggested:

 ```
Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]




============================= Boot Info Summary: ===============================




ubuntu-gnome-vg-root: __________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.10
    Boot files:        /etc/fstab


ubuntu-gnome-vg-swap_1: ________________________________________________________


    File system:       swap
    Boot sector type:  -
    Boot sector info: 


============================ Drive/Partition Info: =============================


no valid partition table found
"blkid" output: ________________________________________________________________


Device           UUID                                   TYPE       LABEL


/dev/mapper/nvme0n1p3_crypt bBovLh-7CzH-6slE-Pxbs-1CW8-RCtb-AeU82i LVM2_member 
/dev/mapper/ubuntu--gnome--vg-root 188d8e0f-3098-486e-9508-f9a7e15ea312   ext4       
/dev/mapper/ubuntu--gnome--vg-swap_1 60eb1e5e-2f0b-4b2e-a1de-6a4b022b1ae8   swap       
/dev/nvme0n1                                                       
/dev/nvme0n1p1   E478-87D9                              vfat       
/dev/nvme0n1p2   e1f71d2a-03c8-4f1f-aa9a-0dbdf9dc6169   ext2       
/dev/nvme0n1p3   82ea1886-8a1a-48ac-b7fa-c8dc77b4f94d   crypto_LUKS 


========================= "ls -l /dev/disk/by-id" output: ======================


total 0
lrwxrwxrwx 1 root root 10 Jan 29 20:46 dm-name-nvme0n1p3_crypt -> ../../dm-0
lrwxrwxrwx 1 root root 10 Jan 29 20:46 dm-name-ubuntu--gnome--vg-root -> ../../dm-1
lrwxrwxrwx 1 root root 10 Jan 29 20:46 dm-name-ubuntu--gnome--vg-swap_1 -> ../../dm-2
lrwxrwxrwx 1 root root 10 Jan 29 20:46 dm-uuid-CRYPT-LUKS1-82ea18868a1a48acb7fac8dc77b4f94d-nvme0n1p3_crypt -> ../../dm-0
lrwxrwxrwx 1 root root 10 Jan 29 20:46 dm-uuid-LVM-ks6gV2Zrb3rMVJN29m3h6aAdRDlEDE3Z3wXxgRsdxq6TIbiA3LGcGXm2tHrveZMC -> ../../dm-1
lrwxrwxrwx 1 root root 10 Jan 29 20:46 dm-uuid-LVM-ks6gV2Zrb3rMVJN29m3h6aAdRDlEDE3ZzJDBxeI2h6V3MccKjnQOF2FrpNutCMpL -> ../../dm-2
lrwxrwxrwx 1 root root 10 Jan 29 20:46 lvm-pv-uuid-bBovLh-7CzH-6slE-Pxbs-1CW8-RCtb-AeU82i -> ../../dm-0
lrwxrwxrwx 1 root root 15 Jan 29 20:46 nvme-THNSN5256GPUK -> ../../nvme0n1p3
lrwxrwxrwx 1 root root 13 Jan 29 20:46 nvme-eui.00080d0200107a6a -> ../../nvme0n1
lrwxrwxrwx 1 root root 15 Jan 29 20:46 nvme-eui.00080d0200107a6a-part1 -> ../../nvme0n1p1
lrwxrwxrwx 1 root root 15 Jan 29 20:46 nvme-eui.00080d0200107a6a-part2 -> ../../nvme0n1p2
lrwxrwxrwx 1 root root 15 Jan 29 20:46 nvme-eui.00080d0200107a6a-part3 -> ../../nvme0n1p3


========================= "ls -R /dev/mapper/" output: =========================


/dev/mapper:
control
nvme0n1p3_crypt
ubuntu--gnome--vg-root
ubuntu--gnome--vg-swap_1


================================ Mount points: =================================


Device           Mount_Point              Type       Options


/dev/mapper/ubuntu--gnome--vg-root /                        ext4       (rw,relatime,errors=remount-ro,data=ordered)
/dev/nvme0n1p1   /boot/efi                vfat       (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/nvme0n1p2   /boot                    ext2       (rw,relatime,block_validity,barrier,user_xattr,acl)




======================= ubuntu-gnome-vg-root/etc/fstab: ========================


--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--gnome--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/nvme0n1p2 during installation
UUID=e1f71d2a-03c8-4f1f-aa9a-0dbdf9dc6169 /boot           ext2    defaults        0       2
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=E478-87D9  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/ubuntu--gnome--vg-swap_1 none            swap    sw              0       0
--------------------------------------------------------------------------------


=========== ubuntu-gnome-vg-root: Location of files loaded by Grub: ============


           GiB - GB             File                                 Fragment(s)


   0.059690475 = 0.064092160    vmlinuz                                       10
   0.217893600 = 0.233961472    vmlinuz.old                                   11
   0.122642517 = 0.131686400    initrd.img                                    15
   0.474609375 = 0.509607936    initrd.img.old                                23


=============================== StdErr Messages: ===============================


File descriptor 9 (/proc/9648/mountinfo) leaked on lvs invocation. Parent PID 18370: bash
File descriptor 63 (pipe:[240994]) leaked on lvs invocation. Parent PID 18370: bash
File descriptor 9 (/proc/9648/mountinfo) leaked on lvchange invocation. Parent PID 18417: bash
File descriptor 63 (pipe:[240994]) leaked on lvchange invocation. Parent PID 18417: bash
File descriptor 9 (/proc/9648/mountinfo) leaked on lvchange invocation. Parent PID 18417: bash
File descriptor 63 (pipe:[240994]) leaked on lvchange invocation. Parent PID 18417: bash


ADDITIONAL INFORMATION :
=================== log of boot-info 2017-01-29__20h46 ===================
boot-info version : 4ppa40
boot-sav version : 4ppa40
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa40
BLKID BEFORE LVM ACTIVATION:
/dev/mapper/nvme0n1p3_crypt: UUID="bBovLh-7CzH-6slE-Pxbs-1CW8-RCtb-AeU82i" TYPE="LVM2_member"
/dev/mapper/ubuntu--gnome--vg-root: UUID="188d8e0f-3098-486e-9508-f9a7e15ea312" TYPE="ext4"
/dev/nvme0n1: PTUUID="0b1ce20e-df63-4129-a1d4-b948bd20877e" PTTYPE="gpt"
/dev/nvme0n1p1: UUID="E478-87D9" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="f2abaf3b-e98e-4c59-8a8b-d98f3e34e760"
/dev/nvme0n1p2: UUID="e1f71d2a-03c8-4f1f-aa9a-0dbdf9dc6169" TYPE="ext2" PARTUUID="46522921-9757-438f-aeb7-8a2a43cf6dae"
/dev/nvme0n1p3: UUID="82ea1886-8a1a-48ac-b7fa-c8dc77b4f94d" TYPE="crypto_LUKS" PARTUUID="2a385cfe-365c-469c-803e-d8dfe5ea63ab"
/dev/mapper/ubuntu--gnome--vg-swap_1: UUID="60eb1e5e-2f0b-4b2e-a1de-6a4b022b1ae8" TYPE="swap"
MODPROBE
VGSCAN
File descriptor 9 (/proc/9648/mountinfo) leaked on vgscan invocation. Parent PID 9660: /bin/bash
Reading volume groups from cache.
Found volume group "ubuntu-gnome-vg" using metadata type lvm2
VGCHANGE
File descriptor 9 (/proc/9648/mountinfo) leaked on vgchange invocation. Parent PID 9660: /bin/bash
2 logical volume(s) in volume group "ubuntu-gnome-vg" now active
File descriptor 9 (/proc/9648/mountinfo) leaked on lvscan invocation. Parent PID 9660: /bin/bash
LVSCAN:
ACTIVE            '/dev/ubuntu-gnome-vg/root' [229.60 GiB] inherit
ACTIVE            '/dev/ubuntu-gnome-vg/swap_1' [7.88 GiB] inherit
Successfully activated LVM.
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
E' presente la tecnologia RAID su questo computer? no
File descriptor 9 (/proc/9648/mountinfo) leaked on lvs invocation. Parent PID 11296: /bin/sh
Error: /dev/mapper/nvme0n1p3_crypt: unrecognised disk label
Error: /dev/mapper/nvme0n1p3_crypt: unrecognised disk label
boot-info is executed in installed-session (Ubuntu 16.10, yakkety, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/vmlinuz-4.8.0-34-generic.efi.signed root=/dev/mapper/ubuntu--gnome--vg-root ro quiet splash vt.handoff=7
Set mapper/ubuntu--gnome--vg-root as corresponding disk of mapper/ubuntu--gnome--vg-root
nvme0n1 (mapper/ubuntu--gnome--vg-root) has unknown type. Per cortesia, invia un messaggio a [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
Set mapper/ubuntu--gnome--vg-root as corresponding disk of mapper/ubuntu--gnome--vg-root
nvme0n1 (mapper/ubuntu--gnome--vg-root) has unknown type. Per cortesia, invia un messaggio a [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]
mount: unknown filesystem type 'crypto_LUKS'
mount /dev/nvme0n1p3 : Error code 32
mount -r /dev/nvme0n1p3 /mnt/boot-sav/nvme0n1p3
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/nvme0n1p3 : Error code 32
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount /dev/nvme0n1 : Error code 32
mount -r /dev/nvme0n1 /mnt/boot-sav/nvme0n1
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount -r /dev/nvme0n1 : Error code 32
ls: impossibile accedere a '/sys/block/mapper/ubuntu--gnome--vg-root/': File o directory non esistente


=================== os-prober:
/dev/mapper/ubuntu--gnome--vg-root:Sistema operativo ora in uso - Ubuntu 16.10 CurrentSession:linux


=================== blkid:
/dev/mapper/nvme0n1p3_crypt: UUID="bBovLh-7CzH-6slE-Pxbs-1CW8-RCtb-AeU82i" TYPE="LVM2_member"
/dev/mapper/ubuntu--gnome--vg-root: UUID="188d8e0f-3098-486e-9508-f9a7e15ea312" TYPE="ext4"
/dev/nvme0n1p1: UUID="E478-87D9" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="f2abaf3b-e98e-4c59-8a8b-d98f3e34e760"
/dev/nvme0n1p2: UUID="e1f71d2a-03c8-4f1f-aa9a-0dbdf9dc6169" TYPE="ext2" PARTUUID="46522921-9757-438f-aeb7-8a2a43cf6dae"
/dev/nvme0n1p3: UUID="82ea1886-8a1a-48ac-b7fa-c8dc77b4f94d" TYPE="crypto_LUKS" PARTUUID="2a385cfe-365c-469c-803e-d8dfe5ea63ab"
/dev/mapper/ubuntu--gnome--vg-swap_1: UUID="60eb1e5e-2f0b-4b2e-a1de-6a4b022b1ae8" TYPE="swap"
/dev/nvme0n1: PTUUID="0b1ce20e-df63-4129-a1d4-b948bd20877e" PTTYPE="gpt"


Set mapper/ubuntu--gnome--vg-root as corresponding disk of mapper/ubuntu--gnome--vg-root


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


mount: unknown filesystem type 'crypto_LUKS'
mount /dev/nvme0n1p3 : Error code 32
mount -r /dev/nvme0n1p3 /mnt/boot-sav/nvme0n1p3
mount: unknown filesystem type 'crypto_LUKS'
mount -r /dev/nvme0n1p3 : Error code 32
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount /dev/nvme0n1 : Error code 32
mount -r /dev/nvme0n1 /mnt/boot-sav/nvme0n1
mount: /dev/nvme0n1 is already mounted or /mnt/boot-sav/nvme0n1 busy
mount -r /dev/nvme0n1 : Error code 32
sfdisk: failed to dump partition table: Successo


=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 ott 12 21:28 grub.d
totale 76
-rwxr-xr-x 1 root root  9791 set  6 16:10 00_header
-rwxr-xr-x 1 root root  6258 mar 15  2016 05_debian_theme
-rwxr-xr-x 1 root root 12261 set  6 16:10 10_linux
-rwxr-xr-x 1 root root 11082 set  6 16:10 20_linux_xen
-rwxr-xr-x 1 root root  1992 gen 28  2016 20_memtest86+
-rwxr-xr-x 1 root root 11692 set  6 16:10 30_os-prober
-rwxr-xr-x 1 root root  1418 set  6 16:10 30_uefi-firmware
-rwxr-xr-x 1 root root   214 set  6 16:10 40_custom
-rwxr-xr-x 1 root root   216 set  6 16:10 41_custom
-rw-r--r-- 1 root root   483 set  6 16:10 README








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






/boot/efi detected in the fstab of mapper/ubuntu--gnome--vg-root: UUID=E478-87D9   (nvme0n1p1)
/boot detected in the fstab of mapper/ubuntu--gnome--vg-root: UUID=e1f71d2a-03c8-4f1f-aa9a-0dbdf9dc6169  (nvme0n1p2)
Presence of EFI/Boot file detected: /boot/efi/EFI/Boot/bootx64.efi


=================== efibootmgr -v
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0001
Boot0000* Windows Boot Manager    HD(1,GPT,6c0ce6ec-c1c4-407e-bf3a-985496b0f3b3,0x800,0xfa000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0001* ubuntu    PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x0)/NVMe(0x1,00-08-0D-02-00-10-7A-6A)/HD(1,GPT,f2abaf3b-e98e-4c59-8a8b-d98f3e34e760,0x800,0x100000)/File(EFIubuntugrubx64.efi)


=================== UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this installed-session.
SecureBoot disabled. (maybe sec-boot, Per cortesia, invia un messaggio a [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL])




=================== PARTITIONS & DISKS:
mapper/ubuntu--gnome--vg-root    : mapper/ubuntu--gnome--vg-root,    not-sepboot,    grubenv-ok    grub2,    signed grub-efi ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    .
nvme0n1p1    : nvme0n1,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /boot/efi.
nvme0n1p2    : nvme0n1,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /boot.
nvme0n1p3    : nvme0n1,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/nvme0n1p3.
nvme0n1    : mapper/ubuntu--gnome--vg-root,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/nvme0n1.


mapper/ubuntu--gnome--vg-root    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
nvme0n1    : GPT,    no-BIOS_boot,    has-correctEFI,     not-usb,    no-os,    2048 sectors * 512 bytes




=================== parted -l:


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--gnome--vg-swap_1: 8464MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:


Number  Start  End     Size    File system     Flags
1      0.00B  8464MB  8464MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--gnome--vg-root: 247GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags:


Number  Start  End    Size   File system  Flags
1      0.00B  247GB  247GB  ext4




Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/nvme0n1p3_crypt: 255GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:


Model: Unknown (unknown)
Disk /dev/nvme0n1: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:


Number  Start   End     Size   File system  Name                  Flags
1      1049kB  538MB   537MB  fat32        EFI System Partition  boot, esp
2      538MB   1050MB  512MB  ext2
3      1050MB  256GB   255GB


=================== parted -lm:


BYT;
/dev/mapper/ubuntu--gnome--vg-swap_1:8464MB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:8464MB:8464MB:linux-swap(v1)::;


BYT;
/dev/mapper/ubuntu--gnome--vg-root:247GB:dm:512:512:loop:Linux device-mapper (linear):;
1:0.00B:247GB:247GB:ext4::;


BYT;
/dev/mapper/nvme0n1p3_crypt:255GB:dm:512:512:unknown:Linux device-mapper (crypt):;


BYT;
/dev/nvme0n1:256GB:unknown:512:512:gpt:Unknown:;
1:1049kB:538MB:537MB:fat32:EFI System Partition:boot, esp;
2:538MB:1050MB:512MB:ext2::;
3:1050MB:256GB:255GB:::;


=================== lsblk:
KNAME     TYPE  FSTYPE        SIZE LABEL
nvme0n1   disk              238,5G
nvme0n1p3 part  crypto_LUKS 237,5G
dm-0      crypt LVM2_member 237,5G
dm-1      lvm   ext4        229,6G
dm-2      lvm   swap          7,9G
nvme0n1p1 part  vfat          512M
nvme0n1p2 part  ext2          488M


KNAME     ROTA RO RM STATE   MOUNTPOINT
nvme0n1      0  0  0
nvme0n1p3    0  0  0
dm-0         0  0  0 running
dm-1         0  0  0 running /
dm-2         0  0  0 running [SWAP]
nvme0n1p1    0  0  0         /boot/efi
nvme0n1p2    0  0  0         /boot




=================== mount:
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=4003764k,nr_inodes=1000941,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=805336k,mode=755)
/dev/mapper/ubuntu--gnome--vg-root on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,release_agent=/lib/systemd/systemd-cgroups-agent,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=34,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=12037)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/dev/nvme0n1p2 on /boot type ext2 (rw,relatime,block_validity,barrier,user_xattr,acl)
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
tmpfs on /run/user/121 type tmpfs (rw,nosuid,nodev,relatime,size=805332k,mode=700,uid=121,gid=127)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=805332k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)




=================== ls:
/sys/block/dm-0 (filtered):  alignment_offset badblocks bdi capability dev discard_alignment dm ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-1 (filtered):  alignment_offset badblocks bdi capability dev discard_alignment dm ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/dm-2 (filtered):  alignment_offset badblocks bdi capability dev discard_alignment dm ext_range holders inflight integrity power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/nvme0n1 (filtered):  alignment_offset badblocks bdi capability dev device discard_alignment eui ext_range holders inflight integrity mq nsid nvme0n1p1 nvme0n1p2 nvme0n1p3 power queue range removable ro size slaves stat subsystem trace uevent wwid
/dev (filtered):  256GB_96OS13BXT18T 256GB_96OS13BXT18T-part1 256GB_96OS13BXT18T-part2 256GB_96OS13BXT18T-part3 acpi_thermal_rel autofs block btrfs-control bus char console core cpu cpu_dma_latency cuse disk dm-0 dm-1 dm-2 dri drm_dp_aux0 drm_dp_aux1 drm_dp_aux2 ecryptfs fb0 fd full fuse gpiochip0 hidraw0 hpet hugepages hwrng i2c-0 i2c-1 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 initctl input kmsg kvm lightnvm log mapper mcelog media0 mei0 mem memory_bandwidth mqueue net network_latency network_throughput null NVMe nvme0 nvme0n1 nvme0n1p1 nvme0n1p2 nvme0n1p3 port ppp psaux ptmx pts random rfkill rtc rtc0 shm snapshot snd stderr stdin stdout TOSHIBA tpm0 ubuntu-gnome-vg uhid uinput urandom userio v4l vboxdrv vboxdrvu vboxnetctl vboxusb vfio vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control nvme0n1p3_crypt ubuntu--gnome--vg-root ubuntu--gnome--vg-swap_1
ls: impossibile accedere a '': File o directory non esistente


=================== hexdump -n512 -C /dev/nvme0n1p1
00000000  eb 58 90 6d 6b 66 73 2e  66 61 74 00 02 08 20 00  |.X.mkfs.fat... .|
00000010  02 00 00 00 00 f8 00 00  20 00 40 00 00 08 00 00  |........ .@.....|
00000020  00 00 10 00 00 04 00 00  00 00 00 00 02 00 00 00  |................|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 01 29 d9 87 78 e4 4e  4f 20 4e 41 4d 45 20 20  |..)..x.NO NAME  |
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


Filesystem                         Type      Size  Used Avail Use% Mounted on
udev                               devtmpfs  3.9G     0  3.9G   0% /dev
tmpfs                              tmpfs     787M   10M  777M   2% /run
/dev/mapper/ubuntu--gnome--vg-root ext4      225G   31G  184G  15% /
tmpfs                              tmpfs     3.9G  351M  3.5G   9% /dev/shm
tmpfs                              tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                              tmpfs     3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/nvme0n1p2                     ext2      473M  134M  315M  30% /boot
/dev/nvme0n1p1                     vfat      511M  1.2M  510M   1% /boot/efi
tmpfs                              tmpfs     787M   24K  787M   1% /run/user/121
tmpfs                              tmpfs     787M   48K  787M   1% /run/user/1000


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




Disk /dev/nvme0n1: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0B1CE20E-DF63-4129-A1D4-B948BD20877E


Device           Start       End   Sectors   Size Type
/dev/nvme0n1p1    2048   1050623   1048576   512M EFI System
/dev/nvme0n1p2 1050624   2050047    999424   488M Linux filesystem
/dev/nvme0n1p3 2050048 500117503 498067456 237.5G Linux filesystem




Disk /dev/mapper/nvme0n1p3_crypt: 237.5 GiB, 255008440320 bytes, 498063360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/mapper/ubuntu--gnome--vg-root: 229.6 GiB, 246532800512 bytes, 481509376 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/mapper/ubuntu--gnome--vg-swap_1: 7.9 GiB, 8464105472 bytes, 16531456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes








=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to sign-grub enable-lvm) and reinstall the grub-efi-amd64-signed of mapper/ubuntu--gnome--vg-root, using the following options:        nvme0n1p2/boot, nvme0n1p1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    use-standard-efi-file rename-ms-efi




=================== Advice in case of suggested repair
Si consiglia di riprovare dopo aver decriptato le partizioni. ([https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory))
Continuare?




=================== Final advice in case of suggested repair
Non dimenticare di impostare la priorità di avvio nel BIOS al disco mapper/ubuntu--gnome--vg-root (247GB)!




=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2017-01-29
Please use Code Tags if longer code or text. With Summary Repair better to just post link it provides.
You can easily add Code Tags with Forum's advanced editor and # icon.

Is your system working correctly with Secure Boot turned off?
I have been trying to help another user with similar configuration, but do not know LVM, encryption nor NVMe configurations.
[https://ubuntuforums.org/showthread.php?t=2349833](https://ubuntuforums.org/showthread.php?t=2349833)

Does Boot-Repair ask to unencrypt your LVM, or do you have to separately do that.

Boot-Repair's suggested repair is to install the signed versions of the kernel which would include shimx64.efi. 
But I do not use Secure Boot and have /EFI/ubuntu/shimx64.efi. You may not be able to see that as fstab is mounting the efi with umask=0077.
Boot-Repair will also change that to defaults and then it will be visible, as it has to be able to edit it. But it may not be quite as secure if not at 0077 or not readable nor writeable.

---

### Post by plissken2 on 2017-01-30
Ok sorry for how i posted the output.
I will not happen again ;)

Yes, my system is working correctly with Secure Boot turned off.
So you're advising me to run the Boot Repair's suggested repair?

Thank you for your help

---

### Post by oldfred on 2017-01-30
Yes, run Boot-Repairs updates to signed kernels as that should support UEFI Secure Boot. It still should boot with Secure boot off also.

Just make sure your lvm is mounted & / is unencrypted, so the updates see your full configuration. 
Not sure how Boot-Repair handles LVM & encryption. I do know it has issues with determining if BIOS RAID or LVM as both mount with /mapper...

---

### Post by plissken2 on 2017-01-30
Problem solved following the steps from Boot Repair as you suggested :D
Thank you very much

---

