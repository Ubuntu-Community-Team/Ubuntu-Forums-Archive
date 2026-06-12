---
title: "error no such device:####..... after install"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by crashpc on 2009-12-17
I just installed 9.10 on a compaq evo n410c. I already have xp pro on it. I set it up as a dual boot. The installation appeared to go ok. After it installed it prompted me to restart and remove disk. When I got to the boot screen I chose ubuntu and I received the following error "error no such device: 22d36bdc-d4e3-4ed1-be38-f76bf3a323bd" If I restart and choose xp that still works ok. 

Thanks

---

### Post by presence1960 on 2009-12-18
> **crashpc said:**
> I just installed 9.10 on a compaq evo n410c. I already have xp pro on it. I set it up as a dual boot. The installation appeared to go ok. After it installed it prompted me to restart and remove disk. When I got to the boot screen I chose ubuntu and I received the following error "error no such device: 22d36bdc-d4e3-4ed1-be38-f76bf3a323bd" If I restart and choose xp that still works ok. 

Thanks

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by crashpc on 2009-12-18
Thanks. I'll get that for you. Here's something that may help. At the boot screen I hit e to edit. I saw the error there with this message in front " search --no-floppy --fs -uuid --set" then the error number. If I delete that line I can now boot into ubuntu.  There is no floppy drive on the laptop. Now my problem is when I reboot I still get the error. How do I edit that boot file so it doesn't keep looking for a floppy? I will get you the info you asked too.
Thanks.

---

### Post by crashpc on 2009-12-18
Update. after a little research I edited the grub.cfg like in this thread post #8.
[http://ubuntuforums.org/showthread.php?t=1194714&highlight=edit+grub+no+floppy+drive](http://ubuntuforums.org/showthread.php?t=1194714&highlight=edit+grub+no+floppy+drive)
and it worked. If I should do anything else please let me know.
Thanks

---

### Post by nbotticelli on 2009-12-18
I have the same exact error on an old Gateway Tablet M275 that I just installed Ubuntu 9.10 on earlier today.

I pressed and took out the same line which lets it boot up fine but then I have to do it again after each reboot.

Where do I go to edit the config file permanently?

---

### Post by crashpc on 2009-12-18
nbotticelli, click on the link in my post above, #4. Then go to post#8 of that thread. It worked for me.

---

### Post by nbotticelli on 2009-12-18
> **crashpc said:**
> Update. after a little research I edited the grub.cfg like in this thread post #8.
[http://ubuntuforums.org/showthread.php?t=1194714&highlight=edit+grub+no+floppy+drive](http://ubuntuforums.org/showthread.php?t=1194714&highlight=edit+grub+no+floppy+drive)
and it worked. If I should do anything else please let me know.
Thanks

Thank You! Hopefully this helps; looks like it'll break again after a new kernal update.

---

### Post by crashpc on 2009-12-18
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr.mbr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb0378c02

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   210,178,394   210,178,332   7 HPFS/NTFS
/dev/sda2         210,178,395   312,576,704   102,398,310   5 Extended
/dev/sda5         210,178,458   309,588,614    99,410,157  83 Linux
/dev/sda6         309,588,678   312,576,704     2,988,027  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="20482BAE482B81A0" TYPE="ntfs" 
/dev/sda5: UUID="22d36bdc-d4e3-4ed1-be38-f76bf3a323bd" TYPE="ext4" 
/dev/sda6: UUID="0972bd82-cac2-40bb-9698-d98cd3565d9a" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

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


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set 22d36bdc-d4e3-4ed1-be38-f76bf3a323bd
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 22d36bdc-d4e3-4ed1-be38-f76bf3a323bd
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=22d36bdc-d4e3-4ed1-be38-f76bf3a323bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 22d36bdc-d4e3-4ed1-be38-f76bf3a323bd
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=22d36bdc-d4e3-4ed1-be38-f76bf3a323bd ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 22d36bdc-d4e3-4ed1-be38-f76bf3a323bd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=22d36bdc-d4e3-4ed1-be38-f76bf3a323bd ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 22d36bdc-d4e3-4ed1-be38-f76bf3a323bd
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=22d36bdc-d4e3-4ed1-be38-f76bf3a323bd ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 20482bae482b81a0
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=22d36bdc-d4e3-4ed1-be38-f76bf3a323bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0972bd82-cac2-40bb-9698-d98cd3565d9a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 107.6GB: boot/grub/grub.cfg
 107.6GB: boot/initrd.img-2.6.31-14-generic
 107.6GB: boot/initrd.img-2.6.31-16-generic
 107.6GB: boot/vmlinuz-2.6.31-14-generic
 107.6GB: boot/vmlinuz-2.6.31-16-generic
 107.6GB: initrd.img
 107.6GB: initrd.img.old
 107.6GB: vmlinuz
 107.6GB: vmlinuz.old
```

---

### Post by crashpc on 2009-12-18
presence1960, I posted the text file you asked for in above post. nbotticelli was right. After upgrade it doesn't boot anymore. Had to do fix in my #4 post again. Now ok. How do I fix this problem with the floppy permanently so I don't have to edit that file every time I do an update?
Thanks again in advance.
PS linux newbie here so a step by step would be appreciated :)

---

