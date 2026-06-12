---
title: "Re-Install of 9.10 Results In Failure to Boot Grub"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by brianafischer on 2009-11-29
I have been working on re-installing Ubuntu 9.10 for the last 4 hours.  I have made my way through multiple issues, and finally made it through the install process.  Now upon reboot, grub fails to boot into Ubuntu.

**_Issue #1_**
GRUB does not load linux, upon startup of the computer I get the following error message:
```
GRUB loading.
error: no such partition
grub rescue>
```

**_Issue #2_**
Cannot seem to repair grub from a live CD.
```
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sdc5 /mnt
ubuntu@ubuntu:~$ cd /mnt
ubuntu@ubuntu:/mnt$ ls
bin    dev   initrd.img  media  proc  selinux  tmp  vmlinuz
boot   etc   lib         mnt    root  srv      usr
cdrom  home  lost+found  opt    sbin  sys      var
ubuntu@ubuntu:/mnt$ sudo chroot /mnt
ls
root@ubuntu:/# ls
bin    dev   initrd.img  media	proc  selinux  tmp  vmlinuz
boot   etc   lib	 mnt	root  srv      usr
cdrom  home  lost+found  opt	sbin  sys      var
root@ubuntu:/# sudo nano /etc/default/grub
sudo: unable to resolve host ubuntu
root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
grub-probe: error: cannot find a device for /.

root@ubuntu:/# update-grub
grub-probe: error: cannot find a device for /.

root@ubuntu:/# grub-install --recheck /dev/sdc
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
root@ubuntu:/# grub-install --recheck /dev/sdc5
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
root@ubuntu:/# grub-probe
No path or device is specified.
Try ``grub-probe --help'' for more information.
root@ubuntu:/# grub-probe /dev/sdc
grub-probe: error: Cannot stat `/dev/sdc'
root@ubuntu:/# grub-probe /dev/sdc5
grub-probe: error: Cannot stat `/dev/sdc5'
root@ubuntu:/# sudo chroot /mnt
sudo: unable to resolve host ubuntu
chroot: cannot run command `/bin/bash': No such file or directory
root@ubuntu:/# ls
bin    dev   initrd.img  media	proc  selinux  tmp  vmlinuz
boot   etc   lib	 mnt	root  srv      usr
cdrom  home  lost+found  opt	sbin  sys      var
root@ubuntu:/# dpkg-reconfigure grub-pc
sed: warning: failed to get security context of /tmp/grub.RtyerWhWdF: No data availablesed: warning: failed to get security context of /tmp/grub.RtyerWhWdF: No data availablesed: warning: failed to get security context of /tmp/grub.RtyerWhWdF: No data availablesed: warning: failed to get security context of /tmp/grub.RtyerWhWdF: No data availableReplacing config file /etc/default/grub with new version
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
grub-probe: error: cannot find a device for /.

root@ubuntu:/# sudo update-grub
sudo: unable to resolve host ubuntu
grub-probe: error: cannot find a device for /.

root@ubuntu:/#

ubuntu@ubuntu:/mnt$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e8400

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001   83  Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009265a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001   83  Linux

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b612a8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sdc2            7650       15298    61440000    7  HPFS/NTFS
/dev/sdc3           15299       23196    63440685    5  Extended
/dev/sdc5           15299       22947    61440561   83  Linux
/dev/sdc6           22948       23196     2000061   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed4d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   83  Linux

