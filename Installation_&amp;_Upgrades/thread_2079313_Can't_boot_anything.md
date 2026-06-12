---
title: "Can't boot anything"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by AliPM on 2012-11-01
Hi,

I have a Lenovo S205 netbook and until recently I'd been happy just running XP, I had a heap of problems trying to get Ubuntu on it when I bought it 6 months ago and eventually I gave up. Last weekend I decided to try and sort this out, so after reading a lot of forum and blog posts and reinstalling Windows 7, XP and Ubuntu (64 bit) over and over again I now have a system that I can't boot except through a LiveUSB.

I took some advice from somewhere to reformat my hard drive as GPT, and to create a boot partition (with mount point /boot) and install the bootloader there. I also created a 50mb EFI boot partition according to some different advice.

Now when I turn on the laptop it doesn't go to any bootloader at all. There's a boot entry in my BIOS for PCI LAN, and it goes automatically to this, and then back to the BIOS Boot Menu screen (not much use).

If someone could advise me how to reinstall the bootloader in one of the boot partitions that would be great. I don't care if the best thing to do is reformat the disk as MBR if that helps, but I can't handle another reinstall just to get the same non-result I got the last 3 times.

I could only get the wireless on my laptop to work when the disk is in IDE mode, so this has to stay this way. I don't know if that is important info or not.

Massive thanks in advance for any help anyone can offer.

Ali

---

### Post by oldfred on 2012-11-01
Is this an older system? Only new in the last year or so have UEFI boot in place of BIOS boot. And Windows will only boot in gpt partitioning with UEFI.

Best to post link to BootInfo report, you can download into Ubuntu liveCD or USB and run.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by AliPM on 2012-11-02
Thanks very much. I ran boot-repair and selected 'Create a Boot info summary', but it didn't generate a link to a url. It asked me if I wanted to install pastebinit, I said yes but it didn't do it. Tried running sudo boot-repair too but still wouldn't install pastebinit.

