---
title: "Crash during upgrade to 10.10, won't boot."
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by Hamishfox on 2010-10-15
Hi,

I was in the middle of upgrading from 10.04 to 10.10 when the install froze with 25 minutes to go. I restarted, and now ubuntu won't get past the loading screen.

So I made a live usb, which I am currently running from, and found [this thread]("http://ubuntuforums.org/showthread.php?t=1593160"), where someone had solved a similar problem. I tried following his instructions, but hit a few roadblocks, which you can read about in that (short) thread if you desire.

long story short, here's the printout from this [bootscript]("http://bootinfoscript.sourceforge.net/") by meierfra:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 6515079 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   957,104,504   957,104,442  83 Linux
/dev/sda2         957,104,505   976,768,064    19,663,560   5 Extended
/dev/sda5         957,104,568   976,768,064    19,663,497  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1   488,397,167   488,397,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1              34   488,397,134   488,397,101 Linux or Data

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 3984 MB, 3984064512 bytes
146 heads, 24 sectors/track, 2220 cylinders, total 7781376 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *            216     7,781,375     7,781,160   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4fa54ca6-b961-4386-8897-9ce22220994e   ext4       Posey                         
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6fe5372e-bb2e-44b2-a6bc-5857d25e5baa   ext4       Frank                         
/dev/sdb: PTTYPE="gpt" 
/dev/sdc1        DC6A-17B7                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Frank             ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/Posey             ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
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
search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
set locale_dir=($root)/boot/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=4fa54ca6-b961-4386-8897-9ce22220994e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=4fa54ca6-b961-4386-8897-9ce22220994e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4fa54ca6-b961-4386-8897-9ce22220994e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=4fa54ca6-b961-4386-8897-9ce22220994e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=4fa54ca6-b961-4386-8897-9ce22220994e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=4fa54ca6-b961-4386-8897-9ce22220994e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=4fa54ca6-b961-4386-8897-9ce22220994e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=4fa54ca6-b961-4386-8897-9ce22220994e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=4fa54ca6-b961-4386-8897-9ce22220994e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=4fa54ca6-b961-4386-8897-9ce22220994e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 4fa54ca6-b961-4386-8897-9ce22220994e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4fa54ca6-b961-4386-8897-9ce22220994e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=8c74721f-54b6-48d7-8bae-8cc811520352 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sda1: Location of files loaded by Grub: ===================


   3.4GB: boot/grub/core.img
   2.9GB: boot/grub/grub.cfg
  74.2GB: boot/initrd.img-2.6.32-21-generic
  32.2GB: boot/initrd.img-2.6.32-22-generic
  53.7GB: boot/initrd.img-2.6.32-23-generic
  51.6GB: boot/initrd.img-2.6.32-24-generic
 383.7GB: boot/initrd.img-2.6.32-25-generic
   3.3GB: boot/vmlinuz-2.6.32-21-generic
  10.7GB: boot/vmlinuz-2.6.32-22-generic
  10.8GB: boot/vmlinuz-2.6.32-23-generic
  25.8GB: boot/vmlinuz-2.6.32-24-generic
  25.8GB: boot/vmlinuz-2.6.32-25-generic
  55.8GB: boot/vmlinuz-2.6.35-22-generic
 383.7GB: initrd.img
  51.6GB: initrd.img.old
  25.8GB: vmlinuz
  25.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 c2 04  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 d8 00 00 00  |........?.......|
