---
title: "error: no such disk"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by herve3d on 2010-05-08
Hello, I want my parents discover the wonderful world of Ubuntu but it starts bad ...

On the same hard disk I just install Windows XP
Then I install Ubuntu with my official CD : UBUNTU 9.10 DESKTOP EDITION

When the UBUNTU install finish and my pc reboot I have :

GRUB loading.
error: no such partition

If I try ls :

grub rescue> ls
(hd0) (hd0,1) (fd0)
error: no such disk

Other info :

UBUNTU 9.10 so it's GRUB 2

I started with the LIVE CD to take more info :

With GParted :
/dev/sda1	ntfs
/dev/sda2	extended
	/dev/sda5	ext4	
	/dev/sda6	linux-swap

I have a boot CD with GRUB 1.97.2, I can boot on Windows with :
set root=hd0,1
chainloader +1
boot

Why my GRUB doesn't work ? Thanks for you help.

---

### Post by frantid on 2010-05-08
Hi, please run the bootinfoscript:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

post results here by pasting the text in between code tags -- i.e. click on the # sign in the reply box and paste in between the brakets ] [

---

### Post by herve3d on 2010-05-08
I boot with my live CD and I run the script, result :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x25642563

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    20,964,824    20,964,762   7 HPFS/NTFS
/dev/sda2          20,964,825   781,417,664   760,452,840   5 Extended
/dev/sda5          20,964,888   779,200,694   758,235,807  83 Linux
/dev/sda6         779,200,758   781,417,664     2,216,907  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1027 MB, 1027604480 bytes
255 heads, 63 sectors/track, 124 cylinders, total 2007040 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     2,007,039     2,006,977   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        A234F97234F949B5                       ntfs                                     
/dev/sda5        d2fd7ecc-64ed-4016-b868-975ceb5820f3   ext4                                     
/dev/sda6        ebf19cdb-0c72-4cc2-869e-1d5f4b277a4c   swap                                     
/dev/sdc1        B49F-7C3B                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdc1        /media/B49F-7C3B         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

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
search --no-floppy --fs-uuid --set d2fd7ecc-64ed-4016-b868-975ceb5820f3
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
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set d2fd7ecc-64ed-4016-b868-975ceb5820f3
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d2fd7ecc-64ed-4016-b868-975ceb5820f3 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set d2fd7ecc-64ed-4016-b868-975ceb5820f3
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=d2fd7ecc-64ed-4016-b868-975ceb5820f3 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a234f97234f949b5
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
UUID=d2fd7ecc-64ed-4016-b868-975ceb5820f3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ebf19cdb-0c72-4cc2-869e-1d5f4b277a4c none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  17.6GB: boot/grub/core.img
  17.6GB: boot/grub/grub.cfg
  11.2GB: boot/initrd.img-2.6.31-14-generic
  11.2GB: boot/vmlinuz-2.6.31-14-generic
  11.2GB: initrd.img
  11.2GB: vmlinuz

```

---

### Post by frantid on 2010-05-08
let's try -- to check the disk

```
fsck -y /dev/sda5
```

see if you get errors.

Then we'll need to mount the drive

```
sudo mount /dev/sda5 /mnt
```

then recopy grub from the cd.
```

