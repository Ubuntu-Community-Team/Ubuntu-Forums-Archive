---
title: "ubuntu install fails; update-grub2 fails; can't boot"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by eatyourgrub on 2009-12-07
Hello,
I have a system with 3 drives; 2 hardrives and one compactflash.
I can forcibly boot with a bios boot menu into 9.10 live usb.  From there I installed to one harddrive.  I rebooted and found just sh:grub.
I booted into live usb and installed to the second harddrdive.  Again, I just get sh:grub.
Ubuntu installation completely failed.  I even used bios to boot into each drive. all gave same results.
Now I try instructions at:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
To reinstall grub (basically, grub-install).  I did this for every drive.
Grub still fails to load anything.
Next I tried update-grub2.  It says, grub-probe error: cannot find a device for /.
It's clearly not going to be easy to get grub fixed at this point, I can't even change the config files and have them update.
Even when I had one drive, I could never get grub to work.
Thanks for any help!
ubuntu 9.10, intel atom board mini-itx.

---

### Post by darkod on 2009-12-07
Boot with the LiveUSB and download the script in my signature. Move it for example to desktop and execute it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with lots info about your boot process. Copy the content of that file here and wrap CODE tags around it for easier reading (when the text is selected hit the # in the toolbar above).

---

### Post by eatyourgrub on 2009-12-07
```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /grub.
 => Grub 1.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /grub.
 => No known boot loader is installed in the MBR of /dev/sdd

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sdb1 and 
                       looks at sector 1132551 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sdd and 
                       looks on partition #1 for /grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 64 MB, 64225280 bytes
255 heads, 63 sectors/track, 7 cylinders, total 125440 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x30213c5e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,807,589     7,807,527  83 Linux
/dev/sdb2           7,807,590    11,711,384     3,903,795   5 Extended
/dev/sdb5           7,807,653    11,711,384     3,903,732  82 Linux swap / Solaris
/dev/sdb3          11,711,385 1,465,144,064 1,453,432,680  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bd6ad

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63 2,895,796,574 2,895,796,512  83 Linux
/dev/sdc2       2,895,796,575 2,930,272,064    34,475,490   5 Extended
/dev/sdc5       2,895,796,638 2,928,729,824    32,933,187  83 Linux
/dev/sdc6       2,928,729,888 2,930,272,064     1,542,177  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4016 MB, 4016046080 bytes
124 heads, 62 sectors/track, 1020 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0bcd68e

Partition  Boot         Start           End          Size  Id System

/dev/sdd1     ? 3,223,366,781 3,470,046,704   246,679,924  78 Unknown
/dev/sdd2     ?   432,871,117 1,208,554,935   775,683,819  10 OPUS
/dev/sdd3     ? 1,869,562,563 3,788,792,630 1,919,230,068  8b Unknown
/dev/sdd4     ? 2,802,843,648 2,811,166,733     8,323,086   a OS/2 Boot Manager

/dev/sdd1 ends after the last sector of /dev/sdd
/dev/sdd1 overlaps with /dev/sdd3
/dev/sdd2 ends after the last sector of /dev/sdd
/dev/sdd3 ends after the last sector of /dev/sdd
/dev/sdd3 overlaps with /dev/sdd4
/dev/sdd4 ends after the last sector of /dev/sdd

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda: UUID="2fda1f05-194c-4e18-8569-3badec86224b" TYPE="swap" 
/dev/sdb1: LABEL="sdb1" UUID="96d63b91-a5ff-4229-ae6c-eead82de4c96" TYPE="ext4" 
/dev/sdb3: LABEL="700" UUID="d47fadbb-f83d-442d-9582-875428b98636" TYPE="ext4" 
/dev/sdb5: UUID="9a69fb2c-d296-401d-88bd-780abe2d9e94" TYPE="swap" 
/dev/sdc1: LABEL="15tb-2" UUID="de9b3fea-88ae-4daf-ab98-4b11ac68d556" TYPE="ext4" 
/dev/sdc5: LABEL="sdc5" UUID="91fa3c3f-ba01-44a8-be96-43ca03f0b64c" TYPE="ext4" 
/dev/sdc6: UUID="860b477c-c0ab-4032-98ad-ff786b30bfb9" TYPE="swap" 
/dev/sdd: LABEL="4G STICK" UUID="D401-5E7F" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdd on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 96d63b91-a5ff-4229-ae6c-eead82de4c96
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 96d63b91-a5ff-4229-ae6c-eead82de4c96
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=96d63b91-a5ff-4229-ae6c-eead82de4c96 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 96d63b91-a5ff-4229-ae6c-eead82de4c96
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=96d63b91-a5ff-4229-ae6c-eead82de4c96 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 96d63b91-a5ff-4229-ae6c-eead82de4c96
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=96d63b91-a5ff-4229-ae6c-eead82de4c96 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 96d63b91-a5ff-4229-ae6c-eead82de4c96
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=96d63b91-a5ff-4229-ae6c-eead82de4c96 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.10 (9.10) (on /dev/sdc5)" {
    insmod ext2
    set root=(hd2,5)
    search --no-floppy --fs-uuid --set 91fa3c3f-ba01-44a8-be96-43ca03f0b64c
    linux /boot/vmlinuz-2.6.31-14-server root=/dev/sdc5
    initrd /boot/initrd.img-2.6.31-14-server
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=96d63b91-a5ff-4229-ae6c-eead82de4c96 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda during installation
UUID=2fda1f05-194c-4e18-8569-3badec86224b none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=9a69fb2c-d296-401d-88bd-780abe2d9e94 none            swap    sw              0       0
# swap was on /dev/sdc6 during installation
UUID=860b477c-c0ab-4032-98ad-ff786b30bfb9 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

=========================== sdc5/boot/grub/grub.cfg: ===========================


=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=91fa3c3f-ba01-44a8-be96-43ca03f0b64c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=860b477c-c0ab-4032-98ad-ff786b30bfb9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


1482.6GB: boot/grub/grub.cfg
1482.6GB: boot/initrd.img-2.6.31-14-server
1482.6GB: boot/vmlinuz-2.6.31-14-server
1482.6GB: initrd.img
1482.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 24 00  |.X.MSDOS5.0...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 b0 77 00 de 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 7f 5e 01 d4 4e  4f 20 4e 41 4d 45 20 20  |..).^..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c0 8e d0  |  FAT32   ..1...|
00000060  bc b4 7b 06 57 8e c0 b9  08 00 bf b4 7b f3 a5 8e  |..{.W.......{...|
00000070  d8 bb 78 00 0f b4 37 0f  a0 56 88 16 91 2c 20 d2  |..x...7..V..., .|
00000080  78 15 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |x....?.G..d....||
00000090  88 4d f8 cd 13 eb 27 f6  45 f0 7f 75 08 66 8b 45  |.M....'.E..u.f.E|
000000a0  f8 66 a3 1c 7c b4 08 cd  13 72 13 20 e4 75 0f c1  |.f..|....r. .u..|
000000b0  ea 08 42 89 16 1a 7c 83  e1 3f 89 0e 18 7c fb bb  |..B...|..?...|..|
000000c0  aa 55 b4 41 8a 16 91 2c  cd 13 72 10 81 fb 55 aa  |.U.A...,..r...U.|
000000d0  75 0a f6 c1 01 74 05 c6  06 02 7d 00 66 a1 f8 7d  |u....t....}.f..}|
000000e0  bb 00 7e e8 10 00 66 81  3e 24 7e 0f 20 6e 76 0f  |..~...f.>$~. nv.|
000000f0  85 c3 00 e9 3a 02 bd 01  00 66 03 06 1c 7c 66 31  |....:....f...|f1|
00000100  d2 eb 4f 55 e8 d5 00 66  0f b7 fd b9 10 00 66 52  |..OU...f......fR|
00000110  66 50 06 53 57 6a 10 89  e6 66 60 8a 16 91 2c 1e  |fP.SWj...f`...,.|
00000120  16 1f b4 42 cd 13 1f 66  61 8d 64 10 72 10 5d 66  |...B...fa.d.r.]f|
00000130  01 f8 29 fd c1 e7 09 01  fb 21 ed 75 c6 c3 66 60  |..)......!.u..f`|
00000140  31 c0 8a 16 91 2c cd 13  66 61 e2 c2 c6 06 02 7d  |1....,..fa.....}|
00000150  4f 5d 66 52 66 50 55 53  66 0f b7 36 18 7c 66 0f  |O]fRfPUSf..6.|f.|
00000160  b7 3e 1a 7c 66 f7 f6 31  c9 87 ca 66 f7 f7 e8 6b  |.>.|f..1...f...k|
00000170  00 29 ce 39 f5 76 02 89  f5 c0 e4 06 41 08 e1 88  |.).9.v......A...|
00000180  c5 88 d6 8a 16 91 2c 95  b4 02 bd 10 00 66 60 cd  |......,......f`.|
00000190  13 66 61 72 17 66 0f b6  c8 c1 e0 09 5b 01 c3 5d  |.far.f......[..]|
000001a0  66 58 66 5a 66 01 c8 29  cd 75 a7 c3 4d 75 de 95  |fXfZf..).u..Mu..|
000001b0  d1 2e fc 7d 75 df 31 f6  8e d6 bc b0 7b 8e de 66  |...}u.1.....{..f|
000001c0  8f 06 78 00 be e7 7d ac  20 c0 74 09 b4 0e bb 07  |..x...}. .t.....|
000001d0  00 cd 10 eb f2 98 cd 16  cd 19 eb fe 3b 2e fc 7d  |............;..}|
000001e0  76 04 8b 2e fc 7d c3 42  6f 6f 74 20 65 72 72 6f  |v....}.Boot erro|
000001f0  72 0d 0a 00 00 00 00 00  10 a7 0e 00 7f 00 55 aa  |r.............U.|
00000200