00000020  28 bb 76 00 9f 1d 00 00  00 00 00 00 02 00 00 00  |(.v.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b7 17 6a dc 4e  4f 20 4e 41 4d 45 20 20  |..)..j.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 e0 e7 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```Please let me know if there's any additional information I could provide that might help you to help me. It's been several days since I broke her and I'm starting to miss her warm, glowing embrace. :(

---

### Post by Hamishfox on 2010-10-15
So I tried some of the suggestions found in [this thread]("http://ubuntuforums.org/showthread.php?t=1596901"). 

When I inputted 

```
sudo apt-get -f install
```it returned some nonsense about being broken, and it told me it would fix it if I did this:

```
sudo dpkg --configure -a
```So I did that, whatever it was, and a bunch of "installing such-and-such" and "setting up whatzits" wizzed past faster then I could read. This went on for a while. Eventually it gave me the command prompt back, so I tried the first command again. It worked. then I did

```
startx
```Now I'm stuck. It said a bunch of things like "FATAL: Module nvidia not found" "No drivers available" "fatal server error: no screens found" and told me to view the log at /var/log/xorg.0.log for more errors.

This is Xorg/0/log

```
[    75.618] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    75.618] X Protocol Version 11, Revision 0
[    75.618] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    75.618] Current Operating System: Linux ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[    75.618] Kernel command line: noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz splash -- maybe-ubiquity
[    75.618] Build Date: 16 September 2010  05:39:22PM
[    75.618] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[    75.618] Current version of pixman: 0.18.4
[    75.618]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    75.618] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    75.618] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 15 13:14:46 2010
[    75.618] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    75.618] (==) No Layout section.  Using the first Screen section.
[    75.618] (==) No screen section available. Using defaults.
[    75.618] (**) |-->Screen "Default Screen Section" (0)
[    75.618] (**) |   |-->Monitor "<default monitor>"
[    75.618] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    75.619] (==) Automatically adding devices
[    75.619] (==) Automatically enabling devices
[    75.619] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    75.619]     Entry deleted from font path.
[    75.619] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    75.619] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    75.619] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    75.619] (II) Loader magic: 0x81f8e00
[    75.619] (II) Module ABI versions:
[    75.619]     X.Org ANSI C Emulation: 0.4
[    75.619]     X.Org Video Driver: 8.0
[    75.619]     X.Org XInput driver : 11.0
[    75.619]     X.Org Server Extension : 4.0
[    75.620] (--) PCI:*(0:1:0:0) 10de:0615:1682:2601 rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    75.620] (II) Open ACPI successful (/var/run/acpid.socket)
[    75.620] (II) LoadModule: "extmod"
[    75.621] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    75.621] (II) Module extmod: vendor="X.Org Foundation"
[    75.621]     compiled for 1.9.0, module version = 1.0.0
[    75.621]     Module class: X.Org Server Extension
[    75.621]     ABI class: X.Org Server Extension, version 4.0
[    75.621] (II) Loading extension MIT-SCREEN-SAVER
[    75.621] (II) Loading extension XFree86-VidModeExtension
[    75.621] (II) Loading extension XFree86-DGA
[    75.621] (II) Loading extension DPMS
[    75.621] (II) Loading extension XVideo
[    75.621] (II) Loading extension XVideo-MotionCompensation
[    75.621] (II) Loading extension X-Resource
[    75.621] (II) LoadModule: "dbe"
[    75.621] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    75.621] (II) Module dbe: vendor="X.Org Foundation"
[    75.621]     compiled for 1.9.0, module version = 1.0.0
[    75.621]     Module class: X.Org Server Extension
[    75.621]     ABI class: X.Org Server Extension, version 4.0
[    75.621] (II) Loading extension DOUBLE-BUFFER
[    75.621] (II) LoadModule: "glx"
[    75.622] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    75.622] (II) Module glx: vendor="X.Org Foundation"
[    75.622]     compiled for 1.9.0, module version = 1.0.0
[    75.622]     ABI class: X.Org Server Extension, version 4.0
[    75.622] (==) AIGLX enabled
[    75.622] (II) Loading extension GLX
[    75.622] (II) LoadModule: "record"
[    75.622] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    75.622] (II) Module record: vendor="X.Org Foundation"
[    75.622]     compiled for 1.9.0, module version = 1.13.0
[    75.622]     Module class: X.Org Server Extension
[    75.622]     ABI class: X.Org Server Extension, version 4.0
[    75.622] (II) Loading extension RECORD
[    75.622] (II) LoadModule: "dri"
[    75.623] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    75.623] (II) Module dri: vendor="X.Org Foundation"
[    75.623]     compiled for 1.9.0, module version = 1.0.0
[    75.623]     ABI class: X.Org Server Extension, version 4.0
[    75.623] (II) Loading extension XFree86-DRI
[    75.623] (II) LoadModule: "dri2"
[    75.623] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    75.623] (II) Module dri2: vendor="X.Org Foundation"
[    75.623]     compiled for 1.9.0, module version = 1.2.0
[    75.623]     ABI class: X.Org Server Extension, version 4.0
[    75.623] (II) Loading extension DRI2
[    75.623] (==) Matched nouveau as autoconfigured driver 0
[    75.623] (==) Matched nv as autoconfigured driver 1
[    75.623] (==) Matched vesa as autoconfigured driver 2
[    75.623] (==) Matched fbdev as autoconfigured driver 3
[    75.623] (==) Assigned the driver to the xf86ConfigLayout
[    75.623] (II) LoadModule: "nouveau"
[    75.623] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    75.624] (II) Module nouveau: vendor="X.Org Foundation"
[    75.624]     compiled for 1.8.99.905, module version = 0.0.16
[    75.624]     Module class: X.Org Video Driver
[    75.624]     ABI class: X.Org Video Driver, version 8.0
[    75.624] (II) LoadModule: "nv"
[    75.624] (II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
[    75.624] (II) Module nv: vendor="X.Org Foundation"
[    75.624]     compiled for 1.8.99.905, module version = 2.1.17
[    75.624]     Module class: X.Org Video Driver
[    75.624]     ABI class: X.Org Video Driver, version 8.0
[    75.624] (II) LoadModule: "vesa"
[    75.624] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    75.624] (II) Module vesa: vendor="X.Org Foundation"
[    75.624]     compiled for 1.8.99.905, module version = 2.3.0
[    75.624]     Module class: X.Org Video Driver
[    75.624]     ABI class: X.Org Video Driver, version 8.0
[    75.624] (II) LoadModule: "fbdev"
[    75.625] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    75.625] (II) Module fbdev: vendor="X.Org Foundation"
[    75.625]     compiled for 1.8.99.905, module version = 0.4.2
[    75.625]     ABI class: X.Org Video Driver, version 8.0
[    75.625] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[    75.625] (II) NOUVEAU driver for NVIDIA chipset families :
[    75.625]     RIVA TNT    (NV04)
[    75.625]     RIVA TNT2   (NV05)
[    75.625]     GeForce 256 (NV10)
[    75.625]     GeForce 2   (NV11, NV15)
[    75.625]     GeForce 4MX (NV17, NV18)
[    75.625]     GeForce 3   (NV20)
[    75.625]     GeForce 4Ti (NV25, NV28)
[    75.625]     GeForce FX  (NV3x)
[    75.625]     GeForce 6   (NV4x)
[    75.625]     GeForce 7   (G7x)
[    75.625]     GeForce 8   (G8x)
[    75.625] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[    75.625] (II) NOUVEAU driver for NVIDIA chipset families :
[    75.625]     RIVA TNT    (NV04)
[    75.625]     RIVA TNT2   (NV05)
[    75.625]     GeForce 256 (NV10)
[    75.625]     GeForce 2   (NV11, NV15)
[    75.625]     GeForce 4MX (NV17, NV18)
[    75.625]     GeForce 3   (NV20)
[    75.625]     GeForce 4Ti (NV25, NV28)
[    75.625]     GeForce FX  (NV3x)
[    75.625]     GeForce 6   (NV4x)
[    75.625]     GeForce 7   (G7x)
[    75.625]     GeForce 8   (G8x)
[    75.625] (II) VESA: driver for VESA chipsets: vesa
[    75.625] (II) FBDEV: driver for framebuffer: fbdev
[    75.625] (++) using VT number 7