Here is the full boot report:



    ```
Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info October 25th 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    300248 of the same hard drive for core.img. core.img is at this location 
    and looks in partition 1 for /grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:  Syslinux looks at sector 7892 of /dev/sdb1 for its 
                       second stage. According to the info in the boot 
                       sector, sdb1 starts at sector 0. But according to the 
                       info from fdisk, sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   625,142,447   625,142,447  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       976,895       974,848 EFI System partition
/dev/sda2         976,896   137,695,231   136,718,336 Data partition (Windows/Linux)
/dev/sda3     137,695,232   145,508,351     7,813,120 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2063 MB, 2063073280 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4029440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     4,027,519     4,027,458   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       3cc0ecd6-bccb-4154-945c-8db8b80527f7   ext3       
/dev/sda1        c7c4f6f4-c0f3-474a-9f95-d4770ec92a79   ext4       
/dev/sda2        1936ff47-fcca-4e4c-9926-c140b4333094   ext4       
/dev/sda3        328a6a20-29dd-41f3-8e72-e8f1de000c72   swap       
/dev/sdb1        75D6-B625                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/1936ff47-fcca-4e4c-9926-c140b4333094 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 1936ff47-fcca-4e4c-9926-c140b4333094
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set c7c4f6f4-c0f3-474a-9f95-d4770ec92a79
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c7c4f6f4-c0f3-474a-9f95-d4770ec92a79
    linux    /vmlinuz-2.6.32-38-generic root=UUID=1936ff47-fcca-4e4c-9926-c140b4333094 ro   quiet splash
    initrd    /initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c7c4f6f4-c0f3-474a-9f95-d4770ec92a79
    echo    'Loading Linux 2.6.32-38-generic ...'
    linux    /vmlinuz-2.6.32-38-generic root=UUID=1936ff47-fcca-4e4c-9926-c140b4333094 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-38-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c7c4f6f4-c0f3-474a-9f95-d4770ec92a79
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c7c4f6f4-c0f3-474a-9f95-d4770ec92a79
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.143192291 = 0.153751552    grub/core.img                                  1
   0.143558502 = 0.154144768    grub/grub.cfg                                  2
   0.040023804 = 0.042975232    initrd.img-2.6.32-38-generic                   1
   0.016479492 = 0.017694720    vmlinuz-2.6.32-38-generic                      1

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=1936ff47-fcca-4e4c-9926-c140b4333094 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=c7c4f6f4-c0f3-474a-9f95-d4770ec92a79 /boot           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=328a6a20-29dd-41f3-8e72-e8f1de000c72 none            swap    sw              0       0
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-11-02__20h08 ===================
boot-repair version : 3.194~ppa50~lucid
boot-sav version : 3.194~ppa50~lucid
glade2script-gtk2 version : 3.2.2~ppa45~lucid
boot-sav-extra version :
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
boot-repair is executed in live-session (Ubuntu 10.04.4 LTS, lucid, Ubuntu, x86_64)
CPU op-mode(s):        64-bit
BOOT_IMAGE=/casper/vmlinuz noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda2:Ubuntu 10.04.4 LTS (10.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="3cc0ecd6-bccb-4154-945c-8db8b80527f7" TYPE="ext3"
/dev/sda1: UUID="c7c4f6f4-c0f3-474a-9f95-d4770ec92a79" TYPE="ext4"
/dev/sda2: UUID="1936ff47-fcca-4e4c-9926-c140b4333094" TYPE="ext4"
/dev/sda3: UUID="328a6a20-29dd-41f3-8e72-e8f1de000c72" TYPE="swap"
/dev/sdb1: UUID="75D6-B625" TYPE="vfat"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.



=================== /media/1936ff47-fcca-4e4c-9926-c140b4333094/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== /media/1936ff47-fcca-4e4c-9926-c140b4333094/etc/grub.d/ :
drwxr-xr-x  2 root    root     4096 2012-02-14 11:47 grub.d
total 40
-rwxr-xr-x 1 root root 4444 2012-01-20 15:56 00_header
-rwxr-xr-x 1 root root 1416 2012-01-20 15:34 05_debian_theme
-rwxr-xr-x 1 root root 4843 2012-01-20 15:56 10_linux
-rwxr-xr-x 1 root root  918 2010-03-23 10:40 20_memtest86+
-rwxr-xr-x 1 root root 6605 2012-01-20 15:56 30_os-prober
-rwxr-xr-x 1 root root  214 2012-01-20 15:56 40_custom
-rw-r--r-- 1 root root  483 2012-01-20 15:56 README


/boot detected in the fstab of sda2: UUID=c7c4f6f4-c0f3-474a-9f95-d4770ec92a79  (sda1)
=================== UEFI/Legacy mode :
EFI in dmesg. Please report this message to [EMAIL="yannubuntu@gmail.com"]yannubuntu@gmail.com[/EMAIL]
This live-session is not EFI-compatible.
[    0.000000] ACPI: UEFI 0000000066404000 0003E (v01 LENOVO CB-01    00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 0000000066403000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000663ff000 00116 (v01 LENOVO CB-01    00000001 PTL  00000001)


=================== PARTITIONS & DISKS:
sda1    : sda,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    grub2,    grub-pc,    update-grub,    64,    no-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /media/1936ff47-fcca-4e4c-9926-c140b4333094.

sda    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA HITACHI HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      1049kB  500MB   499MB   ext4                  boot
2      500MB   70.5GB  70.0GB  ext4
3      70.5GB  74.5GB  4000MB  linux-swap(v1)


Model: Samsung Mighty Drive (scsi)
Disk /dev/sdb: 2063MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      31.7kB  2062MB  2062MB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:320GB:scsi:512:512:gpt:ATA HITACHI HTS54323;
1:1049kB:500MB:499MB:ext4::boot;
2:500MB:70.5GB:70.0GB:ext4::;
3:70.5GB:74.5GB:4000MB:linux-swap(v1)::;

BYT;
/dev/sdb:2063MB:scsi:512:512:msdos:Samsung Mighty Drive;
1:31.7kB:2062MB:2062MB:fat32::boot, lba;


=================== mount:
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/1936ff47-fcca-4e4c-9926-c140b4333094 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  audio1 block bsg btrfs-control bus char console core cpu_dma_latency disk dsp1 ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mem mixer mixer1 net network_latency network_throughput null oldmem pktcdvd port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sequencer sequencer2 sg0 sg1 shm snapshot snd sndstat stderr stdin stdout urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 v4l vga_arbiter video0 zero
ls /dev/mapper:  control

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    646M  123M  491M  21% /
none      devtmpfs    799M  304K  798M   1% /dev
/dev/sdb1     vfat    2.0G  1.4G  611M  69% /cdrom
/dev/loop0
squashfs    665M  665M     0 100% /rofs
none         tmpfs    804M  288K  804M   1% /dev/shm
tmpfs        tmpfs    804M  1.7M  802M   1% /tmp
none         tmpfs    804M   92K  804M   1% /var/run
none         tmpfs    804M  4.0K  804M   1% /var/lock
none         tmpfs    804M     0  804M   0% /lib/init/rw
/dev/sda2     ext4     65G  2.2G   59G   4% /media/1936ff47-fcca-4e4c-9926-c140b4333094
/dev/sda1     ext4    461M   27M  411M   6% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38914   312571223+  ee  GPT

Disk /dev/sdb: 2063 MB, 2063073280 bytes
64 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002378f

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1015     2013729    c  W95 FAT32 (LBA)


/boot detected. Please check the options.
(debug) reinstall grub2 place-in-MBR no-BIOS_boot (sda2)
=================== Repair blockers
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sda2 into the MBR of sda, using the following options:        sda1/boot,
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer. See you soon!
pastebinit  packages needed
E: Package pastebinit has no installation candidate
Could not install pastebinit
Please install the [pastebinit ] packages.  Then try again.
```

---

### Post by oldfred on 2012-11-02
Added code tags to make it easier to read. Please use code tags on any long post to preserve formatting and make it easier to read.

I have not seen grub2's core.img install to an efi partition. If booting with UEFI you need gpt and an efi partition. But if using gpt with Linux only, as Windows only boots from gpt partitioned drives with UEFI, you need a bios_grub partition. The bios grub can be anywhere on drive. Efi partition is suppose to be first. 

