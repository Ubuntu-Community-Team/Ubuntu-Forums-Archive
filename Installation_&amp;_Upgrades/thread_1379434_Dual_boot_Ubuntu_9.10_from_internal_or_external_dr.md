---
title: "Dual boot Ubuntu 9.10 from internal or external drive"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by decopeland on 2010-01-12
I have Ubuntu 9.10 installed on Asus 900A internal ssd.  I installed Ubuntu 9.10 on external drive (also ssd in USB closure) after removing the internal drive during install.  It boots from the external drive as long as the internal drive is removed.  But when I install the internal and with the BIOS showing the external drive as first boot, it will boot from the internal drive.  I would like to either have a dual boot or default to the external drive whenever it is attached.

---

### Post by oldfred on 2010-01-12
Plug both drives in and download & run this script to see where everything is at. You can download from a working install or the liveCd.

Boot Info Script courtesy of forum member meierfra.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions:  louieb's
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download:
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by Herman on 2010-01-12
I have some new scripts that can be used to set up your GRUB2 automatically for you, just download the tar.gz file, right-click on it an click 'extract here'. 
Open the folder and click on the 00_start_here file.
There's an option in it specifically for setting up booting to other drives including USBs.
It will make your job easy for you.

The download link is in this web page, [http://members.iinet.net/~herman546/p20.html]("http://members.iinet.net/%7Eherman546/p20.html")

---

### Post by Bartender on 2010-01-12
Wow, herman, did you make all the guides on that page??

---

### Post by Herman on 2010-01-12
Yes.

I hope people are able to find them okay.

GRUB2 is a really great boot loader but I think it's being under-rated simply because not enough people know how to make use of its amazing features.

I was hoping somebody might make a nice GUI program for it, like SUM. It's taking a long time for SUM to add much support for GRUB2. The impression I got from reading the SUM developers website is that SUM won't be adding much GRUB2 support until GRUB2 settles a bit, sometime after Lucid is released with all the new booting improvements that will bring.

There are a lot of people who probably don't want to be kept waiting that long, so I thought that I'd throw together a few quick scripts people can use for the meantime.
I hope they help people.

---

### Post by raymondh on 2010-01-12
as always .. incredible!  Thanks Herman.

Raymond

---

### Post by drs305 on 2010-01-12
I look forward to using these scripts. Right now using Karmic I have grub version 1.97~beta-1ubuntu5, which I believe is from the standard repositories. Your scripts are based on -1ubuntu4 and thus won't run (by your own design) until you update them.

Being familiar with your work, I know these are going to be extremely useful to both experienced and inexperienced users. Thanks.

---

### Post by Herman on 2010-01-12
:D Thanks drs305,
I wasn't aware there was a new GRUB update already.
I'll be on the road for the next couple of weeks but I'll try to get time to make an updated version of those scripts pretty soon.
I'll run apt-get update before I go so I can see if there will be many changes I'll need to make. If we're lucky it might turn out that I won't need to make too many alterations and I can fix it before I leave.

---

### Post by decopeland on 2010-01-13
> **oldfred said:**
> Plug both drives in and download & run this script to see where everything is at. You can download from a working install or the liveCd.

Boot Info Script courtesy of forum member meierfra.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions:  louieb's
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download:
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

RESULTS.txt:
```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 1.97 is installed in the MBR of /dev/sdc and looks on the same drive 
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

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

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

Disk /dev/sda: 32.3 GB, 32296140800 bytes
255 heads, 63 sectors/track, 3926 cylinders, total 63078400 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd65316e1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    60,388,334    60,388,272  83 Linux
/dev/sda2          60,388,335    63,071,189     2,682,855   5 Extended
/dev/sda5          60,388,398    63,071,189     2,682,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 249     3,967,487     3,967,239   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x892d892d

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     7,405,964     7,405,902  83 Linux
/dev/sdc2           7,405,965     7,871,849       465,885   5 Extended
/dev/sdc5           7,406,028     7,871,849       465,822  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6caefb2b-304e-4f9a-9aba-d1a740aa33c4" TYPE="ext4" 
/dev/sda5: UUID="ca531240-90ae-4477-abae-51656419a329" TYPE="swap" 
/dev/sdb1: UUID="8856-755D" TYPE="vfat" 
/dev/sdc1: UUID="a69a4f8e-7201-43ad-91c5-52b7e8ae80ed" TYPE="ext4" 
/dev/sdc5: UUID="5f06e2be-4778-4151-9c5c-0f28bc2edba9" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dael)
/dev/sdb1 on /media/8856-755D type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc1 on /media/a69a4f8e-7201-43ad-91c5-52b7e8ae80ed type ext4 (rw,nosuid,nodev,uhelper=devkit)


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
search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
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
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
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
UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca531240-90ae-4477-abae-51656419a329 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/initrd.img-2.6.31-18-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-18-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro single 
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=a69a4f8e-7201-43ad-91c5-52b7e8ae80ed /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=5f06e2be-4778-4151-9c5c-0f28bc2edba9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 1.97 is installed in the MBR of /dev/sdc and looks on the same drive 
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

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

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

Disk /dev/sda: 32.3 GB, 32296140800 bytes
255 heads, 63 sectors/track, 3926 cylinders, total 63078400 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd65316e1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    60,388,334    60,388,272  83 Linux
/dev/sda2          60,388,335    63,071,189     2,682,855   5 Extended
/dev/sda5          60,388,398    63,071,189     2,682,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 249     3,967,487     3,967,239   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x892d892d

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     7,405,964     7,405,902  83 Linux
/dev/sdc2           7,405,965     7,871,849       465,885   5 Extended
/dev/sdc5           7,406,028     7,871,849       465,822  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6caefb2b-304e-4f9a-9aba-d1a740aa33c4" TYPE="ext4" 
/dev/sda5: UUID="ca531240-90ae-4477-abae-51656419a329" TYPE="swap" 
/dev/sdb1: UUID="8856-755D" TYPE="vfat" 
/dev/sdc1: UUID="a69a4f8e-7201-43ad-91c5-52b7e8ae80ed" TYPE="ext4" 
/dev/sdc5: UUID="5f06e2be-4778-4151-9c5c-0f28bc2edba9" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dael)
/dev/sdb1 on /media/8856-755D type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc1 on /media/a69a4f8e-7201-43ad-91c5-52b7e8ae80ed type ext4 (rw,nosuid,nodev,uhelper=devkit)


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
search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
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
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
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
UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca531240-90ae-4477-abae-51656419a329 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/initrd.img-2.6.31-18-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-18-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro single 
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=a69a4f8e-7201-43ad-91c5-52b7e8ae80ed /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=5f06e2be-4778-4151-9c5c-0f28bc2edba9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 1.97 is installed in the MBR of /dev/sdc and looks on the same drive 
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

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

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

Disk /dev/sda: 32.3 GB, 32296140800 bytes
255 heads, 63 sectors/track, 3926 cylinders, total 63078400 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd65316e1

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    60,388,334    60,388,272  83 Linux
/dev/sda2          60,388,335    63,071,189     2,682,855   5 Extended
/dev/sda5          60,388,398    63,071,189     2,682,792  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2032 MB, 2032664576 bytes
64 heads, 63 sectors/track, 984 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                 249     3,967,487     3,967,239   b W95 FAT32


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x892d892d

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     7,405,964     7,405,902  83 Linux
/dev/sdc2           7,405,965     7,871,849       465,885   5 Extended
/dev/sdc5           7,406,028     7,871,849       465,822  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="6caefb2b-304e-4f9a-9aba-d1a740aa33c4" TYPE="ext4" 
/dev/sda5: UUID="ca531240-90ae-4477-abae-51656419a329" TYPE="swap" 
/dev/sdb1: UUID="8856-755D" TYPE="vfat" 
/dev/sdc1: UUID="a69a4f8e-7201-43ad-91c5-52b7e8ae80ed" TYPE="ext4" 
/dev/sdc5: UUID="5f06e2be-4778-4151-9c5c-0f28bc2edba9" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dael)
/dev/sdb1 on /media/8856-755D type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc1 on /media/a69a4f8e-7201-43ad-91c5-52b7e8ae80ed type ext4 (rw,nosuid,nodev,uhelper=devkit)


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
search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
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
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro  vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 6caefb2b-304e-4f9a-9aba-d1a740aa33c4
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 ro single  vga=769
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
UUID=6caefb2b-304e-4f9a-9aba-d1a740aa33c4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ca531240-90ae-4477-abae-51656419a329 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/initrd.img-2.6.31-18-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-18-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-17-generic root=/dev/sda1 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    linux    /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro single 
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=a69a4f8e-7201-43ad-91c5-52b7e8ae80ed /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=5f06e2be-4778-4151-9c5c-0f28bc2edba9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/initrd.img-2.6.31-17-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-17-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
```

---

### Post by decopeland on 2010-01-13
> **Herman said:**
> I have some new scripts that can be used to set up your GRUB2 automatically for you, just download the tar.gz file, right-click on it an click 'extract here'. 
Open the folder and click on the 00_start_here file.
There's an option in it specifically for setting up booting to other drives including USBs.
It will make your job easy for you.

The download link is in this web page, [http://members.iinet.net/~herman546/p20.html]("http://members.iinet.net/%7Eherman546/p20.html")

Herman, 00_start_here.sh file would not run.  I opened README so I believe grub_fun_scripts was extracted correctly.  I must not have the correct GRUB file.

---

### Post by Leppie on 2010-01-13
if you run update-grub again with the external drive attached, the kernel versions on the external drive should be added to the main grub menu as well:
```
sudo update-grub
```

or if you want the menu with both drives only to show when the external drive is attached, at boot go into the grub menu and boot manually into the system on the external drive. this should be something like this:
```
set root=(hd1,1)
insmod linux
insmod ext2
linux /vmlinuz root=/dev/sdc1 ro		
initrd /initrd.img		
boot
```

then once in the system issue the following commands to install grub to the mbr of the external drive and regenerate the grub.cfg:
```
sudo grub-install --recheck /dev/sdc
sudo update-grub
```

---

### Post by drs305 on 2010-01-13
> **decopeland said:**
> Herman, 00_start_here.sh file would not run.  I opened README so I believe grub_fun_scripts was extracted correctly.  I must not have the correct GRUB file.

Try it from the command line. Change into the directory in which the scripts are located and start it this way:
```

sudo ./00_start_here.sh 
or:
sudo bash ./00_start_here.sh 

```

I don't know if you need sudo to start it but at some point you will need your password.

Also, you might check in Synaptic to see which version of Grub 2 you have. Until Herman updates the script, it will only work on the 1.97~beta-1ubuntu4 version, but -1ubuntu5 has been released and if you updated in the last day or two it will tell you the versions are incompatible with the script.

Even so, you can still see if the script will run.

---

### Post by oldfred on 2010-01-13
Leppie has the right corrections. The problem is your grub.cfg in the external refers to sda1 which is back to the internal drive. Was this because the internal was not plugged in when you installed to the external?

Set the internal to boot first and it should boot. The update grub will add the external to the internals bootmenu. Then you should be able to get into the externals install to run the update grub to reinstall to sdc and correct the grub.cfg in sdc. Then with the external set first in BIOS it should boot.

---

### Post by decopeland on 2010-01-13
> **oldfred said:**
> Leppie has the right corrections. The problem is your grub.cfg in the external refers to sda1 which is back to the internal drive. Was this because the internal was not plugged in when you installed to the external?

Set the internal to boot first and it should boot. The update grub will add the external to the internals bootmenu. Then you should be able to get into the externals install to run the update grub to reinstall to sdc and correct the grub.cfg in sdc. Then with the external set first in BIOS it should boot.

I removed the internal drive when I installed OS to the external drive.  Are you saying that if the internal drive had been present during the install to the external drive, the boot order would have been external first (if present) and then default to internal drive if the external drive is not connected?  I would rather try that than trying to change the existing grub file.  Changing looks pretty daunting.

---

### Post by oldfred on 2010-01-13
Depends on how the BIOS is set. And I have seen several posters where grub automatically installed to the internal. I do not know if they had the external set as first in BIOS or grub just wanted to be on the internal. There is an advanced button about the screen where if finalizes the partitions that lets you specify which drive to put grub on. If you reinstall I would be sure to use that and make sure I knew which drive is sda & which is sdb.

The reinstall of grub should not be that difficult per leppies commands. You should just have to type them in.

---

### Post by decopeland on 2010-01-14
> **oldfred said:**
> Depends on how the BIOS is set. And I have seen several posters where grub automatically installed to the internal. I do not know if they had the external set as first in BIOS or grub just wanted to be on the internal. There is an advanced button about the screen where if finalizes the partitions that lets you specify which drive to put grub on. If you reinstall I would be sure to use that and make sure I knew which drive is sda & which is sdb.

The reinstall of grub should not be that difficult per leppies commands. You should just have to type them in.

My purpose in having an OS on the external drive is to serve as a backup.  As I understand your post I may have a problem.  Normally I would be using the internal drive but, in the event of internal drive failure, I want to plug in the external drive and be up and running.  If GRUB is on the internal drive I would not be able to get the external drive running.  If GRUB is on the external drive that drive would have to be connected in order to boot from the internal drive.  Do I have that correct?  Does that change any of your advice?

---

### Post by oldfred on 2010-01-14
If you want to normally boot the internal then just leave that first in BIOS. Your grub on the internal must point the the install on the internal. On a update grub with the external installed it will also find that install and add it to the menu. If the external is not installed that menu item of course will not work, but will not create a problem otherwise.

The external should have grub pointing to the external's install. On an update-grub it will also find the internal and allow booting either if the external is plugged in and set to boot first. You do not have to set the external to be first, just boot it from the internal occasionally to update it.

---

### Post by decopeland on 2010-01-14
> **oldfred said:**
> If you want to normally boot the internal then just leave that first in BIOS. Your grub on the internal must point the the install on the internal. On a update grub with the external installed it will also find that install and add it to the menu. If the external is not installed that menu item of course will not work, but will not create a problem otherwise.

The external should have grub pointing to the external's install. On an update-grub it will also find the internal and allow booting either if the external is plugged in and set to boot first. You do not have to set the external to be first, just boot it from the internal occasionally to update it.

With external drive attached, at terminal typed sudo update-grub
Got the following response:
Generating grub.cfg...
Found linux image:  /boot/vmlinuz-2.6.31-18-generic
Found initrd image:  /boot/initrd.img-2.6.31-18-generic
(then -17, -16, -15, -14)
Found memtest86+ image:  /boot/memtest86+.bin
Found Ubuntu 9.10 (9.10) on /dev/sdb1
grub-probe: error:  Cannot find GRUB for /dev/sdb1.  Check your device.map
(repeated several times)

There is a grub.cfg in the grub folder under boot folder on Filesystem of my 4gb external drive.  What do I need to do to get the GRUB for internal to recognize the GRUB of the external drive?  You will have to be pretty specific.  I am not certain what Leppie means when he says "if you want the menu with both drives only to show when the external drive is attached, at boot go into the grub menu and boot manually into the system on the external drive. this should be something like this:
     Code:
     set root=(hd1,1)
insmod linux
insmod ext2
linux /vmlinuz root=/dev/sdc1 ro        
initrd /initrd.img        
boot

---

### Post by oldfred on 2010-01-14
Probably in all the plugging and unplugging drives, your device.map only has one drive listed.

  Check your device.map

It is in /boot/grub

My portable only has one:
(hd0)    /dev/sda

But you can edit and add the second linein the same format but hd1 and sdb

---

### Post by Leppie on 2010-01-14
> **decopeland said:**
> I am not certain what Leppie means when he says "if you want the menu with both drives only to show when the external drive is attached, at boot go into the grub menu and boot manually into the system on the external drive. this should be something like this:
     Code:
     set root=(hd1,1)
insmod linux
insmod ext2
linux /vmlinuz root=/dev/sdc1 ro        
initrd /initrd.img        
boot
if you want to see menu entries for systems present on both drives only if you're booting with the usb drive plugged in, you have to use the grub prompt at boot to get into your system on the external drive. i don't know about grub legacy, but with grub2 you have to press "c" when the menu is displayed to get to the grub prompt.

---

### Post by decopeland on 2010-01-15
> **oldfred said:**
> Probably in all the plugging and unplugging drives, your device.map only has one drive listed.

  Check your device.map

It is in /boot/grub

My portable only has one:
(hd0)    /dev/sda

But you can edit and add the second linein the same format but hd1 and sdb

Tried to change device.map
Error message "Read only"
Reinstalled Ubuntu to external drive with internal drive present.  Installed and booted from external drive.  With external drive connected I can boot from either.  With external drive disconnected and booting, I get message GRUB loading.  error:no such disk  grub rescue>
The original GRUB file seems to be on the internal drive.  BIOS has the internal drive as a boot device.  What do I do now?

---

### Post by Leppie on 2010-01-15
> **decopeland said:**
> Tried to change device.map
Error message "Read only"
Reinstalled Ubuntu to external drive with internal drive present.  Installed and booted from external drive.  With external drive connected I can boot from either.  With external drive disconnected and booting, I get message GRUB loading.  error:no such disk  grub rescue>
The original GRUB file seems to be on the internal drive.  BIOS has the internal drive as a boot device.  What do I do now?
if you want the 2 different boot menu's (systems for both ext. + int. when ext. drive is connected and systems for int. drive only when ext. drive is not connected) you need to install grub2 to the mbr of the external drive:
```
sudo grub-install /dev/sdb
```
then boot into the system on the internal drive and re-install the internal drive's system's grub to the mbr of the internal drive:
```
sudo grub-install /dev/sda
```
like this, you will only be presented with the systems on the external drive when the external drive is plugged in at boot.

to edit device.map you can use your editor with root permissions, for example:
```
gksudo gedit /boot/grub/device.map
```

---

### Post by decopeland on 2010-01-15
> **Leppie said:**
> if you want the 2 different boot menu's (systems for both ext. + int. when ext. drive is connected and systems for int. drive only when ext. drive is not connected) you need to install grub2 to the mbr of the external drive:
```
sudo grub-install /dev/sdb
```then boot into the system on the internal drive and re-install the internal drive's system's grub to the mbr of the internal drive:
```
sudo grub-install /dev/sda
```like this, you will only be presented with the systems on the external drive when the external drive is plugged in at boot.

to edit device.map you can use your editor with root permissions, for example:
```
gksudo gedit /boot/grub/device.map
```

At this point I can boot from either drive.   Now when it boots I am shown a menu with several versions of Linux (Ubuntu Linux-image 2.16.31-14, and 15, and 16, etc.) and recovery modes for each and a memory test.  This is shown for both drives (although the external drive skipped 15 and 16).  The menu is the same whether the external drive is connected or not.  Is there a way to configure it so that it boots from external drive when it is connected and from the internal drive when the external is not connected and skip this menu page?   I don't understand what the BIOS plays in this matter.  If the external drive is connected it will appear in the list of Hard Disk Drives under the Boot tab.  I can move the external drive to 1st drive and it will then be shown as first bootable drive in the Priority list.  But the menu is unchanged and I can still boot from the internal drive.  However if the external drive is not connected, there is no Hard Disk Drive list and the internal drive is the first bootable drive in the Priority list.  Connect the external drive again and it automatically becomes the 2nd listed in the Hard Disk Drives.  And then I don't understand the role of device.map.

---

### Post by decopeland on 2010-01-20
Folks, I have managed to mess something up.  I removed the old kernels from the boot menu (went to Synaptic and searched for the numbers) on the internal drive.  That worked so well (boot menu did not display with external drive unplugged) I decided to do that for the external drive.  Trouble.  Get error message to load the kernel when I tried to boot from the external drive.  So I reinstalled Ubuntu to the external drive with the internal drive in place.  Now I can only boot with the external drive connected.  If not connected I get error message no such disk, grub rescue>  I have updated GRUB on both drives-doesn't help.  Any suggestions?  Reinstall with the internal drive removed?

---

### Post by Leppie on 2010-01-20
what you need to do is the following:
- boot into the install on the internal drive
- re-install grub2 into the mbr of the internal drive
- regenerate the grub.cfg of the install on the internal drive
- reboot into the install on the external drive
- re-install grub2 into the mbr of the external drive
- regenerate the grub.cfg for the install on the external drive
at this point you should have 2 iidentical grub2 menus on both the internal and external drive.
if you want to show a different menu (showing only the os's present on the internal drive), boot into the install of the internal drive, unmount and disconnect the external drive and regenerate the grub.cfg file, set your bios to boot from usb first.

---

### Post by decopeland on 2010-01-20
> **Leppie said:**
> what you need to do is the following:
- boot into the install on the internal drive
- re-install grub2 into the mbr of the internal drive
- regenerate the grub.cfg of the install on the internal drive
- reboot into the install on the external drive
- re-install grub2 into the mbr of the external drive
- regenerate the grub.cfg for the install on the external drive
at this point you should have 2 iidentical grub2 menus on both the internal and external drive.
if you want to show a different menu (showing only the os's present on the internal drive), boot into the install of the internal drive, unmount and disconnect the external drive and regenerate the grub.cfg file, set your bios to boot from usb first.

No change.  Whenever I update grub on the internal drive it finds Ubuntu 9.10 on /dev/sdb1 but cannot find GRUB drive on /dev/sdb1.  Updating grub on external drive seems to work as expected.  After identifying the two kernels on external drive, it finds Ubuntu 9.10 on /dev/sda1 and then done.  Is there a problem having 2.6.31-18 on the internal drive and 2.6.31-17 on the external drive?
The biggest problem at this point is not being able to boot from the internal drive unless the external drive is connected.  I don't want to have to have it connected in order to get the machine to operate.  Perhaps, I don't understand what is meant by "booting into install."  I open a terminal window and type sudo apt-get install grub2

---

### Post by Leppie on 2010-01-20
since grub is installed properly into the mbr of your external drive, do the following:
- boot into the install on the internal drive
- unmount ***and disconnect*** your external drive
- install grub into the mbr of the internal drive
```
sudo grub-install --recheck /dev/sda
```
- regenerate your grub.cfg:
```
sudo update-grub
```

grub should now be installed into the mbr of the internal drive as well and its menu should not have entries for your install on the external drive.

---

### Post by decopeland on 2010-01-20
> **Leppie said:**
> since grub is installed properly into the mbr of your external drive, do the following:
- boot into the install on the internal drive
- unmount ***and disconnect*** your external drive
- install grub into the mbr of the internal drive
```
sudo grub-install --recheck /dev/sda
```- regenerate your grub.cfg:
```
sudo update-grub
```grub should now be installed into the mbr of the internal drive as well and its menu should not have entries for your install on the external drive.

Perfect-just what I was looking for.  I do have to change the hard drive in BIOS because the external drive is added at the bottom of the list if the machine boots up with the external drive disconnected.  One more question:  Is there some reason I should not remove Ubuntu, Linux 2.6.31-14 from the list on the external drive now that I am using 2.6.31-17 on that drive?  Why won't that drive update to -18 like the internal drive?  (I guess that is actually two questions.)  Thanks Leppie for your help.

---

### Post by Leppie on 2010-01-20
> **decopeland said:**
> One more question:  Is there some reason I should not remove Ubuntu, Linux 2.6.31-14 from the list on the external drive now that I am using 2.6.31-17 on that drive?  Why won't that drive update to -18 like the internal drive?  (I guess that is actually two questions.)  Thanks Leppie for your help.
you're welcome, we're here to help each other :)
the 14 kernel is basically the one kernel that's least likely to create issues on systems as it is the default stock kernel.
the system on the internal drive most likely doesn't have "proposed" and "backports" repos selected. the current stable kernel is 17 (i just ran update manager;))

---

### Post by decopeland on 2010-02-02
I am back again with what I hope is a simple question.  I liked the install on my external drive better than the one on the internal drive.  Using Clonezilla (which I find to be a nice program), I created an image of the external drive and installed it on the internal drive.  What that included was the boot menu for the external drive.  How do I get rid of the menu with the external drive disconnected and booting from the internal drive.  I did not have any menu before the change.

---

