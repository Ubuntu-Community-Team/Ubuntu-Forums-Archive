---
title: "OK, now its definately screwed"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by koglaa on 2009-12-31
I highly doubt this is normal...

So, yeah, ubuntu is screwed at first, w/e.  Atleast it works and I can use office/browse web.

So, I just decided to upgrade to 9.10, hoping it would increase system performance.  Seems to have ruined ubuntu more like.

Installed, w/e, restarted.  BOOM, it's dead.  It automatically starts up with a console with the following error:

```
init: unreadaheaed main process (2565) terminated with status 5
mountall:/proc: unable to mount: device or resource busy
mountall:/proc/self/mountinfo: No suck file or directory
mountall: root filesystem isn't mounted
init: mountall main process (3566) terminated with status 1... See More
General error mounting filesystems
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry
Give root password for maintenance
(or type Control-D to continue)
```

Yeah, please help.  I'm newbie when it comes to ubuntu/linux/terminal/console.  You'll need to explain this in noob terms.

Thanks

---

### Post by Herman on 2009-12-31
You can fix it by booting your Ubuntu CD and opening 'System', 'Administration', GParted', right-click on your Ubuntu partition and click 'check'.
Confirm in two different 'Apply' buttons.
Wait a few minutes while the file system check is runnning.
When it's finished, reboot into your operating system, it should be all fixed.

---

### Post by koglaa on 2009-12-31
... I can't boot from CD and I'm locked out of BIOS

---

### Post by koglaa on 2010-01-02
Bump?

---

### Post by boscopup on 2010-01-02
I'm also having this problem after upgrading to 9.10. I previously had 8.04 and upgraded to 8.10 and then 9.04 with no problems. Upgraded to 9.10 and got the above error. I tried the GParted advice above, but I'm still getting the error. I then tried a clean install from the CD, but the CD isn't seeing my existing operating systems (I have a RAID, with XP and Ubuntu). I'd be fine with just wiping out Ubuntu and starting over, but I don't want to wipe out XP (takes too long to reinstall and get everything "just right" with that! :P).

Any other ways to fix this problem? XP is still working fine.

---

### Post by boscopup on 2010-01-02
Nevermind. I fixed mine. My Grub menu.lst still had the 8.04 boot image listed. I just had to point it to the 9.10 boot image.

---

### Post by koglaa on 2010-01-02
I'm guessing that you didn't use the method that Herman mentioned.  As said in the first post I'm a noob.  How do you did you do this?

---

### Post by koglaa on 2010-01-04
Bump D:

---

### Post by koglaa on 2010-01-05
Bump

---

### Post by koglaa on 2010-01-06
Cmon, surely its not that hard to answer??

---

### Post by kansasnoob on 2010-01-06
> ... I can't boot from CD and I'm locked out of BIOS

