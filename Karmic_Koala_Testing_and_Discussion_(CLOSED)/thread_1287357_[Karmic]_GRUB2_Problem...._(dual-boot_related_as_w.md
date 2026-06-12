---
title: "[Karmic] GRUB2 Problem.... (dual-boot related as well)"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Laibcoms on 2009-10-10
Hi,

   I am having problems currently.  To run through what I did...

[LIST=1]
[*] Disconnected my PATA drive
[*] Left my SATA drive (which is set as Primary/Boot HardDrive)
[*] Fresh Installed Karmic Koala to my usual partition (it deleted Jaunty and installed Karmic)
[*] After that, everything went smoothly.  GRUB2 detected WinXP just fine.
[*] Then tested if WinXP will boot = Success!
[*] Shutdown the PC
[*] Re-inserted my PATA Harddrive
[*] Checked if BIOS detected it correctly as my "Secondary Slave PATA" = Checked
[*] Booted to Ubuntu = success
[*] Booted to XP = failed; gave me this error: "error: invalid signature"
[*] Re-booted to Ubuntu; searched Google and the forums
[/LIST]


When I did fdisk -l for some weird reason, Karmic/GRUB2 did this:
/dev/sda is now my PATA HDrive
/dev/sdb is now my SATA HDrive

So when I try to boot to WinXP it returned the said error "error: invalid signature".

I then removed my PATA HDrive again.
Rebooted to Ubuntu and rebuilt grub (grub-install or something - ie the command that will rebuild it's config file, as instructed in the Ubuntu WIKI).

Then rebooted to XP = success!

I did fdisk -l again, and my SATA Drive is back as /dev/sda

If I put back my PATA, and since as I've read everytime the grub update command is run (for example, kernel updates), it will re-detect the OS, rebuild the config, etc.  I ran it again, and it is back to:
/dev/sda as my PATA HDrive
/dev/sdb as my SATA HDrive

WinXP fails to boot once again.

I removed my PATA drive again... then ran the Boot Info Script (as instructed here: [http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3) ).  Here's what I got:
[php]
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb523b523

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,846,935   275,932,439   112,085,505   f W95 Ext d (LBA)
/dev/sda5         163,846,998   275,932,439   112,085,442   7 HPFS/NTFS
/dev/sda3         275,932,440   308,560,454    32,628,015  83 Linux
/dev/sda4         308,560,455   312,576,704     4,016,250  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="BCC01853C01815EC" LABEL="C:" TYPE="ntfs" 
/dev/sda3: UUID="3f7fa1a8-b2de-4e8a-bc31-5eb73d4c8620" TYPE="ext4" 
/dev/sda5: UUID="B084D9D684D99EE2" LABEL="D:" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda3 on /media/3f7fa1a8-b2de-4e8a-bc31-5eb73d4c8620 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sda5 on /media/D: type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/C: type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sda3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="6"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 3f7fa1a8-b2de-4e8a-bc31-5eb73d4c8620
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
  set timeout=13
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-13-generic" {
        recordfail=1
        save_env recordfail
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 3f7fa1a8-b2de-4e8a-bc31-5eb73d4c8620
    linux    /boot/vmlinuz-2.6.31-13-generic root=UUID=3f7fa1a8-b2de-4e8a-bc31-5eb73d4c8620 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-13-generic
}
menuentry "Ubuntu, Linux 2.6.31-13-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 3f7fa1a8-b2de-4e8a-bc31-5eb73d4c8620
    linux    /boot/vmlinuz-2.6.31-13-generic root=UUID=3f7fa1a8-b2de-4e8a-bc31-5eb73d4c8620 ro single 
    initrd    /boot/initrd.img-2.6.31-13-generic
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
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=3f7fa1a8-b2de-4e8a-bc31-5eb73d4c8620 / ext4 errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/sda5 /media/G: ntfs-3g defaults,locale=en_PH.UTF-8 0 0
/dev/sda1 /media/F: ntfs-3g defaults,locale=en_PH.UTF-8 0 0
/dev/sdb5 /media/D: ntfs-3g defaults,locale=en_PH.UTF-8 0 0
/dev/sdb1 /media/C: ntfs-3g defaults,locale=en_PH.UTF-8 0 0

=================== sda3: Location of files loaded by Grub: ===================


 141.2GB: boot/grub/grub.cfg
 141.2GB: boot/initrd.img-2.6.31-13-generic
 141.2GB: boot/vmlinuz-2.6.31-13-generic
 141.2GB: initrd.img
 141.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  eb 63 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.c....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 00 80 01 00 00 00  |u....Y|..1......|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  23 b5 23 b5 00 00 80 01  |...<.u..#.#.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 d8 1a c4 09 00 00  |......?.........|
000001d0  c1 ff 0f fe ff ff 17 1b  c4 09 01 4a ae 06 00 fe  |...........J....|
000001e0  ff ff 83 fe ff ff 18 65  72 10 2f dd f1 01 00 fe  |.......er./.....|
000001f0  ff ff 82 fe ff ff 47 42  64 12 7a 48 3d 00 55 aa  |......GBd.zH=.U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde [/php]For some reason it says: "No known boot loader is installed in the MBR of /dev/sda".
GRUB2 shows up just fine, with just the SATA drive active (which is currently /dev/sda).

I do not understand though why there is no boot loader but GRUB2 is showing up on boot.  O_O

Any help?  Thanks!!

---

### Post by Laibcoms on 2009-10-10
*sigh* no matter what I do, I always get the /dev/sda and /dev/sdb swap.

As stated in my previous post above, my /dev/sda should be my SATA (160GB) which is setup as my primary HD/boot in BIOS.
And my /dev/sdb should be my PATA (80GB)

But Ubuntu Karmic keeps switching the two, and so it is affecting GRUB and Windows XP.

As you can see below:
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2dd2b41f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,156,224    78,156,162   7 HPFS/NTFS
/dev/sda2          78,156,225   156,296,384    78,140,160   f W95 Ext d (LBA)
/dev/sda5          78,156,288   156,296,384    78,140,097   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb523b523

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sdb2         163,846,935   275,932,439   112,085,505   f W95 Ext d (LBA)
/dev/sdb5         163,846,998   275,932,439   112,085,442   7 HPFS/NTFS
/dev/sdb3         275,932,440   308,560,454    32,628,015  83 Linux
/dev/sdb4         308,560,455   312,576,704     4,016,250  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="8E58D05F58D0479B" LABEL="F" TYPE="ntfs" 
/dev/sda5: UUID="BE5404F35404B067" LABEL="G" TYPE="ntfs" 
/dev/sdb1: UUID="BCC01853C01815EC" LABEL="C" TYPE="ntfs" 
/dev/sdb3: UUID="b49811ab-e965-49b2-877c-fc72157f9a83" TYPE="ext4" 
/dev/sdb5: UUID="B084D9D684D99EE2" LABEL="D" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /media/C type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/D type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/home/jc/.Private on /home/jc type ecryptfs (ecryptfs_sig=e7de6967f78d00ee,ecryptfs_fnek_sig=301e837a40bde37d,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/jc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jc)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sdb3/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set b49811ab-e965-49b2-877c-fc72157f9a83
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
menuentry "Ubuntu, Linux 2.6.31-13-generic" {
        recordfail=1
        save_env recordfail
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set b49811ab-e965-49b2-877c-fc72157f9a83
    linux    /boot/vmlinuz-2.6.31-13-generic root=UUID=b49811ab-e965-49b2-877c-fc72157f9a83 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-13-generic
}
menuentry "Ubuntu, Linux 2.6.31-13-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set b49811ab-e965-49b2-877c-fc72157f9a83
    linux    /boot/vmlinuz-2.6.31-13-generic root=UUID=b49811ab-e965-49b2-877c-fc72157f9a83 ro single 
    initrd    /boot/initrd.img-2.6.31-13-generic
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bcc01853c01815ec
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=b49811ab-e965-49b2-877c-fc72157f9a83 / ext4 errors=remount-ro 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/sda1 /media/C ntfs-3g defaults,locale=en_PH.UTF-8 0 0
/dev/sda5 /media/D ntfs-3g defaults,locale=en_PH.UTF-8 0 0

=================== sdb3: Location of files loaded by Grub: ===================


 141.2GB: boot/grub/grub.cfg
 141.2GB: boot/initrd.img-2.6.31-13-generic
 141.2GB: boot/vmlinuz-2.6.31-13-generic
 141.2GB: initrd.img
 141.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  eb 63 90 d0 bc 00 7c fb  50 07 50 1f fc be 1b 7c  |.c....|.P.P....||
00000010  bf 1b 06 50 57 b9 e5 01  f3 a4 cb bd be 07 b1 04  |...PW...........|
00000020  38 6e 00 7c 09 75 13 83  c5 10 e2 f4 cd 18 8b f5  |8n.|.u..........|
00000030  83 c6 10 49 74 19 38 2c  74 f6 a0 b5 07 b4 03 02  |...It.8,t.......|
00000040  ff 00 00 20 01 00 00 00  00 02 fa 90 90 f6 c2 80  |... ............|
00000050  75 02 b2 80 ea 59 7c 00  00 31 00 80 01 00 00 00  |u....Y|..1......|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  be 88 7d e8 24 01 be 05  ||<.t...R..}.$...|
00000090  7c f6 c2 80 74 48 b4 41  bb aa 55 cd 13 5a 52 72  ||...tH.A..U..ZRr|
000000a0  3d 81 fb 55 aa 75 37 83  e1 01 74 32 31 c0 89 44  |=..U.u7...t21..D|
000000b0  04 40 88 44 ff 89 44 02  c7 04 10 00 66 8b 1e 5c  |.@.D..D.....f..\|
000000c0  7c 66 89 5c 08 66 8b 1e  60 7c 66 89 5c 0c c7 44  ||f.\.f..`|f.\..D|
000000d0  06 00 70 b4 42 cd 13 72  05 bb 00 70 eb 73 b4 08  |..p.B..r...p.s..|
000000e0  cd 13 73 0a f6 c2 80 0f  84 d8 00 e9 82 00 66 0f  |..s...........f.|
000000f0  b6 c6 88 64 ff 40 66 89  44 04 0f b6 d1 c1 e2 02  |...d.@f.D.......|
00000100  88 e8 88 f4 40 89 44 08  0f b6 c2 c0 e8 02 66 89  |....@.D.......f.|
00000110  04 66 a1 60 7c 66 09 c0  75 4e 66 a1 5c 7c 66 31  |.f.`|f..uNf.\|f1|
00000120  d2 66 f7 34 88 d1 31 d2  66 f7 74 04 3b 44 08 7d  |.f.4..1.f.t.;D.}|
00000130  37 fe c1 88 c5 30 c0 c1  e8 02 08 c1 88 d0 5a 88  |7....0........Z.|
00000140  c6 bb 00 70 8e c3 31 db  b8 01 02 cd 13 72 29 8c  |...p..1......r).|
00000150  c3 60 1e b9 00 01 8e db  31 f6 bf 00 80 8e c6 fc  |.`......1.......|
00000160  f3 a5 1f 61 ff 26 5a 7c  be 8e 7d e8 44 00 eb 0e  |...a.&Z|..}.D...|
00000170  be 93 7d e8 3c 00 eb 06  be 9d 7d e8 34 00 be a2  |..}.<.....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  23 b5 23 b5 00 00 80 01  |...<.u..#.#.....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 d8 1a c4 09 00 00  |......?.........|
000001d0  c1 ff 0f fe ff ff 17 1b  c4 09 01 4a ae 06 00 fe  |...........J....|
000001e0  ff ff 83 fe ff ff 18 65  72 10 2f dd f1 01 00 fe  |.......er./.....|
000001f0  ff ff 82 fe ff ff 47 42  64 12 7a 48 3d 00 55 aa  |......GBd.zH=.U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```I have no idea how GRUB0.97 got installed in my PATA (80GB), when I do fresh install, I always disconnect the cables of PATA first.