An efi partition has to have a FAT32 format. And a bios_grub has  to not have any format at all. But somehow you have a partition labeled efi but formatted ext4 and used as a /boot partition.

Some BIOS/grub boot issues have been caused by very large / (root) partitions. Boot-Repair suggests a separate /boot, I usually suggest a smaller 25GB / and a separate /home for the rest of the drive.

Also 10.04 was not efi compatible, but I did use gpt partitioning and BIOS boot with a bios_grub partition without issue.

If your system is not UEFI or you will never use UEFI, then you do not need efi partition.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Gone fishing on 2012-11-02
I recently had a problem with getting a Lenovo to boot via EFI and GPT. I was more brutal and just used parted to write a new MBR type partition table.

Started up on a live cd and then ran 

```
parted /dev/sda
``` followed by ```
mktable
``` it then asked what type I used ```
msdos
``` parted warned me that all the data on the disk would be lost and I ended up with a standard diskthat installed linux without any messing about.

---

### Post by AliPM on 2012-11-03
Thanks for all the advice. To be honest I'm not sure I understand all of it, but it's great to have.

I don't understand UEFI well enough to explain why I created an EFI partition - I read on a forum somewhere that if a computer has EFI, it is preferable to use it. If it would be better to scrap this, I certainly don't mind doing it.

I want to dual-boot Ubuntu with Windows 7 or XP, will this be easier if I reformat the disk as MBR?

I have never bothered with a /home partition in the past, because when dual-booting I've found it more useful to have a non-system partition formatted in NTFS that I can access from Windows and Linux.

If I leave it all as it is, can I change the size of the partition with Ubuntu installed without reinstalling it?

Once again, thanks for the help

---

### Post by oldfred on 2012-11-03
If you want XP you have to have drive formatted with MBR(msdos), XP does not work with gpt drives nor is able to read them. Windows 7 will boot from gpt partitioned drives only with UEFI but can read another drive that is gpt if even if Windows 7 is installed in MBR.

I prefer to have Windows & Linux on separate drives but many are installing to one drive systems, so you have to find what works with both.

Windows has to be installed in primary partitions sda1 thru sda4 formatted NTFS with the boot flag. With gpt all partitions are in effect primary as there are no logical partitions, but then both Windows & Linux require added small partitions for system info.

---

### Post by AliPM on 2012-11-04
I used parted to make an MBR partition table (as Gone Fishing suggested). The first time I tried this I got an error message that one of the partitions was in use and that I needed to restart the computer to complete the process.

I restarted, ran the parted>mktable command again, this time with no error message. Disk Utility now says /dev/sda is partitioned as MBR.

However, my Windows 7 Installation USB doesn't boot into the installer. This works fine on my desktop PC. Any ideas why this could be?

If I create 1 or 2 NTFS partitions (for Windows 7 and XP) sda1 and sda2 before installing Ubuntu on sda3, could this cause any problems when I come back to install Windows later?

Thanks

---

### Post by oldfred on 2012-11-04
You should be able to create the NTFS partitions in advance. Just move boot flag to partition you want to install or Windows will combine boot into the one partition with boot flag.

Ubuntu will be fine in all logical partitions.

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

You may want another NTFS data partition for shared data. It can also be logical if not a boot. Although second installs of Windows can be in logical partitions they only can boot thru a first install in a primary partition. With shared data NTFS partition you can have data you share with Ubuntu & both Windows installs. 
I shared my Firefox & Thunderbird profiles & all photos with Picasa with a shared NTFS data partition.

---

### Post by AliPM on 2012-11-04
Installed Windows XP and created 2 NTFS partitions (from a newly-formatted disk) in the XP installer. I'm about to install Ubuntu now, and in the disk partitioner I can see that for some reason the 2 partitions I created are sda1 and sda5 - is this going to be a problem? You mentioned that Windows can only install onto sda1-4.

Any idea why it did this?

---

### Post by darkod on 2012-11-04
It seems the second partition is logical, not primary. Did it ever ask you whether you wanted to create it as logical?

Actually windows needs one primary partition (sda1-sda4) for the bootloader files. After that you can have a second copy of windows on a logical partition since windows will combine the boot files on one partition anyway.

But if you plan to have ubuntu and two versions of windows, all of them present in the grub boot menu (three OSs), then you need both windows installs onto primary partitions, AND you need to switch the boot flag from the first to the second windows partition BEFORE you install the second windows version. This is done to prevent it combining the boot files.
If it does combine the boot files, you will have only one windows in the grub menu, and then have another menu to select between the two windows versions.

In your place, I would redo it again, this time preparing the two ntfs partitions in advance using the ubuntu cd in live mode and Gparted. I know many people advise not to create partitions for windows with linux tools, but windows is so idiotic when you are talking about preparing partitions in advance. I guess because it can't even run in live mode so they weren't thinking about that.

Just delete all partitions again, and create two primary ntfs partitions with the sizes you want for XP and 7.

On the other hand, if you plan to install only XP it doesn't matter if the other ntfs partiton is logical or primary.

---

### Post by AliPM on 2012-11-04
Thanks darkod - no, the XP installer never asked me if I wanted the second partition I made to be primary or logical.