sudo grub-install --root-directory=/mnt/ /dev/sda
```


we are working through the repair steps here, for more info:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by herve3d on 2010-05-22
I am back to my parent home to try again...

```
$ sudo fsck -y /dev/sda5
fsck de util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda5*: propre, 128732/23699456 fichiers, 2027402/94779475 blocs
```

```
$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)	/dev/sda
```

Same Grub message = error: no such partition

A big problem with grub, it never find my linux partition !
I don't think that I have to re-install Grub, I think I have to make any configuration to help him to find my disk...

I don't know wath to do, maybe to find an alternative to Grub...

---

### Post by darkod on 2010-05-22
I think you are hit with this problem:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Your UUID in grub.cfg seems correct, so just start from step 4 in the solution.

PS. Forgot to mention. Look at step 1 for how to boot into ubuntu, then jump over steps 2 and 3.

---

### Post by herve3d on 2010-06-19
I'm back again.
I tried this solution, I commented the 3 lines but same problem :-/

I remember that during Ubuntu install I saw my hard disk as a SCSI2 disk, but it's a IDE disk, maybe a problem come from that...

---

### Post by darkod on 2010-06-19
No, reporting as SCSI shouldn't matter. Linux stopped making difference between sata and ide disks so I guess they use SCSI always.

But your ubuntu partitions don't seem to be recognized, both sda5 and sda6.

In the rescue prompt, if you type ls again, does it list (hd0,5) and (hd0,6)?

---

### Post by kansasnoob on 2010-06-19
Please read this all before beginning!

I'm just curious, clear back at the beginning you said,

> I have a boot CD with GRUB 1.97.2, I can boot on Windows with :
set root=hd0,1
chainloader +1
boot

But obviously NOT with the auto-generated entry:

> menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set a234f97234f949b5
	drivemap -s (hd0) ${root}
	chainloader +1
}

Is that correct?

If so I think darkod is on the right track so I'd try creating some custom entries in "/etc/grub.d/40_custom" using nano in a chroot like shown below (please copy-n-paste commands since some are quite long).

But, before beginning, please read a bit here about my chroot procedure:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

And here about Nano if you've never used it:

[https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

And when you're ready do the following from Terminal using the Live CD:

```
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
nano /etc/grub.d/40_custom
```

Do NOT edit any text there just copy-n-paste the following below the existing text:

```
menuentry "Custom Win XP one" {
	insmod ntfs
	set root=(hd0,1)
	drivemap -s (hd0) ${root}
	chainloader +1
}

menuentry "Custom Win XP two" {
	set root=(hd0,1)
	drivemap -s (hd0) ${root}
	chainloader +1
}

menuentry "Custom Win XP three" {
	set root=(hd0,1)
	chainloader +1
}

menuentry "Ubuntu one" {
        set root=(hd0,5)
	linux	/vmlinuz root=UUID=d2fd7ecc-64ed-4016-b868-975ceb5820f3 ro quiet splash
	initrd	/initrd.img
}

menuentry "Ubuntu two" {
        set root=(hd0,5)
	search --no-floppy --fs-uuid --set d2fd7ecc-64ed-4016-b868-975ceb5820f3
	linux	/vmlinuz root=UUID=d2fd7ecc-64ed-4016-b868-975ceb5820f3 ro quiet splash
	initrd	/initrd.img
}

```

The one, two, three is just so we know the difference, and so I'll know what (if anything) works and what doesn't. As I said I'm curious.

Anyway after editing and saving the changes you can check to see if the changes were saved properly by running:

```
cat /etc/grub.d/40_custom
```

Then to apply those changes to grub.cfg run:

```
update-grub
```

And just to play it safe lets reinstall grub to the mbr:

```
grub-install /dev/sda
```

Then we can exit the chroot and unmount:

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt
```

Those new entries should now show up at the bottom of the boot menu so let us know what works and what doesn't. It may take several hours for me to reply, but based on that we should know what to do next.

---

### Post by herve3d on 2010-06-20
Sorry first I retried to update grub but I have an error. I think it's basic but I don't know what to do... :oops:

sudo update-grub2
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

I tried before
sudo mount /dev/sda5 /mnt
or
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

---

### Post by darkod on 2010-06-20
You can't run update-grub just like that from live mode.

Did you try to execute the commands from kansasnoob one by one as stated?

---

### Post by herve3d on 2010-06-20
Before I just updated grub-mkconfig_lib and tried listed mount commands, I didn't seen other commands to do...

But I have to finish today, so I made it durty, I installed Ubuntu on the same partition of windows, ntfs :-\
but same problem :'-( A better point is that booting on windows works now.

Now I have to go back to my home, I will try to make Ubuntu working the next time I'll come, if you have ideas...

Thanks for your support.

---

