---
title: "GRUB Loading Error"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by wuzeman on 2009-12-05
When trying to dual boot Windows XP and Ubuntu 9.10 on a Dell PC I encountered a problem, the installation works fine then I am told to restart the computer. I do so then after the Dell Splash screen I get:
GRUB loading.
error: no such disk
grub rescue> _
I used an Ubuntu 9.10 Live CD I got in the mail.
P.S. I installed Ubuntu on an external hard drive.

---

### Post by darkod on 2009-12-05
Not to type everything again, please do what I described in post #2 here
[http://ubuntuforums.org/showthread.php?t=1346798](http://ubuntuforums.org/showthread.php?t=1346798)

and post your results back here.

---

### Post by wuzeman on 2009-12-05
```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=4ae7966f-253a-4c95-a7cd-aa97773ac875)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        64,259        64,197  de Dell Utility
/dev/sda2    *         64,260    71,119,754    71,055,495   7 HPFS/NTFS
/dev/sda3          71,119,755    78,108,029     6,988,275  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2111 MB, 2111864832 bytes
64 heads, 63 sectors/track, 1023 cylinders, total 4124736 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x15761576

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     4,124,735     4,124,673   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f9c6998

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sdc2    *     40,965,750    80,276,804    39,311,055   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0416" TYPE="vfat" 
/dev/sda2: UUID="74E8F0C3E8F08520" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" TYPE="vfat" 
/dev/sdb1: UUID="74A2-1E53" TYPE="vfat" 
/dev/sdc1: UUID="8880007580006C4E" LABEL="Pictures" TYPE="ntfs" 
/dev/sdc2: UUID="1C686B27686AFEC0" LABEL="Music" TYPE="ntfs" 

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


================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
```
That's what I got

---

### Post by darkod on 2009-12-05
Did you install using wubi.exe? You have no Ubuntu 9.10 partition on any disk, you can see they all say XP. Wubi is different type of install and plus I don't know too much about it.
Or your external drive is not plugged in. You said you installed on external drive.

---

### Post by wuzeman on 2009-12-05
Ah yes I forgot to plug my external hard drive back in.

---

### Post by wuzeman on 2009-12-05
```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=4ae7966f-253a-4c95-a7cd-aa97773ac875)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => No known boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdd8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        64,259        64,197  de Dell Utility
/dev/sda2    *         64,260    71,119,754    71,055,495   7 HPFS/NTFS
/dev/sda3          71,119,755    78,108,029     6,988,275  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2111 MB, 2111864832 bytes
64 heads, 63 sectors/track, 1023 cylinders, total 4124736 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x15761576

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     4,124,735     4,124,673   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f9c6998

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sdc2    *     40,965,750    80,276,804    39,311,055   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04457cc4

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   349,670,789   349,670,727   b W95 FAT32
/dev/sdd2         349,670,790   625,137,344   275,466,555   5 Extended
/dev/sdd5         349,670,853   486,223,289   136,552,437  83 Linux
/dev/sdd6         619,129,098   625,137,344     6,008,247  82 Linux swap / Solaris
/dev/sdd7         486,223,353   613,618,739   127,395,387  83 Linux
/dev/sdd8         613,618,803   619,129,034     5,510,232  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0416" TYPE="vfat" 
/dev/sda2: UUID="74E8F0C3E8F08520" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" TYPE="vfat" 
/dev/sdb1: UUID="74A2-1E53" TYPE="vfat" 
/dev/sdc1: UUID="8880007580006C4E" LABEL="Pictures" TYPE="ntfs" 
/dev/sdc2: UUID="1C686B27686AFEC0" LABEL="Music" TYPE="ntfs" 
/dev/sdd5: UUID="f5d00d5d-d371-4760-9d87-7beb1fb78f8b" TYPE="ext4" 
/dev/sdd6: UUID="41476ece-8bc1-4fe2-a77d-69fc59f5af1b" TYPE="swap" 
/dev/sdd7: UUID="4ae7966f-253a-4c95-a7cd-aa97773ac875" TYPE="ext4" 
/dev/sdd8: UUID="1cf08497-5c1a-471d-b282-f0feb7cb9631" TYPE="swap" 

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
/dev/sdd7 on /media/4ae7966f-253a-4c95-a7cd-aa97773ac875 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdd5 on /media/f5d00d5d-d371-4760-9d87-7beb1fb78f8b type ext4 (rw,nosuid,nodev,uhelper=devkit)


================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdd5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set f5d00d5d-d371-4760-9d87-7beb1fb78f8b
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
    search --no-floppy --fs-uuid --set f5d00d5d-d371-4760-9d87-7beb1fb78f8b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f5d00d5d-d371-4760-9d87-7beb1fb78f8b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,5)
    search --no-floppy --fs-uuid --set f5d00d5d-d371-4760-9d87-7beb1fb78f8b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f5d00d5d-d371-4760-9d87-7beb1fb78f8b ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 74e8f0c3e8f08520
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdd5 during installation
UUID=f5d00d5d-d371-4760-9d87-7beb1fb78f8b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd6 during installation
UUID=41476ece-8bc1-4fe2-a77d-69fc59f5af1b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdd5: Location of files loaded by Grub: ===================


 179.0GB: boot/grub/grub.cfg
 179.0GB: boot/initrd.img-2.6.31-14-generic
 179.0GB: boot/vmlinuz-2.6.31-14-generic
 179.0GB: initrd.img
 179.0GB: vmlinuz

=========================== sdd7/boot/grub/grub.cfg: ===========================

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
set root=(hd3,7)
search --no-floppy --fs-uuid --set 4ae7966f-253a-4c95-a7cd-aa97773ac875
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
    set root=(hd3,7)
    search --no-floppy --fs-uuid --set 4ae7966f-253a-4c95-a7cd-aa97773ac875
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4ae7966f-253a-4c95-a7cd-aa97773ac875 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd3,7)
    search --no-floppy --fs-uuid --set 4ae7966f-253a-4c95-a7cd-aa97773ac875
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=4ae7966f-253a-4c95-a7cd-aa97773ac875 ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 74e8f0c3e8f08520
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sde5)" {
    insmod ext2
    set root=(hd3,5)
    search --no-floppy --fs-uuid --set f5d00d5d-d371-4760-9d87-7beb1fb78f8b
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f5d00d5d-d371-4760-9d87-7beb1fb78f8b ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sde5)" {
    insmod ext2
    set root=(hd3,5)
    search --no-floppy --fs-uuid --set f5d00d5d-d371-4760-9d87-7beb1fb78f8b
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=f5d00d5d-d371-4760-9d87-7beb1fb78f8b ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdd7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sde7 during installation
UUID=4ae7966f-253a-4c95-a7cd-aa97773ac875 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde8 during installation
UUID=1cf08497-5c1a-471d-b282-f0feb7cb9631 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdd7: Location of files loaded by Grub: ===================


 248.9GB: boot/grub/grub.cfg
 248.9GB: boot/initrd.img-2.6.31-14-generic
 248.9GB: boot/vmlinuz-2.6.31-14-generic
 248.9GB: initrd.img
 248.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdd

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  c4 7c 45 04 00 00 00 01  |.........|E.....|
000001c0  01 00 0b fe ff ff 3f 00  00 00 47 8d d7 14 00 fe  |......?...G.....|
000001d0  ff ff 05 fe ff ff 86 8d  d7 14 3b 49 6b 10 00 00  |..........;Ik...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
This is what I got with the hard drive plugged in.

---

### Post by darkod on 2009-12-05
Create another results.txt with the drive plugged in.

---

### Post by darkod on 2009-12-05
OK, few things. Look at the beginning of the results where the partitions are listed. sda, sdb etc are drives, and the number sda1 means first partition on it, etc.

sdd is your external drive. First of all you seem to have two separate 9.10 installs, one is at sdd5 with swap partition sdd6, and the other at sdd7 with swap sdd8. Did you install it twice? It doesn't automatically overwrite itself unless you specifically tell it too, to prevent unwanted destruction of the OS.

Also the FAT32 sdd1 partition, the first on the external hdd, is not recognized correctly, you see the info about it is missing, There is some info below that.

Otherwise, with the drive plugged in you should be able to boot the second Ubuntu on sdd7.

PS. What is sdb, some usb stick? It's only 2GB.

---

### Post by ctult on 2009-12-05
Yay!  I solved it!


EDIT: I had the same problem

---

### Post by wuzeman on 2009-12-05
> **darkod said:**
> OK, few things. Look at the beginning of the results where the partitions are listed. sda, sdb etc are drives, and the number sda1 means first partition on it, etc.

sdd is your external drive. First of all you seem to have two separate 9.10 installs, one is at sdd5 with swap partition sdd6, and the other at sdd7 with swap sdd8. Did you install it twice? It doesn't automatically overwrite itself unless you specifically tell it too, to prevent unwanted destruction of the OS.

Also the FAT32 sdd1 partition, the first on the external hdd, is not recognized correctly, you see the info about it is missing, There is some info below that.

Otherwise, with the drive plugged in you should be able to boot the second Ubuntu on sdd7.

PS. What is sdb, some usb stick? It's only 2GB.
Yes, I did install Ubuntu twice, when it didn't work the first time I tried to reinstall it and it still didn't work so that is why there are to installations of it on there.

I believe the FAT32 partition is all the data I previously had on the external hard drive and I cannot think of why it isn't recognized.

I think sdb was some secondary drive that came with the computer so that you could use it to backup your system, I'm not sure.

---

### Post by darkod on 2009-12-05
You need to make a decision. Do you want to delete both ubuntu installs and make another clean install? In this situation you might consider using one of the internal drives for ubuntu and all of the external hdd for data (put the data from one internat drive on it). Of course, you can install again on the external hdd instead of the current two Ubuntu installs.
I have no idea how you are using your computer, this is only a suggestion. Also if that 2GB drive is some kind of usb stick, and is not used regularly, keep it unplugged until you need it.

---

### Post by wuzeman on 2009-12-05
> **darkod said:**
> You need to make a decision. Do you want to delete both ubuntu installs and make another clean install? In this situation you might consider using one of the internal drives for ubuntu and all of the external hdd for data (put the data from one internat drive on it). Of course, you can install again on the external hdd instead of the current two Ubuntu installs.
I have no idea how you are using your computer, this is only a suggestion. Also if that 2GB drive is some kind of usb stick, and is not used regularly, keep it unplugged until you need it.
Ok, I want to delete both installations and their partitions so the hard drive is 300 gigs again then would it be possible to copy the data from an internal hard drive that I use for music to the external drive then put Ubuntu on the old music drive?:confused:

---

### Post by darkod on 2009-12-05
Yes, the only question is what's working at the moment. :) Can you boot into XP or that doesn't work too?
If it doesn't work, you can still delete the ubuntu partitions on the external hdd using the Ubuntu CD, then copy the data from one of the internal drives to the external, and then install on the internal.

---

### Post by wuzeman on 2009-12-05
I cannot boot into XP, the first Ubuntu installation, or the second one. But I can run the liveCD from the Ubuntu disk otherwise it has the GRUB loading error when I try to boot from my hard drive.

---

### Post by darkod on 2009-12-05
You can do it from the cd. Open Gparted (System-Administration). In the top right corner there is drop-down box to select the drive. It should be called the same, /dev/sdd. That's your external.
Select that drive and it will show you graphical image of your partition and a list in the middle of the screen. If any partitions have a symbol like keys, then it's mounted and ca't be deleted. Right click on that partition and select unmount (swapoff for swap). The keys will be gone.
Select one by one all partition from sdd5 to sdd8 and click the red X mark button (or right click on each partition and select Delete).
You should do that for sdd2 too but NOT sdd1. That's your FAT32 data partition. Gparted will show you everything once you start it.
After you select all of them for deletion you need to click the big green check mark in Gparted to apply the operations. After that you will end up with the FAT32 /dev/sdd1 and the rest of space unallocated. Select the unallocated space and create new NTFS partition (put a label on it if you want to). It's better to be NTFS, both windows and ubuntu can work with it. You need to click the green check mark again and it will create the rest of the drive as single NTFS partition.
After that quit Gparted and in Places you will be able to see your internal drives and the external. Open both and copy what ever you want.

NOTE: When working with Gparted be very careful. It's not difficult but double check everything before clicking. Don't delete the wrong partition(s). :)

---

### Post by wuzeman on 2009-12-05
Alright I copied the contents of my picture hard drive to the new partition on the external drive, now would I install Ubuntu from the liveCD to the sd3 or whatever it is?

---

### Post by darkod on 2009-12-05
Yes, but first VERY important question: You copied everything you wanted right? Because the data on that drive will be destroyed.
If yes, proceed. Another slightly bad thing is that both internal drives are similar size, you have to make sure you use the music drive and not the windows drive (ubuntu will overwrite windows). :)
I noticed one was 40GB and the other 41GB, so you need the slightly bigger one. If they are still called the same it should be /dev/sdc but don't count on that, look at them and compare the size.

Unmount (right click on it and eject) the external drive first, it doesn't need to be plugged in during the install, in fact it better not be.

Then you should be fine just double clicking the icon on desktop Install Ubuntu. When it asks where to install select the Erase and use entire disk option and make sure you select the correct disk. Also remember it name (for example /dev/sdc). At the last step of the install before clicking Install button click on Advanced and it will show you where it plans to install grub2 bootloader. Make sure it's the same drive, eg /dev/sdc.
When install finishes it will ask to reboot, when it reboots go into BIOS and set this drive to be first in boot order.
And you should be happily using Ubuntu after that, I hope. :)

---

### Post by wuzeman on 2009-12-05
Ok I'm going to try this and I will post back if it works. Thank you for all your help, I can't wait. :D

---

### Post by wuzeman on 2009-12-05
Ok I installed as directed but GRUB still wouldn't load so now I'm reinstalling it, on the same 41.1 gig drive after I format it. But I'm putting the GRUB loader on my main C: drive to see if that works instead. I believe it will.:D

---

### Post by darkod on 2009-12-05
Did you also change the order of drives in BIOS? Maybe grub2 was installed and would work correctly on drive3 but remember the BIOS setting is still booting from your drive1.

---

### Post by wuzeman on 2009-12-05
Ah, that may have been the problem. It had the same GRUB loading error at the top of the first page. It's a bit late now but that was probably it.:oops:

---

### Post by darkod on 2009-12-05
No problem, no harm done. It should still work fine, just in BIOS find the HDDs boot order and adjust as needed for the 41.1GB to be first.

PS. Too late here, going to bed but I hope you sort it out. Cheers.

---

### Post by wuzeman on 2009-12-05
Alright it didn't work. :(
So I'm rereinstalling to the 41 gig and putting the boot loader in /dev/sdc. I don't know how to change which hard drive my computer boots from though, I will try typing /dev/sdc in the command prompt that comes up and see if that works. If not I will post my boot process order thing again.

---

### Post by oldfred on 2009-12-05
The computer always boots from whatever drive the BIOS defines as first. It used to be master/slave settings on old pata drives but now with Sata the BIOS controls it.

There are two places in the BIOS on drives. One selects devices, HD, CD, floppy as what to boot. Another place  will say which hard drive if you have more than one. I was surprised on my system as I had trouble getting it to boot a USB key. I had lots of selections for USB, USB floppy, USB HD, USB CD but none of them let me boot my USB key. Then I looked at hard drive selection one time when I had the key pluged in and it was a choice. BIOS considered the USB key a hard drive in my BIOS.

---

### Post by wuzeman on 2009-12-05
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=d8f5cfb6-daf5-4279-a62b-819250cd9185)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 1.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        64,259        64,197  de Dell Utility
/dev/sda2    *         64,260    71,119,754    71,055,495   7 HPFS/NTFS
/dev/sda3          71,119,755    78,108,029     6,988,275  db CP/M / CTOS / ...


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2111 MB, 2111864832 bytes
64 heads, 63 sectors/track, 1023 cylinders, total 4124736 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x15761576

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     4,124,735     4,124,673   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f9c6998

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    76,903,154    76,903,092  83 Linux
/dev/sdc2          76,903,155    80,292,869     3,389,715   5 Extended
/dev/sdc5          76,903,218    80,292,869     3,389,652  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0416" TYPE="vfat" 
/dev/sda2: UUID="74E8F0C3E8F08520" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" TYPE="vfat" 
/dev/sdc1: UUID="2d154653-cbf0-4f65-932a-d3a52b7ffd4e" TYPE="ext4" 
/dev/sdc5: UUID="bfa7478b-6cc2-4abc-8839-f40bb4ac58ae" TYPE="swap" 
/dev/sdb1: UUID="74A2-1E53" TYPE="vfat" 

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


================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root=(hd2,1)
search --no-floppy --fs-uuid --set 2d154653-cbf0-4f65-932a-d3a52b7ffd4e
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
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 2d154653-cbf0-4f65-932a-d3a52b7ffd4e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2d154653-cbf0-4f65-932a-d3a52b7ffd4e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 2d154653-cbf0-4f65-932a-d3a52b7ffd4e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2d154653-cbf0-4f65-932a-d3a52b7ffd4e ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 74e8f0c3e8f08520
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=2d154653-cbf0-4f65-932a-d3a52b7ffd4e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=bfa7478b-6cc2-4abc-8839-f40bb4ac58ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```
I got this after I installed on 41 gig drive and put the GRUB in /dev/sdc. I will try the thing from fred.

---

### Post by redcann600 on 2009-12-05
Hello, I am brand new to Ubuntu, so forgive me if I am I bit slow.

I did an install of  Ubuntu 9.10 on the main drive and after the reload I encounter the following:
GRUB loading.
error: out of disk
grub rescue> 

I created the install disk from iso image on the Ubuntu site and burn it to CD.

In reading this thread and others, it seems my problem is similar but different since I'm not dual booting.  I downloaded "boot_info_script039.sh" but not sure how to utilize it.

Appreciate any pointers for the newbie.  I understand the problem but not sure how to fix it.

Thanks.

---

### Post by wuzeman on 2009-12-05
> **redcann600 said:**
> Hello, I am brand new to Ubuntu, so forgive me if I am I bit slow.

I did an install of  Ubuntu 9.10 on the main drive and after the reload I encounter the following:
GRUB loading.
error: out of disk
grub rescue> 

I created the install disk from iso image on the Ubuntu site and burn it to CD.

In reading this thread and others, it seems my problem is similar but different since I'm not dual booting.  I downloaded "boot_info_script039.sh" but not sure how to utilize it.

Appreciate any pointers for the newbie.  I understand the problem but not sure how to fix it.

Thanks.
Read the second post of this thread and use the link to utilize it. And I don't know how to fix it either :(.

---

### Post by darkod on 2009-12-06
@wuzeman
It seems you did good installing Ubuntu, it looks correctly installed on /dev/sdc and grub2 is on /dev/sdc. Your only pain now seems to be finding the setting in BIOS to make the sdc disk first in boot order. Look around in BIOS, it must be there.
Until you change that you are still "calling" the bad grub on sda.
Another alternative, if your efforts to change BIOS to /dev/sdc fail, is to install grub2 also on /dev/sda but it will call your /dev/sdc ubuntu of course.
Boot with the ubuntu cd, like you were already doing in the LiveCD environment. Open terminal and run:

sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That should install the new grub2 from your /dev/sdc installation to /dev/sda. Reboot and check if it's working.

---

### Post by wuzeman on 2009-12-06
> **darkod said:**
> @wuzeman
Boot with the ubuntu cd, like you were already doing in the LiveCD environment. Open terminal and run:

sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

That should install the new grub2 from your /dev/sdc installation to /dev/sda. Reboot and check if it's working.
The thing is, I'm not sure where grub is. I specified it to go to /dev/sdc but when you say /sdc1 it may not be there. I opened gparted and there were 3 partitions, ext4, extended, and linux-swap. /sdc1, /sdc2, and /sdc5, which one do I put in the terminal command?

---

### Post by darkod on 2009-12-06
Don't worry, I checked your latest results.txt file you posted. In the mount command /dev/sdc1 is used because that's the root (/) partition and it needs to be mounted. It's like C: in windows, the main one.
In the second command you tell grub2 to install on /dev/sda (the first drive) because you want it to replace the not working copy of grub2 there.
That is alternative to making drive3 first in BIOS. drive1 can remain first as it is now, but there will be new grub2 there. Run the commands as they are. Reboot and see how it goes.

---

### Post by wuzeman on 2009-12-06
I got this when I did the command, is it right?

---

### Post by darkod on 2009-12-06
Looks perfect. You see, No Error Reported.
Reboot (without the cd) and see if it boots the new good grub2 and if it's working as expected.

---

### Post by wuzeman on 2009-12-06
Ok, I shut down, took the disc out, closed the tray, hit enter, it shut down normally, I booted it back up, but there was still an error. :|

---

### Post by darkod on 2009-12-06
I'm running out of ideas. Your drive1 has Dell Utility partition on it and sometimes that messes with the boot sector. It has been reported also for some HP machines. Not sure if that can create the problem and that's why I preferred the boot loader on drive3 to be used. I suspect the utility partition is at fault. It all looks fine otherwise.
Are you sure you can't locate the setting in BIOS to make drive3 first in boot order as we discussed earlier? That is the final recommendation from me.
Sorry, but there is nothing to fix as far as I can see. Just make it boot from drive3, you don't need to run any commands or anything, you just installed new ubuntu to drive3.

---

### Post by wuzeman on 2009-12-06
You wouldn't happen to know how to change what hard drive a computer with BIOS A02 boots with would you?

---

### Post by darkod on 2009-12-06
I guess you can enter BIOS right? It's either hittin F2, F10, F12 oe Del button during boot (but fast). The needed button should be displayed on screen.
Then inside BIOS look at Advanced BIOS settings, or Boot settings if they are separate.
Once you go inside, there are two types of setting for boot order. One is as device, CD, HDD, USB, etc. You don't need to touch that. But another setting should be which of the multiple drives is first, second, etc. In that setting you need to put drive3 as first, before the other 40GB currently first.
Then with Esc you exit the menues, save the BIOS settings you changed (inside BIOS hittin F10 usually offers to save them and exit). Once inside the BIOS there is info which button to press for what.

---

### Post by wuzeman on 2009-12-06
When I open BIOS the only things I found that might relate are drive configuration, hard-disk drive sequence, and boot sequence. :confused:

---

### Post by darkod on 2009-12-06
Hard Disk drive sequence

---

### Post by wuzeman on 2009-12-06
I get 1. System BIOS boot devices and 2. USB device (not installed)

---

### Post by darkod on 2009-12-06
Look inside System BIOS boot devices. If it doesn't show any way to move the hard drives around, look into that other option Boot Sequence. Look around until you find something making up the hdd boot sequence that you can change their order.

PS. If you have a manual it might help. It might have images and what settings to choose.

---

### Post by redcann600 on 2009-12-06
Below is the results from boot_info_script*.sh.  I have tried changing the BIOS to pick the main drive, which didn't seem to help.  Any suggestions to changes that need to be made.  Thanks.:confused:



============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Grub 0.93 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /grub/menu.lst 
                       /boot/grub/grub.conf /grub/grub.conf

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /etc/fstab

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f00e3

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   485,420,039   485,419,977  83 Linux
/dev/sda2         485,420,040   488,392,064     2,972,025   5 Extended
/dev/sda5         485,420,103   488,392,064     2,971,962  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 76.9 GB, 76869918720 bytes
255 heads, 63 sectors/track, 9345 cylinders, total 150136560 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63        32,129        32,067  83 Linux
/dev/sdb2              32,130     1,044,224     1,012,095  82 Linux swap / Solaris
/dev/sdb3           1,044,225    10,827,809     9,783,585  83 Linux
/dev/sdb4          10,827,810   150,127,424   139,299,615  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="2d26871e-cdc6-4ea2-9807-cb7eb3ddc13b" TYPE="ext4" 
/dev/sda5: UUID="2d046582-4889-45c0-aeed-a38db170bd82" TYPE="swap" 
/dev/sdb1: UUID="33d14446-ffa9-42c7-a93d-e336cb47ad26" TYPE="ext2" 
/dev/sdb2: UUID="1fce1a86-fe04-4a12-a698-0492be367423" TYPE="swap" 
/dev/sdb3: UUID="6a6933bd-af5e-4625-bb0f-a9f1d6b68f37" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: UUID="0b2fad72-1c54-4964-9b6f-f276b0e83030" SEC_TYPE="ext2" TYPE="ext3" 
/dev/ramzswap0: TYPE="swap" 

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


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 2d26871e-cdc6-4ea2-9807-cb7eb3ddc13b
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
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2d26871e-cdc6-4ea2-9807-cb7eb3ddc13b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2d26871e-cdc6-4ea2-9807-cb7eb3ddc13b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 2d26871e-cdc6-4ea2-9807-cb7eb3ddc13b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=2d26871e-cdc6-4ea2-9807-cb7eb3ddc13b ro single 
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
UUID=2d26871e-cdc6-4ea2-9807-cb7eb3ddc13b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2d046582-4889-45c0-aeed-a38db170bd82 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

========================== sdb1/boot/grub/grub.conf: ==========================

#
# Sample boot menu configuration file
#

# Boot automatically after 30 secs.
timeout 30

# By default, boot the first entry.
default 0

splashimage=(hd0,0)/grub/splash.xpm.gz

# For booting GNU/Linux
title  Gentoo Linux 2.6.13-gentoo-r5
root (hd0,0)
kernel (hd0,0)/bzImage.2.6.13-gentoo-r5 root=/dev/hda3

title  Gentoo Linux 2.6.11-gentoo-r6
root (hd0,0)
kernel (hd0,0)/bzImage.2.6.11-gentoo-r6 root=/dev/hda3

title  Gentoo Linux 2.4.28-gentoo-r7
root (hd0,0)
kernel (hd0,0)/bzImage.2.4.28-gentoo-r7 root=/dev/hda3

============================= sdb1/grub/grub.conf: =============================

#
# Sample boot menu configuration file
#

# Boot automatically after 30 secs.
timeout 30

# By default, boot the first entry.
default 0

splashimage=(hd0,0)/grub/splash.xpm.gz

# For booting GNU/Linux
title  Gentoo Linux 2.6.13-gentoo-r5
root (hd0,0)
kernel (hd0,0)/bzImage.2.6.13-gentoo-r5 root=/dev/hda3

title  Gentoo Linux 2.6.11-gentoo-r6
root (hd0,0)
kernel (hd0,0)/bzImage.2.6.11-gentoo-r6 root=/dev/hda3

title  Gentoo Linux 2.4.28-gentoo-r7
root (hd0,0)
kernel (hd0,0)/bzImage.2.4.28-gentoo-r7 root=/dev/hda3

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.conf
    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
# $Header: /home/cvsroot/gentoo-src/rc-scripts/etc/fstab,v 1.14 2003/10/13 20:03:38 azarah Exp $
#
# noatime turns off atimes for increased performance (atimes normally aren't
# needed; notail increases performance of ReiserFS (at the expense of storage
# efficiency).  It's safe to drop the noatime options if you want and to 
# switch between notail and tail freely.

# <fs>              <mountpoint>    <type>      <opts>              <dump/pass>

# NOTE: If your BOOT partition is ReiserFS, add the notail option to opts.
/dev/hda1        /boot        ext2        noauto,noatime        1 2
/dev/hda3        /        ext3        noatime            0 1
/dev/hda2        none        swap        sw            0 0
/dev/hda4        /home    ext3        noatime            0 2
/dev/cdroms/cdrom0    /mnt/cdrom    iso9660        noauto,ro,user        0 0
/dev/fd0        /mnt/floppy    auto        noauto            0 0

# NOTE: The next line is critical for boot!
none            /proc        proc        defaults        0 0

# glibc 2.2 and above expects tmpfs to be mounted at /dev/shm for
# POSIX shared memory (shm_open, shm_unlink). 
# (tmpfs is a dynamically expandable/shrinkable ramdisk, and will
#  use almost no memory if not populated with files)
# Adding the following line to /etc/fstab should take care of this:

none            /dev/shm    tmpfs        defaults        0 0

---

### Post by wuzeman on 2009-12-06
I found a Boot Device Menu,
1. Normal
2. Primary Master Drive
3. Hard-Disk  Drive C:
4. IDE CD-ROM Device

5. System Setup *BIOS
6. IDE Drive Diagnostics
7. Boot to Utility Partition *I think it's that 2.1 gig drive

---

### Post by wuzeman on 2009-12-06
This is taking to long, how can I delete GRUB from my hard drive so I can just load windows normally? I'm going to download Jaunty Jackalope and see if that works better.

---

### Post by darkod on 2009-12-06
You can read how to restore XP bootloader here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by redcann600 on 2009-12-06
I believe that I'm getting much closer, with your help (much thanks). ;)  At the GNU GRUB splash screen and I need to change the drive reference but am unsure what to change.

When booting I get the following error:

cannot open root device "hda3" or unknown block (3,3)

Please append a correct "root=" boot option

kernal panic-not sync: VFS: unable to mount root fs on unknown-block (3,)


Here is, what I believe, I need to change.  Not sure if it should be (hd0,1) or something else.

root (hd0,0)
kernel (hd0,0)/bzImage.2.6.13-gentoo-r5 root=/dev/hda3

---

### Post by darkod on 2009-12-06
> **redcann600 said:**
> I believe that I'm getting much closer, with your help (much thanks). ;)  At the GNU GRUB splash screen and I need to change the drive reference but am unsure what to change.

When booting I get the following error:

cannot open root device "hda3" or unknown block (3,3)

Please append a correct "root=" boot option

kernal panic-not sync: VFS: unable to mount root fs on unknown-block (3,)


Here is, what I believe, I need to change.  Not sure if it should be (hd0,1) or something else.

root (hd0,0)
kernel (hd0,0)/bzImage.2.6.13-gentoo-r5 root=/dev/hda3

Not sure how this combination with Gentoo will work but just to remind you that partitions are not called /dev/hda3 any more. And /dev/sda3 doesn't exist as partition, look in the results.
I would suggest to try setting the 250GB drive as first in boot options in BIOS. Then boot the Ubuntu 9.10 LiveCD and in terminal try to reinstall grub2 with:
sudo mount /dev/sda1 /mnt
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

Reboot without the cd and see if it helps.

---

### Post by redcann600 on 2009-12-06
Tried the following:

sudo mount /dev/sda1 /mnt
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda 

and it loads from hard disk and and go to the following on screen:

GNU GRUB verison 1.97~beta4

[Minimal BASH-like line editing is supported. For the first word, TAB list possible command completions.  Anywhere else TAB lists possible device/file completions.  ]

sh:grub>

---