And I do not know why GRUB2 doesn't get installed on SATA (160GB).  The first install, I tried the default detection "hd0".  When I re-installed I chose from the drop-down menu "/dev/sda".  Similar result.

Now I'm suspecting that the culprit is GRUB0.97 that mysteriously got installed in my PATA (80GB) and the missing GRUB2 on SATA (160GB).

I also noticed, the GRUB menu that shows up when booting is GRUB legacy even though it shows "GRUB2 Beta" version stuff.  I'm assuming then that right at the GRUB loading, there is already a mixed-up (to my understanding GRUB reads the Ubuntu partition).

And since Karmic is switching my /dev/sda and /dev/sdb, there really is a mixed-up.

So how do I remove the MBR from my PATA (which shouldn't have an MBR in the first place because it is only my data drive [I don't remember putting one either; and I never installed an OS in that drive]).

I'm all out, and I guess this is as far as my knowledge of these things go.  Need help.

Thanks!!

---

### Post by oldfred on 2009-10-10
At least once you must have kept the Pata drive installed to have grub legacy installed in it.

It looks like the script does not correctly identify grub2. On my machine I installed it to a partition for chainbooting and I get the same message of unidentified bootloader. As long as it works it should be ok.

I doubt that karmic is switching pata & sata drives. The BIOS controls what drive is first and has no idea what operating system is used, it just loads the MBR from the first drive. Sometimes grub & linux do not list the drives in the same order as the BIOS which can cause confusion. Have you checked for a new revision of you motherboard's BIOS?