I've installed 7 as well just to see how it works, and although both OSes work OK, I will be reinstalling as you suggest because something went awry at some point before I installed XP, and the SATA mode in BIOS reverted to AHCI. 7 has to be installed in IDE mode for the wireless to work, so I'm now in a situation where I can access XP and 7, but before I choose in the bootloader I have to go into BIOS and check the SATA mode. Not really workable.

Regarding making NTFS partitions in Linux, I tried to do this using the partition manager before I installed Ubuntu (10.04) and it seemed that NTFS wasn't an option for the partition type. I guess I could use a later version, but 12.04 seemed a bit slow when I tried it before.

Another question - is it possible to boot from the LiveUSB straight into a command line prompt without loading the whole shell? Most of the times I'm booting into Linux just to enter a few lines in the terminal and it's rather frustrating having to wait 10 minutes every time I want to do this.

---

### Post by darkod on 2012-11-05
If you use Gparted from an installed ubuntu, the ntfs tools are not installed by default. That's why Gparted will not have the option to create ntfs partition.

But if you boot the cd in live mode and open Gparted, it can create ntfs since the support is included in the live cd.

If you want to add the ntfs support to your ubuntu, the package to install was something like ntfs-progs.

As for booting into terminal live mode, I'm not aware of a way but I have never really looked into it. I guess there is a way if you modify the boot lines (parameters), it only needs to be found.

---

### Post by darkod on 2012-11-05
> **Wisestep said:**
> I ran boot-repair and chosen 'Create a Start details summary', but it didn't produce a weblink to a url. It requested me if I desired to set up pastebinit, I said yes but it didn't do it. Tried operating sudo boot-repair too but still wouldn't set up pastebinit.

You can also use the boot_info_script directly, the link is in my signature. It will produce the same results.txt (not a link), so you will have to attach the .txt to your post.

---

### Post by AliPM on 2012-11-05
I've virtually only been running Ubuntu from the LiveUSB (due to the problems with grub, that's another story) and I don't have the option to make NTFS partitions. Is this something that wasn't incorporated in 10.04? Seems unlikely...

---

### Post by darkod on 2012-11-05
> **AliPM said:**
> I've virtually only been running Ubuntu from the LiveUSB (due to the problems with grub, that's another story) and I don't have the option to make NTFS partitions. Is this something that wasn't incorporated in 10.04? Seems unlikely...

It's there in 10.04. Are we talking about Gparted or the Disk Utility? I only ever use Gparted.

If I remember correctly, in 10.04 it was in System - Administration - Gparted.

Or in terminal you can call it with:
gksu gparted

---

### Post by AliPM on 2012-11-05
Yes, you were right, GParted has the option to make NTFS partitions. I made 2 - I'm  reinstalling XP now on the first one (gave it boot flag first, not sure if I needed to or not) and didn't reformat it with the XP installer.

Probably tomorrow I'll have a crack at installing 7, and then I can get on with fighting with GRUB2 again :) 

Thanks for your help everyone - might well be asking more questions in the near future.

---

### Post by darkod on 2012-11-05
Before installing win7 don't forget to turn off the boot flag on partition #1 and turn it on on #2. That way win7 will put the boot files on the same partition and it will not combine them with the ones from XP.

This will make it possible later when you install ubuntu to have all three OSs in the grub2 boot menu and boot any OS from only one menu. That would be impossible if windows combines the boot files.

So, moving the boot flag before the second windows install is very important.

---

### Post by AliPM on 2012-11-05
OK, I'll remember to do that. I still have Ubuntu installed on sda3 - I figured there wasn't much point getting rid of it when as far as I know it's a healthy OS.

When I install 7, is it important there is a boot flag ONLY on the partition I want to install to, or can/should there also be one on the Linux partition?

---

### Post by oldfred on 2012-11-05
Only one boot flag per drive.

Windows uses boot flag and needs it to know which partition to boot from, repair, or install into. Must be primary partition.

Grub does not use boot flag at all, but a few BIOS want to see a boot flag or you cannot even boot, so we usually suggest a boot flag on a primary partition.

---

### Post by AliPM on 2012-11-05
Aha, I see. That would explain why I couldn't get it to boot at all a couple of days ago then.

Are there any tools that can create something like a system restore point for the whole drive rather than just one partition? Once I've got the partitions and OSes up and running I'd like to save the state if possible. Ta

---

### Post by oldfred on 2012-11-05
I separate data from system primarily and do  not then backup system other than some settings. Full image back up is obsolete as soon as you start using system. And as a larger task we usually do not do it as often as we should. So I primarily just backup /home and my data.

discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

I might separately back up Windows using Windows tools.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by AliPM on 2012-11-06
Thanks for the advice, oldfred. Maybe I won't bother with backing up my system image. :)

I've got 7 installing now, so I'm looking forward to seeing what sort of boot menu I get when it's finished. Because I installed Ubuntu before either copy of Windows, I know that GRUB will have been overwritten - when I do the grub-install process, do I need to have boot flags on the XP, 7 and Linux partitions, or just Linux? Or does it not matter?

