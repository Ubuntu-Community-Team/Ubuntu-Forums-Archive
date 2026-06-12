---
title: "GRUB doesn't exist"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by Norami on 2010-01-06
Ok. I believe this is partly (or fully) my fault. I have two internal 500GB hard drives in my system. On the first, I had 9.04 installed, and used the second as storage. Well, I decided to try out 9.10, so I installed it on the second hard drive. Basically I was running 9.04 and 9.10 side-by-side. I just wanted to make sure I liked 9.10, before fully upgrading. Once I decided to move over to 9.10, I just copied all my files and the like from the first drive to the second. Once done with that, I re-formatted the first hard drive to become storage once again. I got 9.10 set-up the way I like it, got my Firefox bookmarks and settings put together, installed all the various apps, etc. Updates came in, I installed them and restarted. But what's this? GRUB is no longer in existence on this system!

I'm assuming that installing 9.10 beside 9.04 allowed for them to use GRUB off the first drive? And in re-formatting it, I got rid of GRUB? That's the only scenario that makes sense. I can boot off LiveCD fine, I just can't get 9.10 to boot, mainly because there is no GRUB.

So, is there any way to install GRUB through a LiveCD, or some other method? I suppose I could just wipe everything, and install a fresh copy of 9.10 again, but I'd like to avoid that.

---

### Post by presence1960 on 2010-01-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Norami on 2010-01-06
Here's the contents of the file:

```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d2b0d2b

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e30f2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   961,683,029   961,682,967  83 Linux
/dev/sdb2         961,683,030   976,768,064    15,085,035   5 Extended
/dev/sdb5         961,683,093   976,768,064    15,084,972  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sdb1: UUID="47df2530-438f-43a5-88dd-de6abc02185c" TYPE="ext4" 
sdb5: UUID="9bb7be76-04e3-495d-8f54-7e2425c6de3a" TYPE="swap" 

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
search --no-floppy --fs-uuid --set 47df2530-438f-43a5-88dd-de6abc02185c
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
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 47df2530-438f-43a5-88dd-de6abc02185c
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=47df2530-438f-43a5-88dd-de6abc02185c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 47df2530-438f-43a5-88dd-de6abc02185c
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=47df2530-438f-43a5-88dd-de6abc02185c ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 47df2530-438f-43a5-88dd-de6abc02185c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=47df2530-438f-43a5-88dd-de6abc02185c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 47df2530-438f-43a5-88dd-de6abc02185c
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=47df2530-438f-43a5-88dd-de6abc02185c ro single 
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
menuentry "Ubuntu 9.04, kernel 2.6.28-17-server (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f5901ab-c52c-45e3-a586-175217457478
    linux /boot/vmlinuz-2.6.28-17-server root=UUID=4f5901ab-c52c-45e3-a586-175217457478 ro quiet splash
    initrd /boot/initrd.img-2.6.28-17-server
}
menuentry "Ubuntu 9.04, kernel 2.6.28-17-server (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f5901ab-c52c-45e3-a586-175217457478
    linux /boot/vmlinuz-2.6.28-17-server root=UUID=4f5901ab-c52c-45e3-a586-175217457478 ro single
    initrd /boot/initrd.img-2.6.28-17-server
}
menuentry "Ubuntu 9.04, kernel 2.6.28-17-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f5901ab-c52c-45e3-a586-175217457478
    linux /boot/vmlinuz-2.6.28-17-generic root=UUID=4f5901ab-c52c-45e3-a586-175217457478 ro quiet splash
    initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f5901ab-c52c-45e3-a586-175217457478
    linux /boot/vmlinuz-2.6.28-17-generic root=UUID=4f5901ab-c52c-45e3-a586-175217457478 ro single
    initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-server (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f5901ab-c52c-45e3-a586-175217457478
    linux /boot/vmlinuz-2.6.28-16-server root=UUID=4f5901ab-c52c-45e3-a586-175217457478 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-server (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f5901ab-c52c-45e3-a586-175217457478
    linux /boot/vmlinuz-2.6.28-16-server root=UUID=4f5901ab-c52c-45e3-a586-175217457478 ro single
    initrd /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f5901ab-c52c-45e3-a586-175217457478
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=4f5901ab-c52c-45e3-a586-175217457478 ro quiet splash
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f5901ab-c52c-45e3-a586-175217457478
    linux /boot/vmlinuz-2.6.28-16-generic root=UUID=4f5901ab-c52c-45e3-a586-175217457478 ro single
    initrd /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f5901ab-c52c-45e3-a586-175217457478
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=4f5901ab-c52c-45e3-a586-175217457478 ro quiet splash
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f5901ab-c52c-45e3-a586-175217457478
    linux /boot/vmlinuz-2.6.28-11-generic root=UUID=4f5901ab-c52c-45e3-a586-175217457478 ro single
    initrd /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4f5901ab-c52c-45e3-a586-175217457478
    linux /boot/memtest86+.bin 
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
UUID=47df2530-438f-43a5-88dd-de6abc02185c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=9bb7be76-04e3-495d-8f54-7e2425c6de3a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
```

---

### Post by presence1960 on 2010-01-06
You want to do 2 things. Go into BIOS and set sdb as first disk to boot in hard disk boot order. Save changes to CMOS and continue booting  off the 9.10 Live CD.

Now you want to reinstall GRUB. When you boot the Live CD choose "try ubuntu without any changes...", when the desktop loads open a terminal and run ```
sudo mount /dev/sdb1 /mnt
```
This will mount your Ubuntu partition.

Next run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```
This will put GRUB on MBR of sdb disk. Now reboot. As long as the sdb disk is set to first in the hard disk boot order in BIOS GRUB will load.

---

### Post by Norami on 2010-01-06
Awesome! That worked perfectly. Thank you very much.

The only weird thing to me is the GRUB menu loads every time. It shows the kernels of the old OS even though it doesn't exist anymore. Any way to change that?

---

### Post by darkod on 2010-01-06
Try:
sudo update-grub

It should figure out the 9.04 is not there any more.

---

### Post by Norami on 2010-01-06
Yup. That did the trick.

Thanks to the both of you, again.

---

### Post by presence1960 on 2010-01-06
> **darkod said:**
> Try:
sudo update-grub

It should figure out the 9.04 is not there any more.

+1

If that does not remove them then you can do so from Synaptic Package manager. Mark for complete removal linux-headers-2.x.xx-xx and linux-image-2.xx.xx-xx that match the old kernels you wish to remove.

The karmic kernels are 2.6.31-xx. You want to keep at minimum the two most recent kernels and their recovery options in case one borks you can still boot from the other. I would remove all kernels not 2.6.31-xx as they are not karmic kernels.

---

### Post by presence1960 on 2010-01-06
> **Norami said:**
> Yup. That did the trick.

Thanks to the both of you, again.

Great!! I posted my last reply and as I was doing so I got the email notification of your post. Enjoy Ubuntu:popcorn:

---