With my old mother board I had both sata & pata drives and in the beginning I had to reboot half the time as the drive order seemed to depend on which drive spun up first. My new mother board with all sata lets me select which drive. The boot order settings may be in two different places in the BIOS, one for which hard drive and another for devices like the floppy, hard drive, cd, etc.

Having Grub installed in your data drive makes no difference unless it is used for booting, which seems to be the case for you. I have grub installed on three drives and every bootable partition for chainbooting. This allows me to change drive order if one fails and still boot.

If you are not able to in BIOS select the sata drive first you have to update the grub in your pata drive. You can reinstall old grub or install new grub to your pata drive. The first hard drive in BIOS has to have a boot loader unless you use a floppy, USB key or CD as the boot device and laod them before the hard drive.

---

### Post by Laibcoms on 2009-10-11
Yep, that's the only explanation, probably during Hardy because I recall I used the alternate CD installer then.

---------------

That's the weird part..  I checked my BIOS setting and all is well - the first to boot is my SATA, then PATA.  (I went through every setting again just to re-check, everything is still the same as before I installed Karmic.)

Secondly, this is the first time there was a HDD switch.  Pre-Karmic, my SATA is loaded as sda; and my PATA as sdb.  But now with Karmic, there's a switching of harddrive.  I do not know now if it is Karmic or not, since you said it wasn't Karmic.  But, this HDD mounting switch only happened to me first time with Karmic.