---

### Post by darkod on 2012-11-06
For grub the boot flag doesn't matter. Leave it on any of the windows partitions, for example on the win7 where it is now.

You will have to reinstall grub2 to the MBR and if you did the installs (moving the flag) right, it should present you with options for both XP and 7 after you boot ubuntu once and run:
sudo update-grub

It will need that command the detect the latest win7 installation.

---

### Post by AliPM on 2012-11-06
I reinstalled 7, had it running OK but without any boot menu on startup, then booted from the LiveUSB and ran Boot-Repair > Recommended Repair.

Now, I have almost the same problem as when I started this thread, in that when I turn on the laptop it doesn't boot anything, just goes in a cycle of splash screen - blank screen - splash screeen etc

Here is the BootInfo summary, maybe (please) someone can tell me what's gone wrong this time! I thought I was almost there this time. Please ignore sdc, that's the flashdrive I booted 7 from, which I also used to transfer the bootinfo summary on.

```


    Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info October 25th 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 3 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.63 Debian-2008-07-15
    Boot sector info:  Syslinux looks at sector 7892 of /dev/sdb1 for its 
                       second stage. According to the info in the boot 
                       sector, sdb1 starts at sector 0. But according to the 
                       info from fdisk, sdb1 starts at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /bootmgr /boot/bcd 
                       /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   143,364,059   143,363,997   7 NTFS / exFAT / HPFS
/dev/sda2    *    143,364,060   307,210,994   163,846,935   7 NTFS / exFAT / HPFS
/dev/sda3         307,212,288   356,038,655    48,826,368  83 Linux
/dev/sda4         356,038,656   363,851,775     7,813,120  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2063 MB, 2063073280 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4029440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62     4,027,519     4,027,458   c W95 FAT32 (LBA)


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63    31,262,489    31,262,427  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       3cc0ecd6-bccb-4154-945c-8db8b80527f7   ext3       
/dev/sda1        48A992267DACA528                       ntfs       XP
/dev/sda2        003138DA1138E2E6                       ntfs       Win7
/dev/sda3        a392a60c-0ca5-41d1-94e7-1fb7bfdd28e3   ext4       
/dev/sda4        8dd2e21b-4469-43c0-9f2b-99bf7656c42c   swap       
/dev/sdb1        75D6-B625                              vfat       
/dev/sdc1        4663E6A1035B074D                       ntfs       Windows USB

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdc1        /media/Windows USB       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[Boot Loader]
Timeout=30
Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="Windows 7 (loader) (on /dev/sda2)"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set a392a60c-0ca5-41d1-94e7-1fb7bfdd28e3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,3)'
search --no-floppy --fs-uuid --set a392a60c-0ca5-41d1-94e7-1fb7bfdd28e3
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a392a60c-0ca5-41d1-94e7-1fb7bfdd28e3
    linux    /boot/vmlinuz-2.6.32-38-generic root=UUID=a392a60c-0ca5-41d1-94e7-1fb7bfdd28e3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-38-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a392a60c-0ca5-41d1-94e7-1fb7bfdd28e3
    echo    'Loading Linux 2.6.32-38-generic ...'
    linux    /boot/vmlinuz-2.6.32-38-generic root=UUID=a392a60c-0ca5-41d1-94e7-1fb7bfdd28e3 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-38-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a392a60c-0ca5-41d1-94e7-1fb7bfdd28e3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a392a60c-0ca5-41d1-94e7-1fb7bfdd28e3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 48A992267DACA528
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 003138DA1138E2E6
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a392a60c-0ca5-41d1-94e7-1fb7bfdd28e3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=8dd2e21b-4469-43c0-9f2b-99bf7656c42c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 154.619625092 = 166.021558272  boot/grub/core.img                             1
 154.619628906 = 166.021562368  boot/grub/grub.cfg                             1
 154.873039246 = 166.293659648  boot/initrd.img-2.6.32-38-generic              1
 154.801074982 = 166.216388608  boot/vmlinuz-2.6.32-38-generic                 1
 154.873039246 = 166.293659648  initrd.img                                     1
 154.801074982 = 166.216388608  vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/vesamenu.c32              :  COM32R module (v3.xx)

=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
echo '------------------------------------'
echo '|      Windows USB - Loading...    |'
echo '------------------------------------'
insmod ntfs
search --no-floppy --fs-uuid 4663E6A1035B074D --set root
chainloader +1
boot
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             0


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-11-06__22h51 ===================
boot-repair version : 3.194~ppa50~lucid
boot-sav version : 3.194~ppa50~lucid
glade2script-gtk2 version : 3.2.2~ppa45~lucid
boot-sav-extra version :
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
boot-repair is executed in live-session (Ubuntu 10.04.4 LTS, lucid, Ubuntu, x86_64)
CPU op-mode(s):        64-bit
BOOT_IMAGE=/casper/vmlinuz noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity

=================== os-prober:
/dev/sda1:Windows NT/2000/XP:Windows:chain
/dev/sda2:Windows 7 (loader):Windows1:chain
/dev/sda3:Ubuntu 10.04.4 LTS (10.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="3cc0ecd6-bccb-4154-945c-8db8b80527f7" TYPE="ext3"
/dev/sda1: LABEL="XP" UUID="48A992267DACA528" TYPE="ntfs"
/dev/sda2: LABEL="Win7" UUID="003138DA1138E2E6" TYPE="ntfs"
/dev/sda3: UUID="a392a60c-0ca5-41d1-94e7-1fb7bfdd28e3" TYPE="ext4"
/dev/sda4: UUID="8dd2e21b-4469-43c0-9f2b-99bf7656c42c" TYPE="swap"
/dev/sdb1: UUID="75D6-B625" TYPE="vfat"


1 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.



=================== sda3/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== sda3/etc/grub.d/ :
drwxr-xr-x  2 root    root     4096 2012-02-14 11:47 grub.d
total 40
-rwxr-xr-x 1 root root 4444 2012-01-20 15:56 00_header
-rwxr-xr-x 1 root root 1416 2012-01-20 15:34 05_debian_theme
-rwxr-xr-x 1 root root 4843 2012-01-20 15:56 10_linux
-rwxr-xr-x 1 root root  918 2010-03-23 10:40 20_memtest86+
-rwxr-xr-x 1 root root 6605 2012-01-20 15:56 30_os-prober
-rwxr-xr-x 1 root root  214 2012-01-20 15:56 40_custom
-rw-r--r-- 1 root root  483 2012-01-20 15:56 README


=================== UEFI/Legacy mode :
EFI in dmesg. Please report this message to yannubuntu@gmail.com
This live-session is not EFI-compatible.
[    0.000000] ACPI: UEFI 0000000066404000 0003E (v01 LENOVO CB-01    00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 0000000066403000 00042 (v01 PTL      COMBUF 00000001 PTL  00000001)
[    0.000000] ACPI: UEFI 00000000663ff000 00116 (v01 LENOVO CB-01    00000001 PTL  00000001)


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda3.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA HITACHI HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
1      32.3kB  73.4GB  73.4GB  primary  ntfs
2      73.4GB  157GB   83.9GB  primary  ntfs            boot
3      157GB   182GB   25.0GB  primary  ext4
4      182GB   186GB   4000MB  primary  linux-swap(v1)


Model: Samsung Mighty Drive (scsi)
Disk /dev/sdb: 2063MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      31.7kB  2062MB  2062MB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:320GB:scsi:512:512:msdos:ATA HITACHI HTS54323;
1:32.3kB:73.4GB:73.4GB:ntfs::;
2:73.4GB:157GB:83.9GB:ntfs::boot;
3:157GB:182GB:25.0GB:ext4::;
4:182GB:186GB:4000MB:linux-swap(v1)::;

BYT;
/dev/sdb:2063MB:scsi:512:512:msdos:Samsung Mighty Drive;
1:31.7kB:2062MB:2062MB:fat32::boot, lba;


=================== mount:
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/dev (filtered):  audio1 block bsg btrfs-control bus char console core cpu_dma_latency disk dsp1 ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mem mixer mixer1 net network_latency network_throughput null oldmem pktcdvd port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sdb sdb1 sequencer sequencer2 sg0 sg1 shm snapshot snd sndstat stderr stdin stdout urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 v4l vga_arbiter video0 zero
ls /dev/mapper:  control
ls /mnt/boot-sav/sda1: WINDOWS Information Volume System RECYCLER $RECYCLE.BIN Files Program pagefile.sys ntldr NTDETECT.COM MSDOS.SYS IO.SYS hiberfil.sys Drivers Settings and Documents CONFIG.SYS boot-sav boot.ini AUTOEXEC.BAT
ls /mnt/boot-sav/sda2: Windows Users Information Volume System $Recycle.Bin Recovery (x86) Files Program Files Program ProgramData PerfLogs pagefile.sys hiberfil.sys FTZSK Drivers Settings and Documents BOOTSECT.BAK boot-sav bootmgr Boot

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    646M  118M  496M  20% /
none      devtmpfs    799M  308K  798M   1% /dev
/dev/sdb1     vfat    2.0G  1.4G  611M  69% /cdrom
/dev/loop0
squashfs    665M  665M     0 100% /rofs
none         tmpfs    804M  100K  804M   1% /dev/shm
tmpfs        tmpfs    804M   16K  804M   1% /tmp
none         tmpfs    804M   80K  804M   1% /var/run
none         tmpfs    804M  4.0K  804M   1% /var/lock
none         tmpfs    804M     0  804M   0% /lib/init/rw
/dev/sda1  fuseblk     69G  7.3G   62G  11% /mnt/boot-sav/sda1
/dev/sda2  fuseblk     79G   16G   64G  20% /mnt/boot-sav/sda2
/dev/sda3     ext4     23G  2.2G   20G  10% /mnt/boot-sav/sda3

=================== fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088c4b

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8924    71681998+   7  HPFS/NTFS
/dev/sda2   *        8925       19123    81923467+   7  HPFS/NTFS
/dev/sda3           19124       22163    24413184   83  Linux
/dev/sda4           22163       22649     3906560   82  Linux swap / Solaris

Disk /dev/sdb: 2063 MB, 2063073280 bytes
64 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002378f

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1015     2013729    c  W95 FAT32 (LBA)


Warning: unknown mime-type for "/mnt/boot-sav/sda3/etc/default/grub" -- using "application/octet-stream"
Error: no "view" mailcap rules found for type "application/octet-stream"

=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sda3 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Custom-Repair
This setting will reinstall the grub2 of sda3 into the MBR of sda, using the following options:      disable-internet-check set-windows-as-default
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 2
mount: special device /run does not exist
grub-install (GNU GRUB 1.98-1ubuntu13),grub-install (GNU GRUB 1.

Reinstall the GRUB of sda3 into the MBR of sda
grub-install /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0

chroot /mnt/boot-sav/sda3 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /media/Windows USB: No such file or directory
ls: cannot access /media/Windows USB: No such file or directory
ls: cannot access /media/Windows USB: No such file or directory
ls: cannot access /media/Windows USB: No such file or directory
Found Windows NT/2000/XP on /dev/sda1
Found Windows 7 (loader) on /dev/sda2

Set Windows 7 (loader) (on /dev/sda2) as default entry

chroot /mnt/boot-sav/sda3 update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-38-generic
Found initrd image: /boot/initrd.img-2.6.32-38-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /casper-rw-backing: No such file or directory
ls: cannot access /media/Windows USB: No such file or directory
ls: cannot access /media/Windows USB: No such file or directory
ls: cannot access /media/Windows USB: No such file or directory
ls: cannot access /media/Windows USB: No such file or directory
Found Windows NT/2000/XP on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
umount: /mnt/boot-sav/sda3/run: not mounted
Unhide GRUB boot menu in sda3/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.

pastebinit  packages needed
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2  Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: Package pastebinit has no installation candidate
Could not install pastebinit
Please install the [pastebinit ] packages.  Then try again.



```

