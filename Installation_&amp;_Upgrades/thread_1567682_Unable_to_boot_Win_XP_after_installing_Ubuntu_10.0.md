---
title: "Unable to boot Win XP after installing Ubuntu 10.04. HELP Yaar ...!"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by Buntu Man on 2010-09-04
First of all, I am new to Ubuntu. It is a great experience. Linux  rocks...:KS

I installed Ubuntu 10.04 on my hard disk (40GB) already hosts my Windows XP [COLOR=Red]( Installed 1st )[/COLOR] on the C: partition (My system is  nearly 10 years old).

First I was able to boot to XP[COLOR=Red](through GRUB, which was installed by  default).[/COLOR]:smile:

[SIZE=4]**[COLOR=Blue]now since 2-3 days[/COLOR]**[/SIZE]
When i select XP , the OS doesn't boot and only a BLANK Screen ( **when I select XP to boot from GRUB Menu, I go to the [COLOR=Blue]Windows not turn off/shutdown properly menu[/COLOR] and when i select to boot windows normally from the [COLOR=Red]old worked setting[/COLOR] i get the [COLOR=Red]BLANK screen without any cursor but a totally blank screen which i am talking about[/COLOR]** ) for eternity. The processor is working heavily(which i  can make out from the deafening fan speed). And all left for my option  is switching off directly. But booting ubuntu causes no problem.:sad::sad::sad:

[COLOR=Magenta]Now, i want to solve this problem and without losing any valuable data  that i have in that hard-disk. :confused:
Please help friends... My only hope lies with you...
Thank you in advance and anticipation...[/COLOR][-o<

[COLOR="SeaGreen"]Note[/COLOR] : I have tried using [COLOR="Blue"]fixboot[/COLOR] command but [COLOR="blue"]dint worked[/COLOR] BUT I have [COLOR="blue"]not used fixmbr command[/COLOR] because i dont know how to use it.
        

[SIZE=4][COLOR=Red]**the output of the Boot Info Script**[/COLOR][/SIZE]

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    28,676,024    28,675,962   7 HPFS/NTFS
/dev/sda2          28,676,086    78,241,791    49,565,706   f W95 Ext d (LBA)
/dev/sda5          28,676,088    63,004,317    34,328,230   b W95 FAT32
/dev/sda6          63,004,672    77,484,031    14,479,360  83 Linux
/dev/sda7          77,486,080    78,241,791       755,712  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0E7C26787C265B2B                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        84FB-D96F                              vfat                                     
/dev/sda6        2c8d0777-1802-4358-a7c2-2c9b3ba10108   ext4                                     
/dev/sda7        02d4761c-02cb-4a84-ae59-674cc064fcb5   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sr1         /media/WINDOWS XP        iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=119,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda1        /media/0E7C26787C265B2B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 2c8d0777-1802-4358-a7c2-2c9b3ba10108
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 2c8d0777-1802-4358-a7c2-2c9b3ba10108
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2c8d0777-1802-4358-a7c2-2c9b3ba10108
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2c8d0777-1802-4358-a7c2-2c9b3ba10108 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2c8d0777-1802-4358-a7c2-2c9b3ba10108
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=2c8d0777-1802-4358-a7c2-2c9b3ba10108 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2c8d0777-1802-4358-a7c2-2c9b3ba10108
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 2c8d0777-1802-4358-a7c2-2c9b3ba10108
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0e7c26787c265b2b
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=2c8d0777-1802-4358-a7c2-2c9b3ba10108 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=02d4761c-02cb-4a84-ae59-674cc064fcb5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  34.8GB: boot/grub/core.img
  37.9GB: boot/grub/grub.cfg
  34.8GB: boot/initrd.img-2.6.32-21-generic
  34.8GB: boot/vmlinuz-2.6.32-21-generic
  34.8GB: initrd.img
  34.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  6e 00 6b 00 88 01 00 00  00 00 00 00 00 00 00 00  |n.k.............|
00000010  01 00 00 00 01 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 08 80 00 00  05 00 ad de 3d 00 00 00  |............=...|
00000030  00 00 00 00 00 10 00 00  1c 00 00 00 00 00 00 00  |................|
00000040  3b 00 00 39 41 35 00 01  41 35 00 02 3a 00 02 51  |;..9A5..A5..:..Q|
00000050  3b 00 03 39 41 35 00 01  41 b8 00 04 39 3a 00 00  |;..9A5..A...9:..|
00000060  40 43 42 3b 00 05 39 41  35 00 02 41 35 00 06 35  |@CB;..9A5..A5..5|
00000070  00 07 35 00 08 3a 00 02  3a 00 06 51 c3 00 00 00  |..5..:..:..Q....|
00000080  09 00 00 00 00 00 00 00  04 00 00 00 10 00 00 00  |................|
00000090  75 00 72 00 6c 00 53 00  65 00 63 00 75 00 72 00  |u.r.l.S.e.c.u.r.|
000000a0  69 00 74 00 79 00 43 00  68 00 65 00 63 00 6b 00  |i.t.y.C.h.e.c.k.|
000000b0  01 00 00 00 04 00 00 00  07 00 00 00 6c 00 69 00  |............l.i.|
000000c0  6e 00 6b 00 55 00 52 00  4c 00 00 00 02 00 00 00  |n.k.U.R.L.......|
000000d0  04 00 00 00 06 00 00 00  64 00 6f 00 63 00 55 00  |........d.o.c.U.|
000000e0  52 00 4c 00 03 00 00 00  04 00 00 00 07 00 00 00  |R.L.............|
000000f0  73 00 61 00 76 00 65 00  55 00 52 00 4c 00 00 00  |s.a.v.e.U.R.L...|
00000100  04 00 00 00 04 00 00 00  08 00 00 00 6c 00 69 00  |............l.i.|
00000110  6e 00 6b 00 54 00 65 00  78 00 74 00 05 00 00 00  |n.k.T.e.x.t.....|
00000120  04 00 00 00 07 00 00 00  6d 00 61 00 6b 00 65 00  |........m.a.k.e.|
00000130  55 00 52 00 49 00 00 00  06 00 00 00 04 00 00 00  |U.R.I...........|
00000140  06 00 00 00 74 00 61 00  72 00 67 00 65 00 74 00  |....t.a.r.g.e.t.|
00000150  07 00 00 00 04 00 00 00  0d 00 00 00 6f 00 77 00  |............o.w.|
00000160  6e 00 65 00 72 00 44 00  6f 00 63 00 75 00 6d 00  |n.e.r.D.o.c.u.m.|
00000170  65 00 6e 00 74 00 00 00  08 00 00 00 04 00 00 00  |e.n.t...........|
00000180  0c 00 00 00 63 00 68 00  61 00 72 00 61 00 63 00  |....c.h.a.r.a.c.|
00000190  74 00 65 00 72 00 53 00  65 00 74 00 b0 65 01 64  |t.e.r.S.e.t..e.d|
000001a0  01 63 0c b4 65 01 64 01  64 05 b6 65 01 64 01 63  |.c..e.d.d..e.d.c|
000001b0  04 63 07 63 12 63 28 00  00 00 00 00 23 00 00 01  |.c.c.c(.....#...|
000001c0  c1 ff 0b fe ff ff 02 00  00 00 a6 ce 0b 02 00 fe  |................|
000001d0  ff ff 05 fe ff ff a8 ce  0b 02 62 f1 dc 00 00 00  |..........b.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



---

### Post by oldfred on 2010-09-04
Fixmbr will install the windows boot loader to the MBR and then you will directly boot windows but not see Ubuntu. You then would have to reinstall grub2 to boot Ubuntu.

But grub just passes the boot the the windows partition, just like the windows boot loader in the MBR does, so I would think directly booting windows will give you the same problem.

You already did fixboot. I would try chkdsk. You often have to run it several times or until there are no errors.

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C:
chkdsk c: /r
XP CHKDSK info:
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk drive: /p /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