```

Please help!  My previous install was on /dev/sdc4 which I assume is where grub is currently looking.  When I re-installed Ubuntu, I deleted and created a new partition which is why I assume /dev/sdc5 was created.

[LIST]
[*]Is there a way to change /dev/sdc5 to /dev/sdc4?
[*]How can I fix grub?
[/LIST]

---

### Post by presence1960 on 2009-11-30
> **brianafischer said:**
> 

Please help!  My previous install was on /dev/sdc4 which **[COLOR="Red"]_I assume_[/COLOR]** is where grub is currently looking.  When I re-installed Ubuntu, I deleted and created a new partition which is why I assume /dev/sdc5 was created.

[LIST]
[*]Is there a way to change /dev/sdc5 to /dev/sdc4?
[*]How can I fix grub?
[/LIST]

Let's not assume, let's see exactly what your setup is.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by keforex on 2009-11-30
Hi, I am not the original poster but I have a similar problem and here's the info on my system, maybe you can help me. The symptom is that it's stuck on "Grub Loading" and seems to be looping with disk access every 5 seconds - this at the 1st reboot after a fresh x64 install.

Any help is GREATLY appreciated!

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=d2fc9881-05b3-40b6-be38-3606ecf3a6d5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Grub0.97 is installed in the MBR of /dev/sdc and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2010.0 
                       (Official) for i586 Kernel 2.6.31.5-desktop586-1mnb on 
                       a 4-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

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

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003ad66

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    25,189,919    25,189,857  83 Linux
/dev/sda2          25,189,920   488,392,064   463,202,145   5 Extended
/dev/sda5          25,189,983    33,367,004     8,177,022  82 Linux swap / Solaris
/dev/sda6          33,367,068   488,392,064   455,024,997  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xffb9de1d

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,465,145,343 1,465,143,296   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3104e5f8

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   139,203,224   139,203,162  83 Linux
/dev/sdc2         139,203,225   145,211,534     6,008,310   5 Extended
/dev/sdc5         139,203,288   145,211,534     6,008,247  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 4092 MB, 4092854272 bytes
255 heads, 63 sectors/track, 497 cylinders, total 7993856 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008f031

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63     7,984,304     7,984,242   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="cb887b8f-c3cd-4cbb-afdd-3f64f3f03241" TYPE="ext4" 
/dev/sda5: UUID="0c332247-1eb1-4b52-88fb-59fddb055c32" TYPE="swap" 
/dev/sda6: UUID="82dbaea8-7c31-401b-90f9-c39b4668fb99" TYPE="ext4" 
/dev/sdb1: UUID="703CF0D53CF09776" LABEL="MAINDISK" TYPE="ntfs" 
/dev/sdc1: UUID="d2fc9881-05b3-40b6-be38-3606ecf3a6d5" TYPE="ext4" 
/dev/sdc5: UUID="f4d7de56-70d2-4a97-9516-6d75c97695bb" TYPE="swap" 
/dev/sdd1: LABEL="READYBOOST" UUID="60B5-F643" TYPE="vfat" 

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
/dev/sdd1 on /media/READYBOOST type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda6 on /media/82dbaea8-7c31-401b-90f9-c39b4668fb99 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sda1 on /media/cb887b8f-c3cd-4cbb-afdd-3f64f3f03241 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdc1 on /media/d2fc9881-05b3-40b6-be38-3606ecf3a6d5 type ext4 (rw,nosuid,nodev,uhelper=devkit)


=========================== sda1/boot/grub/menu.lst: ===========================

timeout 5
color black/cyan yellow/cyan
gfxmenu (hd0,0)/boot/gfxmenu
default 0

title Vista
root (hd1,0)
map (0x82) (0x80)
map (0x80) (0x82)
makeactive
chainloader +1

title Mandriva 2010
kernel (hd0,0)/boot/vmlinuz BOOT_IMAGE=Mandriva_2010 root=UUID=cb887b8f-c3cd-4cbb-afdd-3f64f3f03241  resume=UUID=0c332247-1eb1-4b52-88fb-59fddb055c32 splash=silent vga=788
initrd (hd0,0)/boot/initrd.img

title Ubuntu 9.10 
root (hd2,0)
uuid		899675aa-405e-4f99-b01c-5f1465baf389
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=899675aa-405e-4f99-b01c-5f1465baf389 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Xubuntu 9.04 (1Tb External Disk)
root		(hd3,0)
uuid		570038e2-8fb7-4f18-993b-006c2b6ef14b
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=570038e2-8fb7-4f18-993b-006c2b6ef14b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

=============================== sda1/etc/fstab: ===============================

# Entry for /dev/sda1 :
UUID=cb887b8f-c3cd-4cbb-afdd-3f64f3f03241 / ext4 defaults 1 1
# Entry for /dev/sda6 :
UUID=82dbaea8-7c31-401b-90f9-c39b4668fb99 /home ext4 defaults 1 2
none /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=0c332247-1eb1-4b52-88fb-59fddb055c32 swap swap defaults 0 0
# Entry for /dev/sdc5 :
UUID=7ed4f3cc-a129-4982-a251-4b3bfadae7c5 swap swap defaults 0 0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd-2.6.31.5-desktop586-1mnb.img
    .0GB: boot/initrd-desktop586.img
    .0GB: boot/initrd.img
    .0GB: boot/vmlinuz
    .0GB: boot/vmlinuz-2.6.31.5-desktop586-1mnb
    .0GB: boot/vmlinuz-desktop586

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
search --no-floppy --fs-uuid --set d2fc9881-05b3-40b6-be38-3606ecf3a6d5
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
	search --no-floppy --fs-uuid --set d2fc9881-05b3-40b6-be38-3606ecf3a6d5
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d2fc9881-05b3-40b6-be38-3606ecf3a6d5 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set d2fc9881-05b3-40b6-be38-3606ecf3a6d5
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d2fc9881-05b3-40b6-be38-3606ecf3a6d5 ro single 
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
menuentry "Mandriva 2010 (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set cb887b8f-c3cd-4cbb-afdd-3f64f3f03241
	linux /boot/vmlinuz BOOT_IMAGE=Mandriva_2010 root=UUID=cb887b8f-c3cd-4cbb-afdd-3f64f3f03241 resume=UUID=0c332247-1eb1-4b52-88fb-59fddb055c32 splash=silent vga=788
	initrd (hd0,0)/boot/initrd.img
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 703cf0d53cf09776
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
UUID=d2fc9881-05b3-40b6-be38-3606ecf3a6d5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=f4d7de56-70d2-4a97-9516-6d75c97695bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sde 
```