Please note I cannot install pastebinit images because I can't get wireless working booting from the Live USB, and plugging an ethernet cable in doesn't seem to work either. If anyone could tell me how to download the relevant files and copy them via flash disk that would be great, if that will indeed fix the problem.

Thanks in advance once again

---

### Post by AliPM on 2012-11-06
Also, when i run

sudo grub-update

from the Live USB I get this error message:

/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)

---

### Post by darkod on 2012-11-06
You can't run update-grub from live mode. I said once you boot ubuntu to do it.

So, right now it doesn't even show the grub2 boot menu, right?

PS. I don't see anything wrong, except maybe the ubuntu boot files distance from the start of the disk. But in that case usually it doesn't switch between splash screen and blank screen. That sounds more like a video issue.

---

### Post by AliPM on 2012-11-06
My first thought was that you  meant run "sudo update-grub" from inside an installed version of Ubuntu, but since my problem *is* booting my installed version of Ubuntu, I tried it anyway. How else would you suggest I boot into Ubuntu?

What sort of video issues could this be, and how could they be resolved? I've run all the OSes on this machine fine in the past.

Does boot-repair require internet access to work properly, or is that just for the pastebinit part?

I really don't know why an ethernet cable doesn't give me an internet connection, but that is unfortunately the case.

---

