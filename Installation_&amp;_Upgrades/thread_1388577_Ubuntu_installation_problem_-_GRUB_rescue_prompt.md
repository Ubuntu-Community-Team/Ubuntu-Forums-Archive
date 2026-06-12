---
title: "Ubuntu installation problem - GRUB rescue prompt"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by seivwrig on 2010-01-23
I have just install Ubuntu on my computer. All went well until I rebooted. I got the following:

GRUB loading
error: no such disk 
and a grub rescue prompt.

below is the Boot Script Info.

What can be done to fix this problem,

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=b353489c-722d-4593-b935-0ebbde21c7e6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sdi
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdi1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdi2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdi5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdi6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd059d059

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   461,613,599   461,613,537   7 HPFS/NTFS
/dev/sda2         461,613,600   488,391,119    26,777,520   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xae82b8da

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    10,486,223    10,486,161   7 HPFS/NTFS
/dev/sdb2          10,486,224    31,457,663    20,971,440   7 HPFS/NTFS
/dev/sdb3          31,457,664   325,176,767   293,719,104   7 HPFS/NTFS
/dev/sdb4         325,176,768   488,397,167   163,220,400   5 Extended
/dev/sdb5         325,176,831   488,397,167   163,220,337  bc Acronis BackUp


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc021c021

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63   117,210,239   117,210,177   7 HPFS/NTFS


Drive: sdi ___________________ _____________________________________________________

Disk /dev/sdi: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ffc810

Partition  Boot         Start           End          Size  Id System

/dev/sdi1    *             63   933,697,799   933,697,737   c W95 FAT32 (LBA)
/dev/sdi2         933,697,800   976,768,064    43,070,265   5 Extended
/dev/sdi5         933,697,863   974,888,459    41,190,597  83 Linux
/dev/sdi6         974,888,523   976,768,064     1,879,542  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="884C32054C31EE96" LABEL="HP_PAVILION" TYPE="ntfs" 
/dev/sda2: LABEL="HP_RECOVERY" UUID="018B-5B01" TYPE="vfat" 
/dev/sdb1: UUID="821CBA071CB9F5EF" LABEL="RONNIE_WORK" TYPE="ntfs" 
/dev/sdb2: UUID="0054152454151E4A" LABEL="DOWNLOAD" TYPE="ntfs" 
/dev/sdb3: UUID="389474B29474746A" LABEL="MEDIA" TYPE="ntfs" 
/dev/sdb5: LABEL="ACRONIS SZ" UUID="1992-A3B5" TYPE="vfat" 
/dev/sdd1: UUID="6A0BF367BDB4E50F" TYPE="ntfs" 
/dev/sdi1: LABEL="My Book" UUID="A9FD-023E" TYPE="vfat" 
/dev/sdi5: UUID="b353489c-722d-4593-b935-0ebbde21c7e6" TYPE="ext4" 
/dev/sdi6: UUID="716c719c-87c3-4fa1-af7b-eab40460d23a" TYPE="swap" 

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


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sdi5/boot/grub/grub.cfg: ===========================

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
set root=(hd3,5)
search --no-floppy --fs-uuid --set b353489c-722d-4593-b935-0ebbde21c7e6
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
    set root=(hd3,5)
    search --no-floppy --fs-uuid --set b353489c-722d-4593-b935-0ebbde21c7e6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b353489c-722d-4593-b935-0ebbde21c7e6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,5)
    search --no-floppy --fs-uuid --set b353489c-722d-4593-b935-0ebbde21c7e6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b353489c-722d-4593-b935-0ebbde21c7e6 ro single 
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
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 884c32054c31ee96
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 018b-5b01
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Acronis Secure Zone (on /dev/sdb5)" {
    insmod fat
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 1992-a3b5
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdi5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sde5 during installation
UUID=b353489c-722d-4593-b935-0ebbde21c7e6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde6 during installation
UUID=716c719c-87c3-4fa1-af7b-eab40460d23a none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdi5: Location of files loaded by Grub: ===================


 478.0GB: boot/grub/core.img
 478.0GB: boot/grub/grub.cfg
 478.0GB: boot/initrd.img-2.6.31-14-generic
 478.0GB: boot/vmlinuz-2.6.31-14-generic
 478.0GB: initrd.img
 478.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb5