---

### Post by brianafischer on 2009-11-30
> **presence1960 said:**
> Let's not assume, let's see exactly what your setup is

Here you go, thanks for the help!

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=02e84806-e654-47c8-a206-14fba5bf6a1c)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub1.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #3 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e8400

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,953,520,064 1,953,520,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009265a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 2,930,272,064 2,930,272,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6b612a8f

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   122,881,184   122,881,122   7 HPFS/NTFS
/dev/sdc2         122,882,048   245,762,047   122,880,000   7 HPFS/NTFS
/dev/sdc3         245,762,370   372,643,739   126,881,370   5 Extended
/dev/sdc5         245,762,433   368,643,554   122,881,122  83 Linux
/dev/sdc6         368,643,618   372,643,739     4,000,122  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ed4d7

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   976,768,064   976,768,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="890937d2-6a67-4712-9e63-af9911dbc085" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="e8dc4654-b2be-472b-8d91-0c6be08e3285" TYPE="ext4" 
/dev/sdc1: UUID="50A08D8EA08D7AEC" TYPE="ntfs" 
/dev/sdc2: UUID="DAC8F50BC8F4E723" TYPE="ntfs" 
/dev/sdc5: UUID="02e84806-e654-47c8-a206-14fba5bf6a1c" TYPE="ext4" 
/dev/sdc6: UUID="0ca6b204-fedc-4c10-9eda-53759cffbfc1" TYPE="swap" 
/dev/sdd1: LABEL="/music" UUID="c710aa70-3dcd-495c-bc41-2c6e47edfe01" SEC_TYPE="ext2" TYPE="ext3" 
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
/dev/sdc5 on /mnt type ext4 (rw)