### Post by AliPM on 2012-11-06
Just tried mounting sda3, then running

sudo grub-install --root-directory=/mnt /dev/sda

as suggested by another site. Result was 'Installation complete. No error reported' but seems to have made no difference to the boot process.

---

### Post by AliPM on 2012-11-06
Used boot-repair to restore the MBR, so at least now I can boot into Win7.

This reassures me that boot-repair does actually work without an internet connection, so I'm wondering about re-installing Linux AGAIN on sda3. I don't see why this should be necessary, though! Getting thoroughly confused and frustrated here :mad:

---

### Post by oldfred on 2012-11-06
When you use liveCD do you not get Ethernet either? Always best to install with wired Ethernet as then it can download extra drivers that you may need. Often need drivers for wireless and video.

If not getting video at grub menu, use boot repair to change gfxmode=640x480. By default it is commented out, so you use systems video mode. But if system video not working changing to gfxmode works. 

Then if you get menu try this:

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

At grub menu press e for edit and on linux line change splash quiet to nomodeset and see if you get anything more.

---

### Post by AliPM on 2012-11-07
Wired ethernet doesn't work in my LiveUSB environment, but it did work at one point because I managed to install boot-repair. I have no idea what changed to make it stop working, I wasn't aware that I had changed anything.

I ran Boot-repair and ticked 'uncomment GRUB_GFXMODE', but I didn't get any option to set the GFXMODE to 640*480, or indeed to anything. Is this something I need to set manually? Changing it and rebooting it didn't have any effect.

Also, running Boot-repair and ticking 'Add a kernel option: nomodeset' had no discernible effect.

Could it make any difference that I still have a boot flag on sda2?

Could it help if I installed the bootloader in sda3 instead of sda?

---

### Post by oldfred on 2012-11-07
Grub does not use boot flag. Windows would need boot flag on sda2 to boot Windows 7 directly or on sda1 to boot XP directly. 

Grub has to be installed to sda, not to any partition unless you are using another copy of grub or some other boot loader  to boot.