Seriously no idea :(

---

### Post by presence1960 on 2010-01-06
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by darkod on 2010-01-06
> **koglaa said:**
> Cmon, surely its not that hard to answer??

Well, it's not easy to answer either. If I understood correctly, you can't boot ubuntu, and you also can't boot with the ubuntu cd.
You need a way to execute commands. If you can't do either of the above ways, there are limited options how to enter those commands.

---

### Post by koglaa on 2010-01-06
Oh God, I think I forgot to mention that I can boot from cd, but only by taking out my HDD then replacing it.  What I really wanted to know was how to the 8.04 boot image to 9.10 from grub menu.lst

---

### Post by darkod on 2010-01-06
> **koglaa said:**
> Oh God, I think I forgot to mention that I can boot from cd, but only by taking out my HDD then replacing it.  What I really wanted to know was how to the 8.04 boot image to 9.10 from grub menu.lst

Well, if you can only boot from the cd with the hdd disconnected, it doesn't help much. Yes, you can use terminal from the cd but with the hdd disconnected you can't work with the files on the hdd.
You need a way to boot from cd or usb stick with the hdd connected so you can work on it.

---

### Post by koglaa on 2010-01-06
Didn't you read "and then replacing it"?  Sorry if that sounded harsh.  I just can't seem to access my HDD through "Computer" or "GParted"

RESULTS.TXT
```
============================= Boot Info Summary: ==============================

=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________


=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo/BLKID: No such file or directory
```

---

### Post by presence1960 on 2010-01-06
Here is the totality of your results from the script. Definitely not looking promising!

```
============================= Boot Info Summary: ==============================

=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________
```



whatever happened your hard disk is corrupted, you have no valid partition table on there. You may be able to recover some data with testdisk by booting the Live CD and installing it by opening a terminal and running ```
sudo apt-get install testdisk
```

As far as recovering data I have never had to do that because I have working backups. If you have working backups I would just reinstall.

Just so you can see here is what my boot info script looks like:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub.
 => No known boot loader is installed in the MBR of /dev/sdb
 => Lilo is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   123,234,614   123,234,552   5 Extended
/dev/sda5                 126     8,385,929     8,385,804  82 Linux swap / Solaris
/dev/sda6           8,385,993    50,331,644    41,945,652  83 Linux
/dev/sda2         203,896,980   976,768,064   772,871,085  83 Linux
/dev/sda3         123,234,615   165,180,329    41,945,715  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b4c62

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02020202

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   104,856,254   104,856,192   7 HPFS/NTFS
/dev/sdc2         104,856,255   230,693,399   125,837,145   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda2: LABEL="backup" UUID="b37b51c7-cc17-4401-a66c-4d43193d508a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: LABEL="Sabayon_Fluxbox" UUID="190af1da-9dc4-4be2-9913-740db243e8c6" TYPE="ext4" 
/dev/sda5: UUID="63538de2-1cc9-4451-ab42-5f8712695c89" TYPE="swap" 
/dev/sda6: LABEL="karmic" UUID="e0b415e6-168b-49e7-b62b-0fc42c83a6d7" TYPE="ext4" 
/dev/sdb1: LABEL="data" UUID="8f5b8ecd-2930-46a1-8256-88235c860965" TYPE="ext3" 
/dev/sdc1: UUID="5B8A70BC5646AB94" LABEL="xp" TYPE="ntfs" 
/dev/sdc2: UUID="42D35EE6525751C9" LABEL="win_data" TYPE="ntfs" 
/dev/ramzswap0: TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/raz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raz)
/dev/sdb1 on /media/data type ext3 (rw,nosuid,nodev,uhelper=devkit)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-16-generic
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
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 190af1da-9dc4-4be2-9913-740db243e8c6
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=190af1da-9dc4-4be2-9913-740db243e8c6 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode) (on /dev/sda3)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 190af1da-9dc4-4be2-9913-740db243e8c6
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=190af1da-9dc4-4be2-9913-740db243e8c6 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Windows NT/2000/XP (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 5b8a70bc5646ab94
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/grub.cfg
   4.2GB: boot/initrd.img-2.6.31-16-generic
   4.2GB: boot/initrd.img-2.6.31-17-generic
   4.2GB: boot/vmlinuz-2.6.31-16-generic
   4.2GB: boot/vmlinuz-2.6.31-17-generic
   4.2GB: initrd.img
   4.2GB: initrd.img.old
   4.2GB: vmlinuz
   4.2GB: vmlinuz.old

========================== sda3/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,2)
#          kernel /boot/kernel-genkernel real_root=UUID=190af1da-9dc4-4be2-9913-740db243e8c6
#          initrd /boot/initramfs-genkernel
#boot=sda3
default=0
timeout=5
splashimage=(hd0,2)/boot/grub/splash.xpm.gz

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon)
	root (hd0,2)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=190af1da-9dc4-4be2-9913-740db243e8c6 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode)
	root (hd0,2)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=190af1da-9dc4-4be2-9913-740db243e8c6 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Other Operating System - Microsoft Windows
	rootnoverify (hd0,0)
	chainloader +1
	savedefault
title Other Operating System - Microsoft Windows
	rootnoverify (hd2,0)
	chainloader +1
	savedefault

=============================== sda3/etc/fstab: ===============================

UUID=190af1da-9dc4-4be2-9913-740db243e8c6 /                       ext4    user_xattr,noatime 1 1
/dev/shm                /dev/shm                tmpfs   defaults        0 0
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 swap                    swap    defaults        0 0

=================== sda3: Location of files loaded by Grub: ===================


  63.0GB: boot/grub/grub.conf
  63.0GB: boot/grub/menu.lst
  63.0GB: boot/grub/stage2

================================ sdc1/boot.ini: ================================

[Boot Loader]

