---
title: "Dual Booting Win 7 and Ubuntu (9.10) from sdb"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by jr226 on 2010-01-07
I have Windows 7 installed, on sdb 1, and Ubuntu installed on sdb2.  The Windows boot mgr is located on sdb 1, and grub on sdb 2.  When I boot up my computer, Windows 7 boots without a choice for selecting an OS.  

I would like to have GRUB boot and let me select either Ubuntu or Win 7.

I have run the Boot Info Script and the results are below if this helps:
> 
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=d48354e4-7ab5-4d23-9dbe-88bb5d26f84c)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000abbd7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,769,023   976,766,976   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07ebec70

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   153,602,047   153,600,000   7 HPFS/NTFS
/dev/sdb2         153,613,530   182,900,024    29,286,495  83 Linux
/dev/sdb3         182,900,025   312,576,704   129,676,680   5 Extended
/dev/sdb5         182,900,088   194,611,409    11,711,322  82 Linux swap / Solaris
/dev/sdb6         194,611,473   223,913,969    29,302,497  83 Linux
/dev/sdb7         223,914,033   312,576,704    88,662,672  83 Linux


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="841095E41095DD8C" LABEL="Media" TYPE="ntfs" 
sdb1: UUID="3AD30040D2FFFE3F" TYPE="ntfs" 
sdb2: UUID="d48354e4-7ab5-4d23-9dbe-88bb5d26f84c" TYPE="ext4" 
sdb5: UUID="92324512-ec19-4d3b-a73b-9f7df61f07a1" TYPE="swap" 
sdb6: UUID="37be3a33-3007-4665-95e4-aa347bd697d2" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
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
/dev/sdb2 on /media/d48354e4-7ab5-4d23-9dbe-88bb5d26f84c type ext4 (rw,nosuid,nodev,uhelper=devkit)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root=(hd1,2)
search --no-floppy --fs-uuid --set d48354e4-7ab5-4d23-9dbe-88bb5d26f84c
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set d48354e4-7ab5-4d23-9dbe-88bb5d26f84c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d48354e4-7ab5-4d23-9dbe-88bb5d26f84c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set d48354e4-7ab5-4d23-9dbe-88bb5d26f84c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d48354e4-7ab5-4d23-9dbe-88bb5d26f84c ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 3ad30040d2fffe3f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=d48354e4-7ab5-4d23-9dbe-88bb5d26f84c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=92324512-ec19-4d3b-a73b-9f7df61f07a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  78.6GB: boot/grub/core.img
  78.6GB: boot/grub/grub.cfg
  78.6GB: boot/initrd.img-2.6.31-14-generic
  78.6GB: boot/vmlinuz-2.6.31-14-generic
  78.6GB: initrd.img
  78.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb7