There was a kernel update today, and again when grub2 ran os_prober it listed WinXP as being on sdb since that's how it shows on Karmic - in sdb.  WinXP won't load again :p  

I will try that suggestion of updating grub on the PATA drive (or maybe just remove it).

Thanks again!! ^_^

**UPDATE: Oct. 11, 2009 3:46pm (UTC+0800H)**

It appears that Ubuntu Karmic wants to follow the HardDisk placement and skip the BIOS setting altogether.

Here's my hardware setup.
Primary Master - DVD drive
Primary Slave - none
Secondary Master - none
Secondary Slave - PATA 80GB
Tertiary Master - SATA 160GB
Tertiary Slave - none

Ubuntu Karmic follows that, so it shows PATA 80GB as /dev/sda and SATA 160GB as /dev/sdb

**BUT**, Jaunty and earlier releases follows my BIOS setup correctly which is:
Primary HDD / Boot: SATA 160GB
Secondary HDD (non-boot) :: PATA 80GB

That's why I never had problems before.  But with Karmic, I have to disconnect my PATA 80GB literally everytime the system (kernel upgrades for example) runs update-grub2.  And it's a PITA :p  (which will also end up either [a] accidental electrocution; [b] killing my PATA drive).

Now, I do not know if Karmic is really the problem here.. but as far things go, it _is_ Karmic.  GRUB2's os detection relies on the HDD order reported by Karmic.

T_T  I'm drained.....

Last resort... edit GRUB2 and stop it from putting the _wrong_ configuration that Karmic feeds it re: my 2 HDDs.  And GRUB2 is giving me headache right now... I guess due to Karmic insisting on its own HDD order instead of following the user's BIOS setup.   :(:(:(

---

### Post by oldfred on 2009-10-11
I have heard pre Karmic of some people having issues with Ubuntu boot order or Grub boot order not matching BIOS. You seem to be one of these but I am surprised it changed from Jaunty to Karmic.

When we only had Pata drives the jumpers on the drives set boot order, cable select was added and the order was by where on the cable the drive was. Combined Pata & Sata then started to have BIOS settings, but perhaps early BIOS did not totally control hardware settings. Now I can plug a Sata in anywhere and in BIOS determine order.

Also think of Grub or Grub2 as a mini operating system of its own as it controls the computer until you choose which operating system to boot. As long as you can figure out what Grub sees you should be able to set up your system.

---