timeout=15

Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[Operating Systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="USB Repair NOT to Start Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  0a 00 01 0f 00 65 5d 04  a0 32 00 00 00 00 03 03  |.....e]..2......|
00000010  00 62 61 00 00 00 00 00  00 00 04 32 00 61 61 01  |.ba........2.aa.|
00000020  0c 00 00 00 00 00 05 33  00 64 64 00 00 00 00 00  |.......3.dd.....|
00000030  00 00 07 0f 00 52 3c ee  0a 97 0a 00 00 00 09 32  |.....R<........2|
00000040  00 5f 5f 40 11 00 00 00  00 00 0a 13 00 64 64 00  |.__@.........dd.|
00000050  00 00 00 00 00 00 0c 32  00 62 62 34 0a 00 00 00  |.......2.bb4....|
00000060  00 00 bb 32 00 64 64 00  00 00 00 00 00 00 bd 3a  |...2.dd........:|
00000070  00 64 64 00 00 00 00 00  00 00 be 22 00 47 39 1d  |.dd........".G9.|
00000080  00 1d 1d 00 00 00 c2 22  00 1d 2b 1d 00 00 00 12  |......."..+.....|
00000090  00 00 c3 1a 00 76 39 35  d3 d2 0b 00 00 00 c5 12  |.....v95........|
000000a0  00 64 64 00 00 00 00 00  00 00 c6 10 00 64 64 00  |.dd..........dd.|
000000b0  00 00 00 00 00 00 c7 3e  00 c8 c8 00 00 00 00 00  |.......>........|
000000c0  00 00 c8 00 00 64 fd 00  00 00 00 00 00 00 ca 32  |.....d.........2|
000000d0  00 64 fd 00 00 00 00 00  00 00 00 00 00 00 00 00  |.d..............|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 82 00 ae 01 00 5b  |...............[|
00000170  03 00 01 00 01 40 02 00  00 00 00 00 00 00 00 00  |.....@..........|
00000180  00 00 00 00 00 00 03 02  03 03 03 03 03 03 03 00  |................|
00000190  00 00 00 00 00 00 00 01  d9 53 13 16 00 00 00 00  |.........S......|
000001a0  01 00 af 1a 29 85 e3 01  00 00 00 00 00 00 00 00  |....)...........|
000001b0  00 00 00 00 d9 53 13 16  62 4c 0b 00 00 00 80 01  |.....S..bL......|
000001c0  01 00 83 fe ff ff 3f 00  00 00 42 45 1c 1d 00 00  |......?...BE....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by koglaa on 2010-01-06
Maybe its not reading the harddrive after I put it in when the LiveCD has started up?

---

### Post by presence1960 on 2010-01-06
> **koglaa said:**
> Maybe its not reading the harddrive after I put it in when the LiveCD has started up?

For your sake I hope that is the case. Do you have a SATA optical drive? If so try switching the optical drive to a different SATA controller port and see what happens.

---

### Post by presence1960 on 2010-01-06
> **koglaa said:**
> ... I can't boot from CD and I'm locked out of BIOS

what do you mean by "locked out of BIOS"? Did you forget the password. You can reset it by referring to your motherboard BIOS documentation if that is the case.

---

### Post by koglaa on 2010-01-06
> **presence1960 said:**
> For your sake I hope that is the case. Do you have a SATA optical drive? If so try switching the optical drive to a different SATA controller port and see what happens.

I don't have a different SATA port.  But the HDD seems to be working fine on startup.  Is there anyway for me to access my ubuntu files through XP.  That would save me a lot of time

---

### Post by presence1960 on 2010-01-06
> **koglaa said:**
> I don't have a different SATA port.  But the HDD seems to be working fine on startup.  Is there anyway for me to access my ubuntu files through XP.  That would save me a lot of time

If you only have 2 sata ports then switch the HDD & optical drive on the SATA ports. You have to find a way to boot from CD with the hard disk plugged in and be able to access your HDD.

---

### Post by presence1960 on 2010-01-06
Based on what you have told us this seems to be a hardware problem and has nothing to do with Ubuntu. You are locked out of BIOS (which you still haven't explained exactly what that means) & your machine will not boot from CD with the hard disk plugged in.

If the password is the problem with BIOS refer to your motherboard documentation or look online at the manufacturer's site for the manual. It is only a matter  of changing a jumper setting to reset CMOS and then putting it back to the original setting.

---

### Post by koglaa on 2010-01-06
I've got an idea.  I'll tell you the results later (its 4:14am here)

---

### Post by presence1960 on 2010-01-06
> **koglaa said:**
> I've got an idea.  I'll tell you the results later (its 4:14am here)

Ok sleep on it and let us know tomorrow.

---

### Post by koglaa on 2010-01-06
I'm guess I'm stuck with a useless laptop... for now.  I'll take out the CMOS tomorrow and hope that makes a difference.  Thanks for your help... so far.

---

### Post by koglaa on 2010-01-07
Didn't have any success in removing the CMOS.  I guess I'll goto some repair shop

---

### Post by boscopup on 2010-01-23
Sorry I just realized you had PM'd me to come back to this thread, and I had never subscribed to the thread. My bad.

While I used the CD to boot and change things, it dawned on me later that you can just use the shell you get into when you boot. Just type your root password and it puts you in a maintenance shell. I think you should be able to edit your menu.lst from there. It's located in /boot/grub/menu.lst

Scroll down to where your Linux entries are, and replace the title (so you know which one you edited), kernel, and initrd with the appropriate kernel version (you can find the file names in /boot - look for the highest number kernel and use that).

---

### Post by llawwehttam on 2010-01-23
If you are willing to risk a bit then take the CMOS battery out of your laptop and connect the two contacts underneath it ( unless you have a reset jumper) and when you put the battery back in your BIOS should have reset and should be accessible.

DO NOT TRY THIS IF YOU HAVE NO EXPERIENCE WITH BIOS RESETS!!!!!

---