Unticking the gfxmode will default to 640x480. If that worked you then could reset to your screen size or back to using the installed video driver.

If you hold shift key down from BIOS boot screen at startup do you get grub menu?

---

### Post by AliPM on 2012-11-07
No, holding Shift down has no effect.

When say 'unticking gfxmode', do you mean 'ticking Uncomment grub_gfxmode'? I can try that again, but it didn't work before.

This forum post seems to suggest I may not be the only one with this problem:

[http://forums.lenovo.com/t5/IdeaPad-S-series-Netbooks/S205-Bios-Linux-compatible-when/td-p/563823](http://forums.lenovo.com/t5/IdeaPad-S-series-Netbooks/S205-Bios-Linux-compatible-when/td-p/563823)

---

### Post by oldfred on 2012-11-07
See this thread. Just use newer version.

How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS](https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)

Sorry, I missed that you had the S205 and there are details in above links.

---

### Post by AliPM on 2012-11-07
Hey, no need to apologise! The advice has been hugely appreciated.

The links  do seem to indicate that I will have to use UEFI boot partitions - does that mean that XP is totally out of the question?

---

### Post by oldfred on 2012-11-07
XP does not work with gpt at all. Even Windows 7 will only boot from gpt with UEFI, but 7 will read gpt on another drive where XP will not.

---

### Post by AliPM on 2012-11-08
So now I'm back to where I started with the EFI partitioning process. Ah well, at least now I know that I have to do it with EFI if I want to dual-boot (this is how I understand it at the moment anyway).
 
The only reason I've been so keen to keep XP is that my S205 only has 2GB ram, and although I've bought another 2gb module, to install it in the laptop you have to take the whole back panel off. I tried doing this and one of Lenovo's crappy screws got stripped in the process, so until I find a way of taking the screw out and replacing it (they don't do spares) I'm stuck with 2gb. Running 7 with only 2gb seems to drain the battery quite a lot.

---

### Post by AliPM on 2012-11-09
I'm getting ready to have another go at a reinstall, and I have a couple of questions. @oldfred, when you say that

> **oldfred said:**
> But if using gpt with Linux only, as Windows only boots from gpt partitioned drives with UEFI, you need a bios_grub partition. The bios grub can be anywhere on drive. Efi partition is suppose to be first.

does that mean that if I want to dual-boot I don't need a bios_grub partition? I'm a tad confused because later in the same post, you said that I would need

> **oldfred said:**
>  250 MB efi FAT32 (for UEFI boot or future use for UEFI)
1 MB bios_grub no format (for BIOS boot)

Does this mean I need both, or just one? Will it cause any problems if I have a bios_grub partition, even if I want to dual-boot?


Because you said that 

> **oldfred said:**
>  Also 10.04 was not efi compatible, but I did use gpt partitioning and BIOS boot with a bios_grub partition without issue

I think I will play safe and use 12.04. Maybe I will just use the 32-bit version until I get the other 2gb ram installed somehow. It wouldn't be an issue uninstalling 32-bit and installing 64-bit, would it? Could I even have both installed side-by-side to test the difference?

I would do all the disk partitioning from the LiveUSB in advance of installing Win7, does that seem sensible?

---

### Post by oldfred on 2012-11-09
It depends on whether you are installing Windows and which mode, UEFI or BIOS. With Windows you can only have gpt partitioning if booting in UEFI mode, and Ubuntu only installs in UEFI mode with the 64 bit version.

If you are using BIOS and installing Windows you have to use MBR partitioning. Only if BIOS mode and just Ubuntu can you either gpt or MBR.

You can install 32bit & 64 bit side by side if you have 10 to 25GB for another / (root) partition. With 2GB you can run 64bit, I have it in my 6 year old laptop with only 1.5GB  of RAM. That may be too little but it works. Some say somewhere between 2 & 3GB is break point between 32bit & 64 bit, but if adding memory I would definitely use 64 bit.

A bios_grub partition or efi partition only applies to gpt partitioned drives. If booting with UEFI you have to have gpt partitioning & an efi partition first. Only grub needs a bios_grub in BIOS mode with a gpt partitioned drive, but then you cannot boot Windows.

---

### Post by AliPM on 2012-11-10
I installed 12.04 32-bit without reformatting the disk (still in MBR), and it now boots up fine, GRUB shows XP and 7 and they all work.

One thing though - 12.04 seems pretty slow compared to win 7. Is this a common problem?

---

### Post by oldfred on 2012-11-10
It should not be slow.

What video card/chip is it and is that configured correctly. It may just be using a default driver.

Is some process running continuously?
Use this in terminal, (q to exit) to see what is running.  
top

---

### Post by AliPM on 2012-11-17
It's an AMD Fusion E300 model. Doing a full update of Ubuntu and downloading the proprietary graphics drivers seemed to help.

Pretty happy with the setup at the moment, but I wondered: does installing OSes in UEFI mode actually improve performance? I might yet do another full dual boot install if it was worth it.

---

### Post by oldfred on 2012-11-18
UEFI should just be booting, so you should not have any difference once running system whether Windows or Ubuntu.
Unless one or the other includes some BIOS settings that the other does not??

---