00000000  eb 5e 90 42 4f 4f 54 57  49 5a 30 00 02 40 20 00  |.^.BOOTWIZ0..@ .|
00000010  02 00 00 00 00 f8 00 00  3f 00 10 00 3f 00 00 00  |........?...?...|
00000020  40 8b ba 09 d0 4d 00 00  00 00 00 00 02 00 00 00  |@....M..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 b5 a3 92 19 41  43 52 4f 4e 49 53 20 53  |..)....ACRONIS S|
00000050  5a 20 46 41 54 33 32 20  20 20 10 00 01 00 00 7e  |Z FAT32   .....~|
00000060  fc bd 00 7c 66 bb 00 00  00 00 8e d3 8b e5 fb 8e  |...|f...........|
00000070  db 8e c3 52 32 e4 cd 13  33 ff b4 08 cd 13 72 27  |...R2...3.....r'|
00000080  8a 56 fe 83 e1 3f 89 4e  18 8a ce 41 89 4e 1a b4  |.V...?.N...A.N..|
00000090  41 bb aa 55 cd 13 72 0f  81 fb 55 aa 75 09 d1 e9  |A..U..r...U.u...|
000000a0  73 05 c6 06 83 7d 74 1e  07 66 ff 76 2c 66 58 66  |s....}t..f.v,fXf|
000000b0  50 66 48 66 48 66 3d ed  ff ff 0f 77 44 66 0f b6  |PfHfHf=....wDf..|
000000c0  4e 0d 51 66 f7 e1 66 91  8a 46 10 66 f7 66 24 66  |N.Qf..f..F.f.f$f|
000000d0  03 c1 59 66 50 51 e8 6a  00 be dd 7d 8b fb b9 0b  |..YfPQ.j...}....|
000000e0  00 f3 a6 75 1f f6 05 18  75 1a c7 06 d9 7c eb 1d  |...u....u....|..|
000000f0  ff 77 14 ff 77 1a eb b5  81 7f 68 68 09 0f 84 67  |.w..w.....hh...g|
00000100  01 e9 e4 00 83 c3 20 79  d0 59 66 58 66 40 e2 c3  |...... y.YfXf@..|
00000110  66 58 06 68 e0 1f 07 50  66 c1 e8 07 66 3d ff ff  |fX.h...Pf...f=..|
00000120  ff ff 74 07 66 a3 1e 7d  e8 18 00 5b 83 e3 7f c1  |..t.f..}...[....|
00000130  e3 02 66 26 8b 87 00 7e  66 25 ff ff ff 0f 07 66  |..f&...~f%.....f|
00000140  50 eb b3 66 03 46 1c 66  0f b7 4e 0e 66 03 c1 66  |P..f.F.f..N.f..f|
00000150  89 46 62 bf 05 00 8b 46  64 33 d2 f7 76 18 91 8b  |.Fb....Fd3..v...|
00000160  46 62 f7 76 18 42 87 ca  3b 56 1a 73 18 f7 76 1a  |Fb.v.B..;V.s..v.|
00000170  8a f2 86 c5 c1 e8 02 c0  cc 02 0a c8 0a f4 84 e4  |................|
00000180  b8 01 02 eb 08 8c 46 60  b4 42 be 5a 7c bb 00 7e  |......F`.B.Z|..~|
00000190  8a 56 fe cd 13 73 09 4f  74 4e 32 e4 cd 13 eb b6  |.V...s.OtN2.....|
000001a0  c3 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 0d 4e 6f 6e 2d 73 79  |..........Non-sy|
000001c0  73 74 65 6d 20 64 69 73  6b 2c 20 70 72 65 73 73  |stem disk, press|
000001d0  20 61 6e 79 20 6b 65 79  2e 2e 2e 07 00 46 31 31  | any key.....F11|
000001e0  20 20 20 20 20 53 59 53  be b9 7d ac b4 0e b3 07  |     SYS..}.....|
000001f0  cd 10 ac 84 c0 75 f5 98  cd 16 cd 19 00 00 55 aa  |.....u........U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sde sdf sdg sdh 
```

---

### Post by kansasnoob on 2010-01-23
Ubuntu is on sdi5?

> **[COLOR="Red"]sdi5[/COLOR]**: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

```
a-b-c-d-e-f-g-h-i
1-2-3-4-5-6-7-8-9
```

The ninth drive?

But fstab says:

> # / was on **[COLOR="Red"]/dev/sde5[/COLOR]** during installation
UUID=b353489c-722d-4593-b935-0ebbde21c7e6 /               ext4    errors=remount-ro 0       1
# swap was on **[COLOR="Red"]/dev/sde6[/COLOR]** during installation
UUID=716c719c-87c3-4fa1-af7b-eab40460d23a none            swap    sw              0       0

So naturally grub2 set everything to **[COLOR="Red"](not really because sde should be hd4)[/COLOR]**:

```
set root=(hd3,5)
```

In grub2 drive numbering begins with zero so hd3 = sdd??????????

Assuming you're running the Live CD would you post the output of:

```
sudo fdisk -l
```

BTW that's a lower case L.

I'm just having a hard time even getting my mind around that :confused:

---

### Post by oldfred on 2010-01-23
When you have multiple drives, it is always better to have the boot loader for a operating system in the mbr of the drive the operating system is on. Between BIOS, grub, device.map, and ubuntu drive order can get changed, this is why they want to use UUID's as they have less chance of changing but hdx and sdx may change.Removeable drives seem to be worse at this as they may get renumbered for some reason.

I would reinstall grub2 to the drive that has the ubuntu install. Whether it is sdi or sde or whatever. Just be sure as you reinstall which hdx grub sees it as to know where to install it.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by seivwrig on 2010-01-23
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xd059d059

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30530   230806768+   7  HPFS/NTFS
/dev/sda2           30531       32301    13388760    c  W95 FAT32 (LBA)

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xae82b8da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10403     5243080+   7  HPFS/NTFS
/dev/sdb2           10404       31208    10485720    7  HPFS/NTFS
/dev/sdb3           31209      322596   146859552    7  HPFS/NTFS
/dev/sdb4          322597      484521    81610200    5  Extended
/dev/sdb5          322597      484521    81610168+  bc  Unknown

Disk /dev/sdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc021c021

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        7296    58605088+   7  HPFS/NTFS

Disk /dev/sdi: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1       58120   466848868+   c  W95 FAT32 (LBA)
/dev/sdi2           58121       60801    21535132+   5  Extended
/dev/sdi5           58121       60684    20595298+  83  Linux
/dev/sdi6           60685       60801      939771   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

---

### Post by kansasnoob on 2010-01-23
Well I was hoping that somehow the Boot Info Script was reading things wrong but that also shows sdi.

Can you please explain the type of installation?

Like is it an external drive?

Were some drives disconnected during installation?

Anything at all that you can think of that might be helpful?

I mean it's showing up on sdi now, fstab saw it as sde, but grub saw it as sdd.

I wonder what's up?

---

### Post by seivwrig on 2010-02-02
It installed on the external drive. I end up having to disconnect the external drive. I re-install and got it to work.

---