================================ sdc1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root=(hd2,5)
search --no-floppy --fs-uuid --set 02e84806-e654-47c8-a206-14fba5bf6a1c
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
	set root=(hd2,5)
	search --no-floppy --fs-uuid --set 02e84806-e654-47c8-a206-14fba5bf6a1c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=02e84806-e654-47c8-a206-14fba5bf6a1c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,5)
	search --no-floppy --fs-uuid --set 02e84806-e654-47c8-a206-14fba5bf6a1c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=02e84806-e654-47c8-a206-14fba5bf6a1c ro single 
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
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 50a08d8ea08d7aec
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc5 during installation
UUID=02e84806-e654-47c8-a206-14fba5bf6a1c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=0ca6b204-fedc-4c10-9eda-53759cffbfc1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 125.8GB: boot/grub/grub.cfg
 125.8GB: boot/initrd.img-2.6.31-14-generic
 125.8GB: boot/vmlinuz-2.6.31-14-generic
 125.8GB: initrd.img
 125.8GB: vmlinuz

```

---

### Post by darkod on 2009-11-30
@brianafischer
As you can notice from the top of the result of that script, you have grub2 both on sda and sdc. Always when installing with multiple drives make sure you know where are you installing grub.
The grub2 installed on sda might work (it's looking at /dev/sdc5 as it's supposed to) but you might be booting the other one.
The grub2 on sdc definitely will not work because it's looking at /dev/sdc3 not sdc5.

What you should do:
1. Decide which drive you want to use as boot and set it as first option in BIOS. Lets asume that's sdc.
2. Start with the LiveCD and instead of the commands you tried in your first post, open terminal and do:

```
sudo mount /dev/sdc5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
```

See if that will work. If you decide to install grub2 elsewhere, change the /dev/sdc from the second command into /dev/sda or whatever.

---

### Post by darkod on 2009-11-30
@keforex
You have similar situation, even more complicated.
Grub2 on sda, grub1 on sdc and syslinux on sdd. Why so many bootloaders?
The previous advice is applicable to you also. You should use the commands:

```
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
```

And make sure sdc it the first drive in boot order.

---

### Post by presence1960 on 2009-11-30
+1 darkod! BTW syslinux bootloader is from a bootable USB/flash drive which was plugged in when the script was run.

---

### Post by brianafischer on 2009-11-30
> **darkod said:**
> What you should do:
1. Decide which drive you want to use as boot and set it as first option in BIOS. Lets asume that's sdc.
2. Start with the LiveCD and instead of the commands you tried in your first post, open terminal and do:

```
sudo mount /dev/sdc5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
```

See if that will work. If you decide to install grub2 elsewhere, change the /dev/sdc from the second command into /dev/sda or whatever.

That didn't seem to work.

```
ubuntu@ubuntu:/mnt$ sudo grub-install --root-directory=/mnt/ /dev/sdc
grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

It appears the device map is empty:
```
ubuntu@ubuntu:/mnt$ sudo ls -l /mnt/boot/grub/device.map 
-rw-r--r-- 1 root root 0 2009-11-30 02:19 /mnt/boot/grub/device.map
```

Any additional help is appreciated!  Also, how can I remove grub from a drive?

TIA

---

### Post by darkod on 2009-11-30
For the second command try this modification:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdc

---

### Post by brianafischer on 2009-11-30
That worked great, thanks for the help!

```
ubuntu@ubuntu:/mnt$ sudo grub-install --recheck --root-directory=/mnt/ /dev/sdc
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
```

---

### Post by keforex on 2009-11-30
> **darkod said:**
> @keforex
You have similar situation, even more complicated.
Grub2 on sda, grub1 on sdc and syslinux on sdd. Why so many bootloaders?
The previous advice is applicable to you also. You should use the commands:

```
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
```

And make sure sdc it the first drive in boot order.



Excellent! This did work perfectly - thanks a bunch, I really appreciate the help.

The only thing I've lost was the nice looking mandriva grub menu I had before. Any hints on restoring and/or creating a grub menu that is a little more pleasant to look at? --Thanks!!

---

### Post by darkod on 2009-12-01
Glad you got it working, both of you. For changing layout of the grub2 menu, try googling for "grub2 tweaks", or similar, but not sure how many tutorials are out there yet. Also try searching for "grub2 colors", if that's what you mean by more pleasant, changing the colors used.
Grub2 is fairly new so it might take some time for people to create nice tweaks for it.
The main thing is that it's working fine, and is able to add all OSs that finds on your computer.

---

