---
title: "Triple Boot Grub error"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by weizguy on 2010-01-18
I had Ubuntu 9.10 and Windows 7 working perfectly.  Then I decided to work on getting Snow Leopard working.  I finally got Snow Leopard working, but when I went to reboot, I got the Grub Rescue prompt.  Then I read somewhere that I should install Snow Leopard first, then Windows 7, then Ubuntu 9.10.
   
 I used GParted Live to erase all of the hard drives (I am using separate hard drives for each OS).  I installed Snow Leopard on one HD successfully.  Then I installed Windows 7 on another HD successfully.  Then, while I was installing Ubuntu, I noticed that my install of Windows 7 used 100mb of the disk I was using for Ubuntu (Windows Boot Loader), I didn't know if I should of erased and installed on the whole HD for Ubuntu, so I installed it along side it.  I also have two other HD's, one for Snow Leopard data and one for Windows data.


If I change the order of the HD's in BIOS, I can get Windows 7 to open.  Any other order, and I get this error:


Grub Loading
error: no such disk
grub rescue>

I don't mind starting over, but if I do, how do I COMPLETELY wipe the hard drives, I thought I did with GParted.

   
 Here is the RESULTS.txt from the boot info script:


```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks at sector 1375716 
    of the same hard drive for core.img, core.img is at this location on 
    /dev/sde and looks for 
    (UUID=ee4ce66d-82eb-41d7-b05d-89a06fa1d52d)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 1.97 is installed in the MBR of /dev/sdc and looks for 
    (UUID=e63ba323-5ab4-4b31-a419-67aeeeb84746)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde
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
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *              1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34 1,953,520,064 1,953,520,031 Microsoft Windows

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbf392c37

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8886bed5

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   293,041,664   293,041,602   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                   1   293,046,767   293,046,767  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdd1              34   293,041,664   293,041,631 HFS+

Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2f8fd2a7

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sde2             208,845   625,137,344   624,928,500   5 Extended
/dev/sde5             208,908   601,361,144   601,152,237  83 Linux
/dev/sde6         601,361,208   625,137,344    23,776,137  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="72A7DDD125EF3EEF" LABEL="WindowsData" TYPE="ntfs" 
/dev/sdb1: UUID="6BBB76A250158424" LABEL="MacOSxData" TYPE="ntfs" 
/dev/sdc1: UUID="554CF42D6F492CFF" LABEL="Windows" TYPE="ntfs" 
/dev/sdd1: LABEL="MacOSx" TYPE="hfsplus" 
/dev/sde1: UUID="F830E60030E5C5AA" LABEL="System Reserved" TYPE="ntfs" 
/dev/sde5: UUID="ee4ce66d-82eb-41d7-b05d-89a06fa1d52d" TYPE="ext4" 
/dev/sde6: UUID="8a3518bc-cd20-4c68-9570-c891fc90de52" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr1 on /cdrom type iso9660 (rw)
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


=========================== sde5/boot/grub/grub.cfg: ===========================

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
set root=(hd4,5)
search --no-floppy --fs-uuid --set ee4ce66d-82eb-41d7-b05d-89a06fa1d52d
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
    set root=(hd4,5)
    search --no-floppy --fs-uuid --set ee4ce66d-82eb-41d7-b05d-89a06fa1d52d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ee4ce66d-82eb-41d7-b05d-89a06fa1d52d ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd4,5)
    search --no-floppy --fs-uuid --set ee4ce66d-82eb-41d7-b05d-89a06fa1d52d
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ee4ce66d-82eb-41d7-b05d-89a06fa1d52d ro single 
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
menuentry "Mac OS X (on /dev/sdd1)" {
    insmod hfsplus
    set root=(hd3,1)
    search --no-floppy --fs-uuid --set 0000000000000000
        insmod vbe
        do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 0000000000000000 uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devtree.txt ]; then
              xnu_devtree /Extra/devtree.txt
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
menuentry "Windows 7 (loader) (on /dev/sde1)" {
    insmod ntfs
    set root=(hd4,1)
    search --no-floppy --fs-uuid --set f830e60030e5c5aa
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sde5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sde5 during installation
UUID=ee4ce66d-82eb-41d7-b05d-89a06fa1d52d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde6 during installation
UUID=8a3518bc-cd20-4c68-9570-c891fc90de52 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sde5: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .1GB: boot/grub/grub.cfg
    .1GB: boot/initrd.img-2.6.31-14-generic
    .1GB: boot/vmlinuz-2.6.31-14-generic
    .1GB: initrd.img
    .1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdd1

00000000  fa 31 c0 8e d0 bc f0 ff  fb 8e c0 8e d8 b0 48 e8  |.1............H.|
00000010  3d 01 66 8b 44 20 e8 54  01 66 31 c0 66 a3 00 e4  |=.f.D .T.f1.f...|
00000020  80 7c 03 48 75 03 e9 09  00 be a6 7d e8 10 01 e9  |.|.Hu......}....|
00000030  c2 00 b0 5d e8 18 01 b0  01 31 db 8e c3 bb 00 14  |...].....1......|
00000040  66 b9 02 00 00 00 e8 ae  00 73 03 e9 9b 00 a1 00  |f........s......|
00000050  14 3d 42 44 75 3f b0 7c  e8 f4 00 66 8b 1e 14 14  |.=BDu?.|...f....|
00000060  66 0f cb 66 c1 fb 09 66  31 c0 a1 7e 14 86 c4 52  |f..f...f1..~...R|
00000070  66 f7 e3 5a 66 31 db 8b  1e 1c 14 86 df 66 01 d8  |f..Zf1.......f..|
00000080  66 40 66 40 66 89 c1 b0  01 31 db 8e c3 bb 00 14  |f@f@f....1......|
00000090  e8 64 00 72 54 b0 7d e8  b5 00 a1 00 14 3d 48 2b  |.d.rT.}......=H+|
000000a0  74 05 3d 48 58 75 42 b0  2a e8 a3 00 66 a1 28 14  |t.=HXuB.*...f.(.|
000000b0  66 0f c8 66 c1 f8 09 66  8b 1e c0 15 66 0f cb 52  |f..f...f....f..R|
000000c0  66 f7 e3 5a 66 48 66 48  66 01 c1 b0 21 e8 7f 00  |f..ZfHfHf...!...|
000000d0  b0 7e bb 00 20 8e c3 bb  00 02 e8 1a 00 72 0a b0  |.~.. ........r..|
000000e0  59 e8 6b 00 ea 00 02 00  20 be bd 7d e8 50 00 b0  |Y.k..... ..}.P..|
000000f0  58 e8 5b 00 f4 eb fd 66  60 89 e5 1e 1e 66 03 0e  |X.[....f`....f..|
00000100  00 e4 66 03 4c 20 66 51  06 53 30 e4 50 50 b0 2d  |..f.L fQ.S0.PP.-|
00000110  e8 3c 00 66 89 c8 e8 54  00 b0 3d e8 31 00 58 e8  |.<.f...T..=.1.X.|
00000120  4b 00 68 10 00 89 e6 b4  42 cd 13 73 0d e8 3d 00  |K.h.....B..s..=.|
00000130  b0 52 e8 1a 00 31 c0 cd  13 f9 89 ec 66 61 c3 bb  |.R...1......fa..|
00000140  01 00 fc ac 3c 00 74 06  b4 0e cd 10 eb f5 c3 66  |....<.t........f|
00000150  60 bb 01 00 b4 0e cd 10  66 61 c3 66 60 31 c9 88  |`.......fa.f`1..|
00000160  c1 b0 20 e3 05 e8 e7 ff  e2 f9 66 61 c3 66 60 b9  |.. .......fa.f`.|
00000170  04 00 66 0f c8 50 c0 c8  04 e8 17 00 58 e8 13 00  |..f..P......X...|
00000180  66 c1 c8 08 e2 ef b0 0a  e8 c4 ff b0 0d e8 bf ff  |f...............|
00000190  66 61 c3 24 0f 04 30 3c  39 76 02 04 07 e8 af ff  |fa.$..0<9v......|
000001a0  c3 b4 00 cd 16 c3 0a 0d  48 46 53 2b 20 70 61 72  |........HFS+ par|
000001b0  74 69 74 69 6f 6e 20 65  72 72 6f 72 00 0a 0d 45  |tition error...E|
000001c0  72 72 6f 72 20 6c 6f 61  64 69 6e 67 20 62 6f 6f  |rror loading boo|
000001d0  74 65 72 00 00 00 00 00  00 00 00 00 00 00 00 00  |ter.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by oldfred on 2010-01-18
Your boot config is a little mixed up. You have your 100mb windows boot partition on a different drive than the windows install. I cannot tell if it is sdb or sde MBR that is the windows boot.

You have grub2 installed on two drives. sda looks correct and like it should boot. But sometimes grub has to be reinstalled. The install of grub2 in sdc points to a UUID 63... that does not exist, so it will not boot.

I prefer to have each operating system on different drives with that drives's MBR set to boot that drive. You have windows on two drives (boot from one and run from another) and Ubuntu on two drives. As long as both drives work it is usable but if one drive has issues neither will work. Also having grub on the same drive as Ubuntu saves some time booting as grub has a minor bug that adds 20-30 seconds to boot if it is not on the same drive.

I would try reinstalling grub to see if that gets it working but you may want to consider reinstalling to clean things up. I am not sure if the GPT partition affects anything.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by weizguy on 2010-01-18
OK, reinstalled the Grub2 boot loader, will restart in a minute.

If it doesn't work, does anyone know how to zero out all of the drives so I can start a fresh install?  I don't know why Windows 7 used another disk as a partition.  Should I only connect the hard drive that I plan to use for each install?

Connect one, install Leopard, disconnect it, connect another HD, install Windows, then re-connect all of them and install Ubuntu?  Or will something mess up?

---

### Post by weizguy on 2010-01-18
That didn't work :(

I really have no problem starting over, but does anyone know the best order to do things?

I have a 150gb SATA for Windows 7 along with a 1TB SATA for Windows storage.

I have a 150gb SATA for Snow Leopard along with another 1TB SATA for Leopard storage.

I have a 320gb IDE for Ubuntu.

I have both SATA and IDE DVD drives to use for install (IDE seems to work for Leopard).

Anyone know the best method to erase the HD's?  Apparently GParted didn't work, unless I did something wrong of course...

---

### Post by oldfred on 2010-01-18
this says gparted can handle your gpt partitions, I have not used them but gather that since MBR type partitions have a hard max of 2TB that we will soon have to convert new very large drives.
[http://www.ibm.com/developerworks/linux/library/l-gpt/](http://www.ibm.com/developerworks/linux/library/l-gpt/)

Most systems seem to install to the drive set as boot by the BIOS. So I would set a drive to boot in BIOS and then install to that drive.

Don't know about  Snow Leopard but I would install windows before Ubuntu and then Ubuntu last with its drive set to boot first. Grub2 should find all the other systems.

---

### Post by weizguy on 2010-01-18
I am currently zeroing out all of my drives (long process). After that, I will start with Snow Leopard with only the one HD connected. Then I will disconnect the drive and only connect another drive to install Windows 7. After that, I will connect all of the drives and install Ubuntu to the 320gb drive (with BIOS to start with that drive).
 
At my current rate, I should be done by midnight  :popcorn:
 
I will post if it works. Thanks for the help so far.

---

### Post by presence1960 on 2010-01-18
> **weizguy said:**
> I am currently zeroing out all of my drives (long process). After that, I will start with Snow Leopard with only the one HD connected. Then I will disconnect the drive and only connect another drive to install Windows 7. After that, I will connect all of the drives and install Ubuntu to the 320gb drive (with BIOS to start with that drive).
 
At my current rate, I should be done by midnight  :popcorn:
 
I will post if it works. Thanks for the help so far.

When you install windows make sure you go into BIOS and make whatever disk you are putting windows onto first boot in the hard disk boot order as windows will always write it's bootloader to the first disk that boots. if you do this that 100 MB System reserved (boot partition) will be on the same disk as the windows install.

I would put GRUB2 on MBR of the disk that has Ubuntu on it. Then make that disk boot first in the hard disk boot order in BIOS. To choose where to put GRUB click the Advanced tab at the Ready to install window. See below pic.

---

### Post by weizguy on 2010-01-18
Thanks for the tip, it make sense :)

I have a new problem (Maybe 2).  I zeroed out a drive, then in the middle of my second drive, the computer froze.  I restarted it, and it takes about 5 minutes before it will boot to the CD (first problem).  I can't seem to zero out that drive now as it gives me an error (second problem).

The slow start really sucks, any ideas?

---

### Post by presence1960 on 2010-01-18
> **weizguy said:**
> Thanks for the tip, it make sense :)

I have a new problem (Maybe 2).  I zeroed out a drive, then in the middle of my second drive, the computer froze.  I restarted it, and it takes about 5 minutes before it will boot to the CD (first problem).  I can't seem to zero out that drive now as it gives me an error (second problem).

The slow start really sucks, any ideas?

what do you mean by zero out. Are you using something like dban or dd command? That really is not necessary. All you really need to do is format the disk with gparted and then do the install.

---

### Post by weizguy on 2010-01-18
I am zeroing the drives out with Data Lifeguard Diagnostics from Western Digital (all drives are WD).  I am zeroing them out because I am starting from scratch and Gparted formatting didn't seem to work before.

---

### Post by weizguy on 2010-01-19
The slow start was due to a bad drive.  I disconnected it and it worked.  WD is sending me a new one.  In the meantime, I have Windows 7 running.  I will install Ubuntu after I get my new HD.

Again, thanks for the help, this is a very useful, helpful, and responsive community :)

---

### Post by presence1960 on 2010-01-19
> **weizguy said:**
> The slow start was due to a bad drive.  I disconnected it and it worked.  WD is sending me a new one.  In the meantime, I have Windows 7 running.  I will install Ubuntu after I get my new HD.

Again, thanks for the help, this is a very useful, helpful, and responsive community :)

Glad you found out the problem, now you just gotta wait for the new HDD.

---

