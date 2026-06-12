---
title: "GRUB Fails to Load Ubuntu 9.10"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by nakile on 2009-12-21
I'm trying to install Ubuntu 9.10 on an old Windows XP system. I just want Ubuntu 9.10 on it.

After two install attempts I keep having the same issue. After the BIOS does its thing I see GRUB trying to start for a split second (just a few words in the upper left corner of the screen), then the monitor blanks and the system does nothing.

I used DBAN to quick erase the whole drive and then installed 9.10 again, but same issue. I reinstalled GRUB using the Live CD, still the same issue.

Ubuntu is installed on the drive, I checked using the Live CD. So I don't see what the issue could be with anything except GRUB or the MBR.

What do you all think?

Thanks in advance!

---

### Post by wilee-nilee on 2009-12-21
What is your computers specs and what do you actually want running on it.

---

### Post by presence1960 on 2009-12-21
> **nakile said:**
> I'm trying to install Ubuntu 9.10 on an old Windows XP system. I just want Ubuntu 9.10 on it.

After two install attempts I keep having the same issue. After the BIOS does its thing I see GRUB trying to start for a split second (just a few words in the upper left corner of the screen), then the monitor blanks and the system does nothing.

I used DBAN to quick erase the whole drive and then installed 9.10 again, but same issue. I reinstalled GRUB using the Live CD, still the same issue.

Ubuntu is installed on the drive, I checked using the Live CD. So I don't see what the issue could be with anything except GRUB or the MBR.

What do you all think?

Thanks in advance!

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by nakile on 2009-12-21
Ok, here's what the script gave me:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000675f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    37,383,254    37,383,192  83 Linux
/dev/sda2          37,383,255    39,102,209     1,718,955   5 Extended
/dev/sda5          37,383,318    39,102,209     1,718,892  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="a5ac71dc-9774-4eee-8561-ae600973db1e" TYPE="ext4" 
/dev/sda5: TYPE="swap" 
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
search --no-floppy --fs-uuid --set a5ac71dc-9774-4eee-8561-ae600973db1e
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
	search --no-floppy --fs-uuid --set a5ac71dc-9774-4eee-8561-ae600973db1e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a5ac71dc-9774-4eee-8561-ae600973db1e ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a5ac71dc-9774-4eee-8561-ae600973db1e
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=a5ac71dc-9774-4eee-8561-ae600973db1e ro single 
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
UUID=a5ac71dc-9774-4eee-8561-ae600973db1e /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

As for the system I'm trying to put this on, here's the [spec page]("http://h10025.www1.hp.com/ewfrf/wc/document?dlc=en&lc=en&product=93920&lang=en&cc=us&docname=c00009542"). Only difference is I've upgraded the RAM to 448MB.

---

### Post by presence1960 on 2009-12-21
your info from the script looks good to me, but the thing that concerns me is your video card. Video area is not my expertise, but I would tend to think that is the problem. Maybe someone else can come along who knows more in that area.

Edit: I found [this]("http://georgia.ubuntuforums.org/showthread.php?t=1329112"). Although the OP could boot he had resolution problems with the same card. maybe this can point you in the right direction.

---

### Post by nakile on 2009-12-22
> **presence1960 said:**
> your info from the script looks good to me, but the thing that concerns me is your video card. Video area is not my expertise, but I would tend to think that is the problem. Maybe someone else can come along who knows more in that area.

Edit: I found [this]("http://georgia.ubuntuforums.org/showthread.php?t=1329112"). Although the OP could boot he had resolution problems with the same card. maybe this can point you in the right direction.
The Live CD runs fine and at 1280x960 (it boots at higher resolution than that but I switch it down). I don't see how this could be causing a boot error?

---

