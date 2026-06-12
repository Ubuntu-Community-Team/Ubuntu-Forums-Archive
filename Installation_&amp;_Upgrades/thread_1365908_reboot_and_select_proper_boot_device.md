---
title: "reboot and select proper boot device?"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by ?Jake5511 on 2009-12-27
[LEFT]I installed ubuntu the install went smoothly, but when it was done and I rebooted, it came up with this ''**reboot and select proper boot device'' **Am I doing something wrong? please help, thanks!
[/LEFT]

---

### Post by jonest1 on 2009-12-27
You may need to go into your BIOS settings and verify the boot devices.  Ensure the drive where the boot loader resides is in the list.  

If this doesn't work, give more detail.

---

### Post by ?Jake5511 on 2009-12-27
Thats the first thing I did before I came here, I'm booted in on the live cd, I tried reinstalling it with the boot loader on a different drive, and it still said the same thing, I skipped the ''Installing Language Packs'' could that do anything to it? I've tried multiple installations, if you need to know anything else just say thanks for helping.

---

### Post by nerdtron on 2009-12-27
Are you dual booting? If yes, do you have 2 partitions or 2 physical hard drives?

---

### Post by presence1960 on 2009-12-27
Let's not guess what your setup & boot process looks like. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ?Jake5511 on 2009-12-28
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=c04876bc-79b4-468b-a7be-949aa242deb6)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4390a80e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   390,719,487   390,717,440   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd5694482

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    68,356,574    68,356,512  83 Linux
/dev/sdb2          68,356,575    78,156,224     9,799,650   5 Extended
/dev/sdb5          68,356,638    78,156,224     9,799,587  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xce47f864

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   230,259,644   230,259,582  83 Linux
/dev/sdc2         230,259,645   240,107,489     9,847,845   5 Extended
/dev/sdc5         230,259,708   240,107,489     9,847,782  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9AE6994BE6992911" LABEL="Apps" TYPE="ntfs" 
/dev/sdb1: UUID="3bce53fa-092a-453c-b653-c81440e1b5b8" TYPE="ext4" 
/dev/sdb5: UUID="46267f32-8fdb-49c1-837f-f3bebc5b0aea" TYPE="swap" 
/dev/sdc1: UUID="c04876bc-79b4-468b-a7be-949aa242deb6" TYPE="ext4" 
/dev/sdc5: UUID="55ec8d26-88b3-466c-b419-cfc9781575d5" TYPE="swap" 

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
search --no-floppy --fs-uuid --set 3bce53fa-092a-453c-b653-c81440e1b5b8
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
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 3bce53fa-092a-453c-b653-c81440e1b5b8
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3bce53fa-092a-453c-b653-c81440e1b5b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 3bce53fa-092a-453c-b653-c81440e1b5b8
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3bce53fa-092a-453c-b653-c81440e1b5b8 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 342c97cb2c978690
    chainloader +1
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
UUID=3bce53fa-092a-453c-b653-c81440e1b5b8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=46267f32-8fdb-49c1-837f-f3bebc5b0aea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz

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
search --no-floppy --fs-uuid --set c04876bc-79b4-468b-a7be-949aa242deb6
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
    search --no-floppy --fs-uuid --set c04876bc-79b4-468b-a7be-949aa242deb6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c04876bc-79b4-468b-a7be-949aa242deb6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set c04876bc-79b4-468b-a7be-949aa242deb6
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c04876bc-79b4-468b-a7be-949aa242deb6 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 9ae6994be6992911
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 3bce53fa-092a-453c-b653-c81440e1b5b8
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=3bce53fa-092a-453c-b653-c81440e1b5b8 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 3bce53fa-092a-453c-b653-c81440e1b5b8
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=3bce53fa-092a-453c-b653-c81440e1b5b8 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
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
UUID=c04876bc-79b4-468b-a7be-949aa242deb6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=55ec8d26-88b3-466c-b419-cfc9781575d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by presence1960 on 2009-12-28
you have grldr in your Vista boot files. You need to delete that file.

Also you have 9.10 installed on both sdb and sdc hard disks. Which ever one you want to use I would reinstall GRUB2 to the MBR of that disk.

Boot the Ubuntu Live CD, at the menu choose "try ubuntu without any changes..." When the desktop loads open  file browser and mount sda1 device (windows) by highlighting the correct device on the left side of window. When you see the windows directories on right side it is mounted.

Now open a terminal (Applications > Accessories > Terminal) and run ```
gksu nautilus
```
This will open a root filebrowser. Navigate to the windows device and delete the grldr file. Close both file browsers.

In terminal again mount your Ubuntu partition (depending on which one you want to use sdb1 or sdc1) by running ```
sudo mount /dev/sdb1 /mnt
```
for sdb1 or ```
sudo mount /dev/sdc1 /mnt
```
if you want to use sdc1

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
if you used sdb1 above or ```
sudo grub-install --root-directory=/mnt/ /dev/sdc
``` if you used sdc1 above.

Reboot and go into BIOS. Whatever disk you used (either sdb or sdc) in the above commands set that disk as first in hard disk boot order in BIOS. Save changes to CMOS and continue booting into Ubuntu. Once you log in and the desktop loads open a terminal and run ```
sudo update-grub
```

You should be good to go.

---

### Post by ?Jake5511 on 2009-12-28
Thank you thank you thank you! it worked perfectly, I am now an Official ''Ubuntu'' User :p since I have no windows installations anymore :p

---

### Post by presence1960 on 2009-12-28
> **?Jake5511 said:**
> Thank you thank you thank you! it worked perfectly, I am now an Official ''Ubuntu'' User :p since I have no windows installations anymore :p

Glad you got it working! Enjoy Ubuntu.

---