[    75.625] drmOpenDevice: node name is /dev/dri/card0
[    75.625] drmOpenDevice: open result is 8, (OK)
[    75.625] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    75.625] drmOpenDevice: node name is /dev/dri/card0
[    75.625] drmOpenDevice: open result is 8, (OK)
[    75.625] drmOpenByBusid: drmOpenMinor returns 8
[    75.625] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    75.625] (II) [drm] nouveau interface version: 0.0.16
[    75.625] (WW) Falling back to old probe method for vesa
[    75.625] (WW) Falling back to old probe method for fbdev
[    75.625] (II) Loading sub module "fbdevhw"
[    75.625] (II) LoadModule: "fbdevhw"
[    75.626] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    75.626] (II) Module fbdevhw: vendor="X.Org Foundation"
[    75.626]     compiled for 1.9.0, module version = 0.0.2
[    75.626]     ABI class: X.Org Video Driver, version 8.0
[    75.626] (II) Loading sub module "dri"
[    75.626] (II) LoadModule: "dri"
[    75.626] (II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
[    75.626] (II) NOUVEAU(0): Loaded DRI module
[    75.626] drmOpenDevice: node name is /dev/dri/card0
[    75.626] drmOpenDevice: open result is 9, (OK)
[    75.626] drmOpenDevice: node name is /dev/dri/card0
[    75.626] drmOpenDevice: open result is 9, (OK)
[    75.626] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[    75.626] drmOpenDevice: node name is /dev/dri/card0
[    75.626] drmOpenDevice: open result is 9, (OK)
[    75.626] drmOpenByBusid: drmOpenMinor returns 9
[    75.626] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    75.626] (II) [drm] DRM interface version 1.3
[    75.626] (II) [drm] DRM open master succeeded.
[    75.627] (--) NOUVEAU(0): Chipset: "NVIDIA NV92"
[    75.627] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    75.627] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    75.627] (==) NOUVEAU(0): RGB weight 888
[    75.627] (==) NOUVEAU(0): Default visual is TrueColor
[    75.627] (==) NOUVEAU(0): Using HW cursor
[    75.777] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[    76.065] (II) NOUVEAU(0): Output DVI-I-2 has no monitor section
[    76.215] (II) NOUVEAU(0): EDID for output DVI-I-1
[    76.504] (II) NOUVEAU(0): EDID for output DVI-I-2
[    76.504] (II) NOUVEAU(0): Manufacturer: SAM  Model: 56a  Serial#: 1313091637
[    76.504] (II) NOUVEAU(0): Year: 2010  Week: 20
[    76.504] (II) NOUVEAU(0): EDID Version: 1.3
[    76.504] (II) NOUVEAU(0): Digital Display Input
[    76.504] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    76.504] (II) NOUVEAU(0): Gamma: 2.20
[    76.504] (II) NOUVEAU(0): DPMS capabilities: Off
[    76.504] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    76.504] (II) NOUVEAU(0): First detailed timing is preferred mode
[    76.504] (II) NOUVEAU(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[    76.504] (II) NOUVEAU(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
[    76.504] (II) NOUVEAU(0): Supported established timings:
[    76.504] (II) NOUVEAU(0): 720x400@70Hz
[    76.504] (II) NOUVEAU(0): 640x480@60Hz
[    76.504] (II) NOUVEAU(0): 640x480@67Hz
[    76.504] (II) NOUVEAU(0): 640x480@72Hz
[    76.504] (II) NOUVEAU(0): 640x480@75Hz
[    76.504] (II) NOUVEAU(0): 800x600@56Hz
[    76.504] (II) NOUVEAU(0): 800x600@60Hz
[    76.504] (II) NOUVEAU(0): 800x600@72Hz
[    76.504] (II) NOUVEAU(0): 800x600@75Hz
[    76.504] (II) NOUVEAU(0): 832x624@75Hz
[    76.504] (II) NOUVEAU(0): 1024x768@60Hz
[    76.504] (II) NOUVEAU(0): 1024x768@70Hz
[    76.504] (II) NOUVEAU(0): 1024x768@75Hz
[    76.504] (II) NOUVEAU(0): 1280x1024@75Hz
[    76.504] (II) NOUVEAU(0): 1152x864@75Hz
[    76.504] (II) NOUVEAU(0): Manufacturer's mask: 0
[    76.504] (II) NOUVEAU(0): Supported standard timings:
[    76.504] (II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    76.504] (II) NOUVEAU(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    76.504] (II) NOUVEAU(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    76.504] (II) NOUVEAU(0): #3: hsize: 1280  vsize 800  refresh: 60  vid: 129
[    76.504] (II) NOUVEAU(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    76.504] (II) NOUVEAU(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    76.504] (II) NOUVEAU(0): Supported detailed timing:
[    76.504] (II) NOUVEAU(0): clock: 119.0 MHz   Image Size:  459 x 296 mm
[    76.504] (II) NOUVEAU(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    76.504] (II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    76.504] (II) NOUVEAU(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 155 MHz
[    76.504] (II) NOUVEAU(0): Monitor name: SyncMaster
[    76.504] (II) NOUVEAU(0): Serial No: HVGZ502607
[    76.504] (II) NOUVEAU(0): Supported detailed timing:
[    76.504] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  459 x 296 mm
[    76.504] (II) NOUVEAU(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    76.504] (II) NOUVEAU(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    76.504] (II) NOUVEAU(0): Supported detailed timing:
[    76.504] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  459 x 296 mm
[    76.504] (II) NOUVEAU(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    76.504] (II) NOUVEAU(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    76.504] (II) NOUVEAU(0): Supported detailed timing:
[    76.504] (II) NOUVEAU(0): clock: 27.0 MHz   Image Size:  459 x 296 mm
[    76.504] (II) NOUVEAU(0): h_active: 720  h_sync: 732  h_sync_end 796 h_blank_end 864 h_border: 0
[    76.504] (II) NOUVEAU(0): v_active: 576  v_sync: 581  v_sync_end 586 v_blanking: 625 v_border: 0
[    76.504] (II) NOUVEAU(0): Supported detailed timing:
[    76.504] (II) NOUVEAU(0): clock: 27.0 MHz   Image Size:  459 x 296 mm
[    76.504] (II) NOUVEAU(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    76.504] (II) NOUVEAU(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    76.504] (II) NOUVEAU(0): Number of EDID sections to follow: 1
[    76.504] (II) NOUVEAU(0): EDID (in hex):
[    76.504] (II) NOUVEAU(0):     00ffffffffffff004c2d6a053530444e
[    76.504] (II) NOUVEAU(0):     14140103802f1e782aee91a3544c9926
[    76.504] (II) NOUVEAU(0):     0f5054bfef8081808140714f81009500
[    76.504] (II) NOUVEAU(0):     950f010101017c2e90a0601a1e403020
[    76.504] (II) NOUVEAU(0):     3600cb281100001a000000fd00384b1e
[    76.504] (II) NOUVEAU(0):     510f000a202020202020000000fc0053
[    76.504] (II) NOUVEAU(0):     796e634d61737465720a2020000000ff
[    76.504] (II) NOUVEAU(0):     004856475a3530323630370a202001c0
[    76.504] (II) NOUVEAU(0): Printing probed modes for output DVI-I-2
[    76.504] (II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    76.504] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    76.505] (II) NOUVEAU(0): Output DVI-I-1 disconnected
[    76.505] (II) NOUVEAU(0): Output DVI-I-2 connected
[    76.505] (II) NOUVEAU(0): Using exact sizes for initial modes
[    76.505] (II) NOUVEAU(0): Output DVI-I-2 using initial mode 1680x1050
[    76.505] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    76.505] (--) NOUVEAU(0): Virtual size is 1680x1050 (pitch 1680)
[    76.505] (**) NOUVEAU(0):  Driver mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "1440x900": 136.8 MHz (scaled from 0.0 MHz), 70.6 kHz, 75.0 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "1280x800": 83.5 MHz (scaled from 0.0 MHz), 49.7 kHz, 59.8 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 37.5 kHz, 50.0 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "1280x720": 74.2 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    76.505] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
[    76.505] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
[    76.505] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[    76.505] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    76.505] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[    76.505] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "720x576": 27.0 MHz (scaled from 0.0 MHz), 31.2 kHz, 50.0 Hz
[    76.505] (II) NOUVEAU(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "720x480": 27.0 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[    76.505] (II) NOUVEAU(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
[    76.505] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[    76.505] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
[    76.505] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    76.505] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    76.505] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[    76.505] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    76.505] (==) NOUVEAU(0): DPI set to (96, 96)
[    76.505] (II) Loading sub module "wfb"
[    76.505] (II) LoadModule: "wfb"
[    76.506] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    76.506] (II) Module wfb: vendor="X.Org Foundation"
[    76.506]     compiled for 1.9.0, module version = 1.0.0
[    76.506]     ABI class: X.Org ANSI C Emulation, version 0.4
[    76.506] (II) Loading sub module "fb"
[    76.506] (II) LoadModule: "fb"
[    76.506] (II) Loading /usr/lib/xorg/modules/libfb.so
[    76.506] (II) Module fb: vendor="X.Org Foundation"
[    76.506]     compiled for 1.9.0, module version = 1.0.0
[    76.506]     ABI class: X.Org ANSI C Emulation, version 0.4
[    76.506] (II) Loading sub module "exa"
[    76.506] (II) LoadModule: "exa"
[    76.507] (II) Loading /usr/lib/xorg/modules/libexa.so
[    76.507] (II) Module exa: vendor="X.Org Foundation"
[    76.507]     compiled for 1.9.0, module version = 2.5.0
[    76.507]     ABI class: X.Org Video Driver, version 8.0
[    76.507] (II) Loading sub module "shadowfb"
[    76.507] (II) LoadModule: "shadowfb"
[    76.507] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    76.507] (II) Module shadowfb: vendor="X.Org Foundation"
[    76.507]     compiled for 1.9.0, module version = 1.0.0
[    76.507]     ABI class: X.Org ANSI C Emulation, version 0.4
[    76.507] (II) UnloadModule: "nv"
[    76.507] (II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
[    76.507] (II) UnloadModule: "vesa"
[    76.507] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    76.507] (II) UnloadModule: "fbdev"
[    76.507] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    76.507] (II) UnloadModule: "fbdevhw"
[    76.507] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[    76.507] (--) Depth 24 pixmap format is 32 bpp
[    76.511] (II) NOUVEAU(0): Opened GPU channel 2
[    76.511] (II) NOUVEAU(0): [DRI2] Setup complete
[    76.511] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    76.511] (II) NOUVEAU(0): GART: 512MiB available
[    76.512] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[    76.512] (II) EXA(0): Driver allocated offscreen pixmaps
[    76.512] (II) EXA(0): Driver registered support for the following operations:
[    76.512] (II)         Solid
[    76.512] (II)         Copy
[    76.512] (II)         Composite (RENDER acceleration)
[    76.512] (II)         UploadToScreen
[    76.512] (II)         DownloadFromScreen
[    76.512] (==) NOUVEAU(0): Backing store disabled
[    76.512] (==) NOUVEAU(0): Silken mouse enabled
[    76.512] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[    76.512] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    76.512] (==) NOUVEAU(0): DPMS enabled
[    76.512] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    76.513] (--) RandR disabled
[    76.513] (II) Initializing built-in extension Generic Event Extension
[    76.513] (II) Initializing built-in extension SHAPE
[    76.513] (II) Initializing built-in extension MIT-SHM
[    76.513] (II) Initializing built-in extension XInputExtension
[    76.513] (II) Initializing built-in extension XTEST
[    76.513] (II) Initializing built-in extension BIG-REQUESTS
[    76.513] (II) Initializing built-in extension SYNC
[    76.513] (II) Initializing built-in extension XKEYBOARD
[    76.513] (II) Initializing built-in extension XC-MISC
[    76.513] (II) Initializing built-in extension SECURITY
[    76.513] (II) Initializing built-in extension XINERAMA
[    76.513] (II) Initializing built-in extension XFIXES
[    76.513] (II) Initializing built-in extension RENDER
[    76.513] (II) Initializing built-in extension RANDR
[    76.513] (II) Initializing built-in extension COMPOSITE
[    76.513] (II) Initializing built-in extension DAMAGE
[    76.513] (II) Initializing built-in extension GESTURE
[    76.521] (II) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
[    76.521] (II) AIGLX: reverting to software rendering
[    76.521] (II) AIGLX: Screen 0 is not DRI capable
[    76.523] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    76.523] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    76.531] (II) NOUVEAU(0): NVEnterVT is called.
[    76.531] (II) NOUVEAU(0): Setting screen physical size to 444 x 277
[    76.531] resize called 1680 1050
[    76.544] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    76.551] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    76.551] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    76.551] (II) LoadModule: "evdev"
[    76.551] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    76.552] (II) Module evdev: vendor="X.Org Foundation"
[    76.552]     compiled for 1.9.0, module version = 2.3.2
[    76.552]     Module class: X.Org XInput Driver
[    76.552]     ABI class: X.Org XInput driver, version 11.0
[    76.552] (**) Power Button: always reports core events
[    76.552] (**) Power Button: Device: "/dev/input/event1"
[    76.564] (II) Power Button: Found keys
[    76.564] (II) Power Button: Configuring as keyboard
[    76.564] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    76.564] (**) Option "xkb_rules" "evdev"
[    76.564] (**) Option "xkb_model" "pc105"
[    76.564] (**) Option "xkb_layout" "us"
[    76.565] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    76.565] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    76.565] (**) Power Button: always reports core events
[    76.565] (**) Power Button: Device: "/dev/input/event0"
[    76.580] (II) Power Button: Found keys
[    76.580] (II) Power Button: Configuring as keyboard
[    76.580] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    76.580] (**) Option "xkb_rules" "evdev"
[    76.580] (**) Option "xkb_model" "pc105"
[    76.580] (**) Option "xkb_layout" "us"
[    76.583] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    76.583] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    76.583] (**) USB Optical Mouse: always reports core events
[    76.583] (**) USB Optical Mouse: Device: "/dev/input/event3"
[    76.596] (II) USB Optical Mouse: Found 3 mouse buttons
[    76.596] (II) USB Optical Mouse: Found scroll wheel(s)
[    76.596] (II) USB Optical Mouse: Found relative axes
[    76.596] (II) USB Optical Mouse: Found x and y relative axes
[    76.596] (II) USB Optical Mouse: Configuring as mouse
[    76.596] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    76.596] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    76.596] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    76.596] (II) USB Optical Mouse: initialized for relative axes.
[    76.596] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    76.596] (II) No input driver/identifier specified (ignoring)
[    76.599] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    76.599] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    76.599] (**) AT Translated Set 2 keyboard: always reports core events
[    76.599] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    76.599] (II) AT Translated Set 2 keyboard: Found keys
[    76.599] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    76.599] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    76.599] (**) Option "xkb_rules" "evdev"
[    76.599] (**) Option "xkb_model" "pc105"
[    76.599] (**) Option "xkb_layout" "us"
[    77.335] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1386
[    77.335] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[    77.335] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[    77.336] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    77.336] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    77.336] (II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    77.933] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1386
[    77.933] (II) NOUVEAU(0): Using hsync ranges from config file
[    77.933] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    77.933] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    77.933] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    77.933] (II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    78.445] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1386
[    78.445] (II) NOUVEAU(0): Using hsync ranges from config file
[    78.445] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    78.445] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    78.445] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    78.445] (II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    78.957] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1386
[    78.957] (II) NOUVEAU(0): Using hsync ranges from config file
[    78.957] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    78.957] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    78.957] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    78.957] (II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    84.605] (II) NOUVEAU(0): EDID vendor "SAM", prod id 1386
[    84.605] (II) NOUVEAU(0): Using hsync ranges from config file
[    84.605] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    84.605] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    84.605] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[    84.605] (II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
```Any ideas?

P.S. could someone tell me what hose commands do, because I have no idea what I just did ;/

---

### Post by Dscottmc7 on 2010-11-07
Whoa, Hamishfox...
I am old but a newbe whenever it comes to code.  I'm a gnarled writer...so I just need the OS to work!

I had virtually the same problem...at least I was at that command line for 14 days!!  I realized a rule that the experts will tell me I'm nuts, but for the record, "Never Upgrade!"  Always backup and then do a clean install.  Unless you're a code freak and just want the challenge.

I did everything you did...I have an HP Pavilion (new one and old...I'm on the old), m7674n, 2Gb. RAM, Intel Dual Core (X2), 200Gb drive + peripherals, HP w1907 flat screen monitor, Nvidia GeForce 7300 SL graphics card.

I upgraded in a deranged moment of excitement for the new flash...and the rest is 14 days of lost time...my fault!  Actually, I've had an inoperative CDROM for 2 years.  My last clean install was from as USB key.  [so my thinking was to somehow detect my CDROM and new USB CDROM with particular attention to the BIOS...'cuz it's old and doesn't allow USB Boot.  I used UUID to identify the CDROMs (/dev/disk/by-path [by-ID, by-UUID, by-label], and narrowed it down.  I finally got the cdroms (both working)...but that's just for 'info' if you're far more capable than I...but in the end it didn't matter.

I did all you have.  When I finally got to where you are, (remember I have a Nvidia 7300card), I decided to start over!  I'd searched and implemented every piece of advice in the Ubuntu gurus...and more.  MY BIGGEST PROBLEM WAS "NOVEAU" OR "NV"  (NEITHER!!!)  SO, I deleted (purged) everything "Nivida."  After all I hadn't anything to lose, (I'd backed up everything to an external HDD), and simply rebooted.  I let the default Xorg put in the variables and up came my Xwindows!

It was a slice of Heaven to see that familiar crap purple to whatever!  I then changed the Nvidia driver for an update (sudo apt-get nvidia-current) because  Xorg had installed and compiled the 'nvidia-kernel-module.'

Now that's a layman's diatribe.  OK, maybe in today's Internet speak:
1. *sudo apt-get install* by following the output of the Xorg.0.log --many times!
2. *sudo apt-get update* at various stages along the way. I've found that when some "packages" cannot be installed I found the basic ones within a package to install and viola, I could then install the rest.  (monitor, screens, etc.)
3.  Functional screens.  I struggled with every option to man.  I think it's a trade-off with "Nvidia" (e.g. either you have a FATAL error with Nvidia-module-kernel not installed or the Screen output says "...but none that were acceptable [forgot the actual word].
4.  I think that I got every update I needed and ended up with those two issues.  That's when I purged everything Nvidia.  Reboot...

Dunno...just what I did frustratingly.  But 10.10 is more than worth it!
Good luck, buddy...
Scott
PS: sorry for not having an exact 4 word answer!

---

### Post by Cheesehead on 2010-11-07
Installation freezes can happen for a lot of reasons. And they can have a lot of different effects. The result of somebody else's freeze can be totally different from your result. So don't put too much stock in someone else's fix if you don't understand it completely.

First, is your data backed up somewhere on an external drive?

Second, will a LiveCD run flawlessly on your system?

Third, what does your current (broken) boot sequence look like? Do you get any errors? Exactly what do they say? How are you reaching a command prompt?

Fourth, do you have network access from the command line? Do you know how to get network access from the command line? Or do you have an Alternate CD?

Fifth, look in /var/log/dist-upgrade/main.log for error messages. If there are errors in that log, attach it here.

---

