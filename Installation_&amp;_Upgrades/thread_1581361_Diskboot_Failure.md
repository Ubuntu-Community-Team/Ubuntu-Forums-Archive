---
title: "Diskboot Failure"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by lilsavalex on 2010-09-24
I installed Ubuntu 9.10, the installation processes went great! I rebooted my system as i was told and i get this following message,```
[COLOR=Red]DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER.[/COLOR]
```Not sure what to do since i have no other system on this hardrive and i have no other hardrive connected to my system. What do you think the solution could be?

---

### Post by lilsavalex on 2010-09-25
Anyone have any idea? Any help will be greatly appreciated .

---

### Post by drs305 on 2010-09-25
Do you have a non-system disk inserted and does your BIOS have the system boot the CD or external drive first?

You might try checking the BIOS and change it to boot from the system hard drive first.

---

### Post by sikander3786 on 2010-09-25
It is a Bios boot failure message I believe. Check in your Bios if it is even set properly to boot from the single HDD present. If it is then I think you have chosen not to install GRUB during the installation process by mistake. You'll need to install GRUB in that case but first of all check the Bios.

---

### Post by lilsavalex on 2010-09-25
I tried what I've been told by all of you and still nothing .

---

### Post by drs305 on 2010-09-25
If you can boot the LiveCD (Ubuntu installation disk) to the Desktop, please download and run *meierfra's* boot info script and post the contents of the RESULTS.txt. It provides information which might help us see what is wrong.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

Make sure the BIOS boots first to the CD drive.

---

### Post by lilsavalex on 2010-09-25
Thanks for helping me, its greatly appreciated . =)
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdf

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

sdf4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00058548

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   187,333,964   187,333,902  83 Linux
/dev/sda2         187,333,965   195,366,464     8,032,500   5 Extended
/dev/sda5         187,334,028   195,366,464     8,032,437  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 4022 MB, 4022337024 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7856127 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcad4ebea

Partition  Boot         Start           End          Size  Id System

/dev/sdf4    *             63     7,856,126     7,856,064   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        534e9809-f2fa-4af9-a7ad-4c4c97035fac   ext4                                     
/dev/sda5        8aa003df-acc4-4713-b961-89acaa220e49   swap                                     
/dev/sdf4        B4FE-5315                              vfat       CD_ROM                        

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdf4        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sr0         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=devkit,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


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
search --no-floppy --fs-uuid --set 534e9809-f2fa-4af9-a7ad-4c4c97035fac
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
    search --no-floppy --fs-uuid --set 534e9809-f2fa-4af9-a7ad-4c4c97035fac
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=534e9809-f2fa-4af9-a7ad-4c4c97035fac ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 534e9809-f2fa-4af9-a7ad-4c4c97035fac
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=534e9809-f2fa-4af9-a7ad-4c4c97035fac ro single 
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
UUID=534e9809-f2fa-4af9-a7ad-4c4c97035fac /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8aa003df-acc4-4713-b961-89acaa220e49 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   3.1GB: boot/grub/core.img
   3.1GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: initrd.img
    .5GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by drs305 on 2010-09-25
I don't see anything wrong with the contents of RESULTS.txt. It appears the normal boot files are correctly in place.

To be honest, I haven't seen the error messages you are getting as a result of a Grub2 error. But if you are sure the BIOS is pointing to the correct drive then you might try reinstalling Grub2 so it rewrites the MBR information.

Boot the LiveCD and run the following commands:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Note the first command includes the drive and partition (sda1), while the second only includes the drive (sda).

After running the commands, remove the CD and reboot and see if anything has changed.

---

### Post by lilsavalex on 2010-09-25
Thanks, But i get the following . 
```
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
error: cannot open `/dev/sdb' while attempting to get disk size
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

```

---

### Post by drs305 on 2010-09-25
I don't know why it is referencing sdb. From the Desktop, remount /dev/sda1 (if it's not still mounted) and inspect the contents of /boot/grub/device.map  You may or may not have this file. If you do (the file you open is not empty): 

```
sudo mount /dev/sda1 /mnt
gksudo gedit /mnt/boot/grub/device.map
```

It may look something like this:
> 
(fd0)	/dev/fd0
(hd0)	/dev/disk/by-id/ata-ST3320620AS_9QF3KKYY
(hd1)	/dev/disk/by-id/ata-WDC_WD6400AAKS-22A7B2_WD-WMASY7162178

or this;
> 
(fd0) /dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb


If there is a reference to sdb or (hd1), delete the line and save the file. I'm not optimistic, but try running the grub-install command again and see if the error repeats.

---

### Post by lilsavalex on 2010-09-25
So i delete the 2nd line? 
```
(hd0)    /dev/sda
(hd1)    /dev/sdb
```

---

### Post by drs305 on 2010-09-25
> **lilsavalex said:**
> So i delete the 2nd line? 
```
(hd0)    /dev/sda
(hd1)    /dev/sdb
```

Yes. The boot info script didn't see a sdb drive (although it did find an odd sdf), and you have also said you have only one. This file information won't delete anything on your system, even should you have an sdb.

**Added:** If you get the same message, you can also try running "sudo grub-install --recheck --root-directory=/mnt /dev/sda"

---

### Post by lilsavalex on 2010-09-25
I just ran the Install-Grub command and no errors appeared after i deleted the second line. Ill check back in a bit if it worked.

---

### Post by lilsavalex on 2010-09-25
Nothing . The same thing still happens . :/

---

### Post by drs305 on 2010-09-25
I didn't expect success but I was hoping....  :-(

The "sdf" reference - do you have a thumb drive or SD card attached to your machine? If so, have you tried booting without it inserted?

---

### Post by lilsavalex on 2010-09-25
Haha it was worth a try though :) . Thanks for trying to help . I really appreciate it :)

---

### Post by drs305 on 2010-09-26
I'll use this to bump your thread.

If you do a search for "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER." you will find many entries on Google.

Some things which can trigger the messages include a BIOS problem (trying to read a non-system disk at boot, not recognizing the computer's hard drive), a bad hard drive, and bad files.

I don't think it's a drive problem, as we were able to rewrite the MBR and install the grub files - the drive can be read and written to via the LiveCD. 

Take a look at some of the search results. I'd concentrate on BIOS issues first. 

Good luck and please let us know how you get on.

---