00000000  55 36 22 35 55 04 c1 32  9a 20 a6 32 a8 4e 00 46  |U6"5U..2. .2.N.F|
00000010  01 61 63 62 cb 45 9b 58  02 84 09 50 da fe 1a 29  |.acb.E.X...P...)|
00000020  13 12 07 c1 da b5 5a 07  db 00 97 02 d6 00 4b 31  |......Z.......K1|
00000030  45 17 ab 88 70 05 15 86  c9 c5 f7 9e 36 d7 12 ae  |E...p.......6...|
00000040  73 bf 72 21 4d a7 b7 4d  75 4a f7 96 f8 c9 a9 fa  |s.r!M..MuJ......|
00000050  38 b2 63 2b 77 7e 05 c8  93 b0 9d ee 13 72 f3 28  |8.c+w~.......r.(|
00000060  88 a9 2c 3b fa 10 08 2c  f4 95 c4 c4 4f 5c 98 27  |..,;...,....O\.'|
00000070  09 bd 98 04 89 f3 89 08  25 13 d1 16 28 65 1e 21  |........%...(e.!|
00000080  40 67 25 84 02 e6 e2 25  41 52 7c 21 4e be ef 01  |@g%....%AR|!N...|
00000090  f8 04 a5 a8 6c 89 0b 05  6a 1b 14 2e 55 99 52 04  |....l...j...U.R.|
000000a0  f9 5c b9 72 db 78 dd cd  56 95 03 e5 48 50 29 2a  |.\.r.x..V...HP)*|
000000b0  6c fd 4f 69 cd 78 b3 84  0a 7d a9 df 9b 4e df 4f  |l.Oi.x...}...N.O|
000000c0  41 97 98 8e 97 07 e9 25  7b 59 d3 30 3b bb 5b d9  |A......%{Y.0;.[.|
000000d0  c5 34 ae f3 25 9b ab d4  61 41 28 9c 49 d0 8c 65  |.4..%...aA(.I..e|
000000e0  dd ee b3 e1 10 22 ed f1  91 68 88 45 8d 77 8a dd  |....."...h.E.w..|
000000f0  65 9d 2a 56 8f 2c af 52  77 86 46 e4 1d 59 2d 03  |e.*V.,.Rw.F..Y-.|
00000100  8d e4 5b 9b ea 3d c3 b6  6a 12 b2 b6 6d fd 2d 4e  |..[..=..j...m.-N|
00000110  c5 1c 6a 14 01 4f 06 a9  3d 2b 3a e8 3b 41 ca 0d  |..j..O..=+:.;A..|
00000120  ac 54 08 bd 36 7d 65 65  66 af 55 4b 71 71 0d 15  |.T..6}eef.UKqq..|
00000130  41 74 0e 65 ca 71 1d 92  40 1f 9b 6e 7b 5f 8c 82  |At.e.q..@..n{_..|
00000140  00 76 5c e5 89 c7 21 65  55 ae 57 97 22 22 3b b4  |.v\...!eU.W."";.|
00000150  d2 95 37 30 92 2e f4 2a  2a e2 4d 31 7e cc 8d 48  |..70...**.M1~..H|
00000160  01 71 21 06 95 17 f7 b7  93 bc 02 40 00 7c a9 ad  |.q!........@.|..|
00000170  ef ec 53 8c 82 02 20 2b  d0 3b 17 d7 bc 20 00 00  |..S... +.;... ..|
00000180  00 0d 54 83 d0 2c 4a db  6a 88 d8 1b 34 99 25 24  |..T..,J.j...4.%$|
00000190  24 09 e8 96 41 6f 1b b9  24 40 5b ed f2 72 44 26  |$...Ao..$@[..rD&|
000001a0  b2 ea 7a 51 e6 c9 d3 d3  b9 9b 63 8d 97 d6 d4 ba  |..zQ......c.....|
000001b0  68 28 41 48 b1 90 11 c1  4c 6f 40 0e 66 ae ae f5  |h(AH....Lo@.f...|
000001c0  d5 89 b5 5e 49 36 92 d6  d2 8f 32 b0 d1 62 ee e8  |...^I6....2..b..|
000001d0  31 86 41 28 83 da 6b 45  e3 f0 d6 ec b7 15 50 44  |1.A(..kE......PD|
000001e0  b1 41 de 71 86 59 9b 9f  cf ad 6c 7a 5f 36 ca 2d  |.A.q.Y....lz_6.-|
000001f0  83 65 9a 01 86 25 b9 87  d3 43 a4 19 ba 87 b9 4a  |.e...%...C.....J|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script045.sh: line 1421: type: lvscan: not found
/home/ubuntu/Desktop/boot_info_script045.sh: line 1451: type: mdadm: not found



Thanks a lot for any help you can give me!

---

### Post by oldfred on 2010-01-07
If windows is booting the BIOS must be set to boot from sdb -160GB. Try going into the BIOS and set sda - 500GB to boot first.

---

### Post by jr226 on 2010-01-07
Thanks for the tip, just tried it and got as far as 

  GRUB loading.

in the BIOS.  When I was looking at GRUB before from the Live CD in the loaction that it is listed, there was no file MENU.lst.  I assume that this may be the problem.  If I have this configuration, how do I create a MENU.lst file which will allow for booting given the locations of my OS's?

Thanks again!

---

### Post by lindsay7 on 2010-01-07
First of all "Grub 1.97 is installed in the MBR of /dev/sda and looks for
(UUID=d48354e4-7ab5-4d23-9dbe-88bb5d26f84c)/boot/grub.
=> Windows is installed in the MBR of /dev/sdb"

Which says that grub is on sda and wants to look for linux on sdb2 (uuid).

Your grub menu says that the root is "set root=(hd1,2)" but if linux is on sdb2 the root would be hd1,1.

The grub menu also says that the root for windows "### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
insmod ntfs
set root=(hd1,1)
search --no-floppy --fs-uuid --set 3ad30040d2fffe3f
chainloader +1" is on sdb1 but if so the root should be hd1,0


So unless I am mixed up on drive and partition designation. your roots are off by one.  I would think you should edit the grub menu and see if that fixes things.

---

### Post by jr226 on 2010-01-07
There is currently no menu.lst file (that I can find).  Is this just a text file that I can write myself, or do I need to use some utility to create it?

---

### Post by lindsay7 on 2010-01-07
I know how to edit the old grub menu but not the grub2 file.  Give your post some time to see if I am correct in the partition numbering and also get some help on how to edit. In the mean time I will look for the way to edit the new grub2 configuration.

---

### Post by lindsay7 on 2010-01-07
Try this first and see if this helps.

type sudo update-grub in the terminal and see if it make the changes that you need.

---

### Post by lindsay7 on 2010-01-07
From what I just read, it looks like the partition numbering has changed with grub2.

"User-defined Entries

Users with "root" privileges can create scripts in the /etc/grub.d/ folder which will be incorporated into the grub.cfg file when update-grub is run.

    *

      The filename should normally take the format XX_name, with XX being a number followed by an underscore and name.
    *

      The order the entry appears on the grub menu is based on numerical ordering of the files in /etc/grub.d. Executable files in the /etc/grub.d folder beginning with an alphabetic character are placed in order following numerical entries.
    * The file must be made executable by typing in a terminal 

sudo chmod +x /etc/grub.d/'''filename'''

    * A sample custom entry. This file creates menu items for running a SystemRescueCD installation on sdb10 and a custom kernel on sda1. 

[COLOR="Red"]NOTE: The new partition naming convention. Devices start counting from 0 as done previously. sda is designated as "hd0", sdb is "hd1", etc. However the first partition is now designated as sda1. Counting partitions does not start with "0". The fifth partition on sda is sda5). "[/COLOR]


So what I said is wrong.  Back to square one on me trying to help you!!

This info is from  [https://wiki.edubuntu.org/Grub2](https://wiki.edubuntu.org/Grub2)

---

### Post by oldfred on 2010-01-07
Did you give it some time?

There is a known bug in grub2 that adds 20 secs to the grub loading if the grub is in the MBR of one drive and Ubuntu in on the other drive.

If you do not need to keep your windows boot in sdb you can reinstall grub to sdb and it will boot faster.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS from working Ubuntu:
sudo dpkg-reconfigure grub-pc

If it still does not boot you may have to reinstall anyway:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by kansasnoob on 2010-01-07
Boot an Ubuntu Live Cd choosing "try without changes ...", then from the live desktop run these commands:

```
sudo mount /dev/sdb2 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
grub-install /dev/sdb
```

```
update-grub
```

That will only recognize Ubuntu, that's OK for now!

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

You should then be able to boot Ubuntu but only Ubuntu. Upon first booting Ubuntu run:

```
sudo update-grub
```

Hopefully then you can boot both.

---

### Post by Mark Phelps on 2010-01-08
I have a situation very similar to yours and solved it by (1) switching boot to the drive with Ubuntu (and GRUB) installed, and (2) running "sudo update-grub".

When that runs, it will echo back a line for every OS it finds.  You should see a line something like "Windows 7 loader on sda".

---