Unknown BootLoader  on sdd1


Unknown BootLoader  on sdd2


Unknown BootLoader  on sdd3


Unknown BootLoader  on sdd4



=============================== StdErr Messages: ===============================

hexdump: /dev/sdd1: No such file or directory
hexdump: /dev/sdd1: No such file or directory
hexdump: /dev/sdd2: No such file or directory
hexdump: /dev/sdd2: No such file or directory
hexdump: /dev/sdd3: No such file or directory
hexdump: /dev/sdd3: No such file or directory
hexdump: /dev/sdd4: No such file or directory
hexdump: /dev/sdd4: No such file or directory
```

---

### Post by eatyourgrub on 2009-12-12
Anyone?

---

### Post by darkod on 2009-12-12
You have two ubuntu installs, on /dev/sdb and /dev/sdc. Is that on purpose or error?
Also, you have grub2 installed on the MBR of both /dev/sdb and /dev/sdc which is fine, but you also have grub2 installed in the partition /dev/sdb1 which might be confusing things. Did you deliberately install grub2 on that partition? Because by default it would never install onto a partition.
Or maybe when you were restoring it you put it there in error.

---

### Post by eatyourgrub on 2009-12-12
Hi,
The multitude of grub installs is due to my unsuccessful attempts to keep installing grub everywhere to get the machine to boot.
As it stands, booting for any drive will cause grub to fails in all circumstances - just a grub prompt with no menu.
Of course, I don't need so many grubs.. I'll happy remove all but the one that is necessary.
The two Ubuntu's are 1) server 2) 9.10 desktop.  I wouldn't mind being able to boot both.
As for the grub being on the partition, this may have been from my attempts at re-installing grub.
So, if I can erase all the grubs but one, and try to get that to boot my installed systems, that would be a good goal.
How to proceed?

Thanks for your help!

---

