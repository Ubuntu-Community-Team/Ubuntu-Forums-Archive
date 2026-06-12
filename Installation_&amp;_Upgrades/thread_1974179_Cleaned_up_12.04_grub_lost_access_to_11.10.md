---
title: "Cleaned up 12.04 grub lost access to 11.10"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by Oldhacker on 2012-05-05
After listing the 18 entries in my Ubuntu 12.04 boot menu, I began deleting 2 at a time with gparted. Then, I did a sudo update-grub each time and restarted to check the results. Everything was fine until the last re-boot when I tried to get back into Ubuntu 11.10

The entries for Ubuntu 11.10 still showed up in the update-grub and also in the boot menu. But, instead of going into Ubuntu 11.10, I got this message: "The disk drive for /media/sdb2 is not ready yet or not present."

What I suspect is that one of the deletions that I did (of old installations) could have contained the mount point for /sdb2 which is where my Ubuntu 11.10 resides. 

How can I go about getting it back?

---

### Post by mips on 2012-05-05
post the output of:
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
```

Sounds like you deleted the wrong partition. Did you not write down what you were suppose to keep before deleting the others?

---

### Post by darkod on 2012-05-05
Or you simply had an auto mount of sdb2 present, and after you deleted that partition it reports it can't find it. If you didn't need it anyway, no problem.
Delete the mount configuration and that's it. Assuming you don't need that partition any more.

---

### Post by Oldhacker on 2012-05-05
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00097b98

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2       613095422   625141759     6023169    5  Extended
/dev/sda5       613095424   625141759     6023168   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005237f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   295965165   147982551+  83  Linux
/dev/sdc2       295966718  1953523711   828778497    5  Extended
/dev/sdc5      1009207296  1484585807   237689256   83  Linux
/dev/sdc6      1941479424  1953523711     6022144   82  Linux swap / Solaris
/dev/sdc7       530333696  1005017087   237341696   83  Linux
/dev/sdc8      1005019136  1009203199     2092032   82  Linux swap / Solaris
/dev/sdc9      1484587008  1941471231   228442112   83  Linux
/dev/sdc10      295966720   530331647   117182464   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002e221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   353703104   176851521   83  Linux
/dev/sdb3       608783299   625137344     8177023    5  Extended
/dev/sdb5       614020428   625137344     5558458+  82  Linux swap / Solaris

/dev/sda5: UUID="2bd74177-cbc1-4960-a3fb-62e762da1541" TYPE="swap" 
/dev/sdc1: LABEL="samsung" UUID="b8292d17-77d5-488a-92ad-1cbb7838c9a6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="228db4d1-6d0e-478f-bae7-53dc3913028e" TYPE="ext4" 
/dev/sdc6: UUID="af1b2958-1cc7-4aea-9080-999703b43074" TYPE="swap" 
/dev/sdc7: UUID="7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089" TYPE="ext4" 
/dev/sdc8: UUID="eff9e9dc-69e0-40d0-a84e-9ac1cdc1fb66" TYPE="swap" 
/dev/sdc9: UUID="4ed99c58-19a1-462b-b781-9e64248a9ec3" TYPE="ext4" 
/dev/sdc10: UUID="e05bcd5b-36ce-4eed-a282-3b1dd77054a5" TYPE="ext4" 
/dev/sdb1: LABEL="BACKDATA" UUID="9024a14b-59ec-421e-adbd-827b94a61a69" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="e84ef3fa-40bd-45b5-85ce-e06d445aff21" TYPE="swap" 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc10 during installation
UUID=e05bcd5b-36ce-4eed-a282-3b1dd77054a5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=af1b2958-1cc7-4aea-9080-999703b43074 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I had all 18 disks and what they contained listed on a paper and thought thatall I had to do was delete any partition that had something that I no longer wanted to keep. Obviously, I was wrong

---

### Post by darkod on 2012-05-05
Do you know which partition is your 11.10?

If yes, from live mode simply mount that partition at /mnt and check its fstab with:
cat /mnt/etc/fstab

The fstab you posted might be from 12.04 I guess. You need to look into the fstab of 11.10 if you have a mount for sdb2 set up, because you are getting that error when trying to boot 11.10.

---

### Post by Oldhacker on 2012-05-06
Almost there, but did something else wrong.
I edited the mount point of my sdc7 (Ubuntu 11.10) and attempted to get there from the GRUB boot menu.
This produced the message: "The disk drive for /media/sdb2 is not ready yet or not present. Continue to wait, or press S to skip mounting or M for manual recovery."

I then pressed S and after a while Ubuntu 11.10 was there. Figuring that the boot menu in 11.10 did not coincide with the boot menu from 12.04, I did the same edit there to tell it to use sdc7 instead of sdb2. That was another mistake. Again trying to enter Ubuntu 11.10 only brought up a black console screen with a blinking cursor.

Now, I am back in 12.04 and scratching my head again.

---

### Post by darkod on 2012-05-06
Why don't you just mount the 11.10 partition from live mode and post the fstab as suggested in my last post. Maybe we will notice something.

I say again, it all points to having sdb2 set to mount, now it's missing with Skip you can continue booting 11.10.

And be careful touching the fstab, don't try to many things with it. I don't recommend throwing in sdc7 just like that unless you definitely know what you are doing.

And you can't simply change a mount point, it needs to exist as a folder at least.

---

### Post by Oldhacker on 2012-05-06
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sdc7 during installation
UUID=7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089  /               ext4  users,user                0  1  
# swap was on /dev/sdc8 during installation
UUID=eff9e9dc-69e0-40d0-a84e-9ac1cdc1fb66  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb2                                  /media/sdb2     ext3  defaults                  0  0

---

### Post by darkod on 2012-05-06
Put a # sign in front of the line starting with /dev/sdb2. Save the file.

Restart and try to boot 11.10.

---

### Post by Oldhacker on 2012-05-06
It was a good try, but no cigar yet.
I commented out the line with sdb2 using the #, but when I attempted to boot into Ubuntu 11.0 all I got was a blinking cursor. :-(

---

### Post by darkod on 2012-05-06
Did you do any other changes regarding 11.10? Can it be the grub2 is pointing to the wrong place?

If you can, it's best to run the boot info script from the link in my signature. Post the results as explained there. It will show many details and it will be much faster then guessing like this.

You can run it from your 12.04 which still boots, or from live mode.

One thing is for sure, the /dev/sdb2 needs to be commented out or deleted from fstab because you deleted that partition and it no longer exists. So it can never be mounted by fstab.

---

### Post by Oldhacker on 2012-05-06
At this point, I can't say for certain what, if any other changes have been made. But here is the new output of bootinfoscript:

                 ```
 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos10)/boot/grub on this drive.

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdc9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sdc10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2         613,095,422   625,141,759    12,046,338   5 Extended
/dev/sda5         613,095,424   625,141,759    12,046,336  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   353,703,104   353,703,042  83 Linux
/dev/sdb3         608,783,299   625,137,344    16,354,046   5 Extended
/dev/sdb5         614,020,428   625,137,344    11,116,917  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63   295,965,165   295,965,103  83 Linux
/dev/sdc2         295,966,718 1,953,523,711 1,657,556,994   5 Extended
/dev/sdc5       1,009,207,296 1,484,585,807   475,378,512  83 Linux
/dev/sdc6       1,941,479,424 1,953,523,711    12,044,288  82 Linux swap / Solaris
/dev/sdc7         530,333,696 1,005,017,087   474,683,392  83 Linux
/dev/sdc8       1,005,019,136 1,009,203,199     4,184,064  82 Linux swap / Solaris
/dev/sdc9       1,484,587,008 1,941,471,231   456,884,224  83 Linux
/dev/sdc10        295,966,720   530,331,647   234,364,928  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda5        2bd74177-cbc1-4960-a3fb-62e762da1541   swap       
/dev/sdb1        9024a14b-59ec-421e-adbd-827b94a61a69   ext3       BACKDATA
/dev/sdb5        e84ef3fa-40bd-45b5-85ce-e06d445aff21   swap       
/dev/sdc1        b8292d17-77d5-488a-92ad-1cbb7838c9a6   ext3       samsung
/dev/sdc10       e05bcd5b-36ce-4eed-a282-3b1dd77054a5   ext4       
/dev/sdc5        228db4d1-6d0e-478f-bae7-53dc3913028e   ext4       
/dev/sdc6        af1b2958-1cc7-4aea-9080-999703b43074   swap       
/dev/sdc7        7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089   ext4       
/dev/sdc8        eff9e9dc-69e0-40d0-a84e-9ac1cdc1fb66   swap       
/dev/sdc9        4ed99c58-19a1-462b-b781-9e64248a9ec3   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdc10       /                        ext4       (rw,errors=remount-ro)
/dev/sdc7        /media/sdc7              ext4       (rw,noexec,nosuid,nodev)


=========================== sdc5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 228db4d1-6d0e-478f-bae7-53dc3913028e
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
insmod ext2
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 228db4d1-6d0e-478f-bae7-53dc3913028e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set 228db4d1-6d0e-478f-bae7-53dc3913028e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd2,5)'
	search --no-floppy --fs-uuid --set 228db4d1-6d0e-478f-bae7-53dc3913028e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Ubuntu, with Linux 2.6.32-32-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b5a9b5be-6ccc-453b-b871-2a90f3738bcd
	linux /boot/vmlinuz-2.6.32-32-generic root=UUID=b5a9b5be-6ccc-453b-b871-2a90f3738bcd ro quiet splash
	initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, with Linux 2.6.32-32-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b5a9b5be-6ccc-453b-b871-2a90f3738bcd
	linux /boot/vmlinuz-2.6.32-32-generic root=UUID=b5a9b5be-6ccc-453b-b871-2a90f3738bcd ro single
	initrd /boot/initrd.img-2.6.32-32-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b5a9b5be-6ccc-453b-b871-2a90f3738bcd
	linux /boot/vmlinuz-2.6.32-31-generic root=UUID=b5a9b5be-6ccc-453b-b871-2a90f3738bcd ro quiet splash
	initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "Ubuntu, with Linux 2.6.32-31-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b5a9b5be-6ccc-453b-b871-2a90f3738bcd
	linux /boot/vmlinuz-2.6.32-31-generic root=UUID=b5a9b5be-6ccc-453b-b871-2a90f3738bcd ro single
	initrd /boot/initrd.img-2.6.32-31-generic
}
menuentry "openSUSE 11.1 - 2.6.27.7-9 (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 6b96b0d1-820a-4f84-bbfc-bddbee9ae9ec
	linux /boot/vmlinuz-2.6.27.7-9-default root=/dev/disk/by-id/ata-ST3320620AS_5QF35TNJ-part4 resume=/dev/disk/by-id/ata-ST3320620AS_5QF35TNJ-part5 splash=silent showopts vga=0x317
	initrd /boot/initrd-2.6.27.7-9-default
}
menuentry "Failsafe -- openSUSE 11.1 - 2.6.27.7-9 (on /dev/sdb4)" {
	insmod ext2
	set root='(hd1,4)'
	search --no-floppy --fs-uuid --set 6b96b0d1-820a-4f84-bbfc-bddbee9ae9ec
	linux /boot/vmlinuz-2.6.27.7-9-default root=/dev/disk/by-id/ata-ST3320620AS_5QF35TNJ-part4 showopts ide=nodma apm=off noresume edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
	initrd /boot/initrd-2.6.27.7-9-default
}
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sdc5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=228db4d1-6d0e-478f-bae7-53dc3913028e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=af1b2958-1cc7-4aea-9080-999703b43074 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdc5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.32-33-generic              1
               =                boot/vmlinuz-2.6.32-33-generic                 1
               =                initrd.img                                     1
               =                vmlinuz                                        1

=========================== sdc7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd2,msdos7)'
search --no-floppy --fs-uuid --set=root 7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos7)'
  search --no-floppy --fs-uuid --set=root 7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 3.0.0-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos7)'
	search --no-floppy --fs-uuid --set=root 7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-19-generic
}
menuentry "Ubuntu, with Linux 3.0.0-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos7)'
	search --no-floppy --fs-uuid --set=root 7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089
	echo	'Loading Linux 3.0.0-19-generic ...'
	linux	/boot/vmlinuz-3.0.0-19-generic root=UUID=7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-19-generic
}
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos7)'
	search --no-floppy --fs-uuid --set=root 7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos7)'
	search --no-floppy --fs-uuid --set=root 7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
### END /etc/grub.d/30_os-prober_proxy ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdc7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sdc7 during installation
UUID=7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089  /               ext4  users,user                0  1  
# swap was on /dev/sdc8 during installation
UUID=eff9e9dc-69e0-40d0-a84e-9ac1cdc1fb66  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
# /dev/sdb2                                  /media/sdb2     ext3  defaults                  0  0  
--------------------------------------------------------------------------------

=================== sdc7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-19-generic               2
               =                boot/vmlinuz-3.0.0-19-generic                  2
               =                vmlinuz                                        2

=============================== sdc9/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc9 during installation
UUID=4ed99c58-19a1-462b-b781-9e64248a9ec3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=af1b2958-1cc7-4aea-9080-999703b43074 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdc9: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

========================== sdc10/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd2,msdos10)'
search --no-floppy --fs-uuid --set=root e05bcd5b-36ce-4eed-a282-3b1dd77054a5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd2,msdos10)'
  search --no-floppy --fs-uuid --set=root e05bcd5b-36ce-4eed-a282-3b1dd77054a5
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos10)'
	search --no-floppy --fs-uuid --set=root e05bcd5b-36ce-4eed-a282-3b1dd77054a5
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=e05bcd5b-36ce-4eed-a282-3b1dd77054a5 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos10)'
	search --no-floppy --fs-uuid --set=root e05bcd5b-36ce-4eed-a282-3b1dd77054a5
	echo	'Loading Linux 3.2.0-24-generic ...'
	linux	/boot/vmlinuz-3.2.0-24-generic root=UUID=e05bcd5b-36ce-4eed-a282-3b1dd77054a5 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-24-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos10)'
	search --no-floppy --fs-uuid --set=root e05bcd5b-36ce-4eed-a282-3b1dd77054a5
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=e05bcd5b-36ce-4eed-a282-3b1dd77054a5 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos10)'
	search --no-floppy --fs-uuid --set=root e05bcd5b-36ce-4eed-a282-3b1dd77054a5
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=e05bcd5b-36ce-4eed-a282-3b1dd77054a5 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos10)'
	search --no-floppy --fs-uuid --set=root e05bcd5b-36ce-4eed-a282-3b1dd77054a5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos10)'
	search --no-floppy --fs-uuid --set=root e05bcd5b-36ce-4eed-a282-3b1dd77054a5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.04.3 LTS (10.04) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root 228db4d1-6d0e-478f-bae7-53dc3913028e
	linux /vmlinuz root=/dev/sdc5
	initrd /initrd.img
}
menuentry "Ubuntu 10.04.3 LTS (10.04) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root 228db4d1-6d0e-478f-bae7-53dc3913028e
	linux /vmlinuz root=/dev/sdc5
	initrd /initrd.img
}
menuentry "Ubuntu 10.04.3 LTS (10.04) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root 228db4d1-6d0e-478f-bae7-53dc3913028e
	linux /boot/vmlinuz-2.6.32-33-generic root=/dev/sdc5
	initrd /boot/initrd.img-2.6.32-33-generic
}
menuentry "Ubuntu 10.04.3 LTS (10.04) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root 228db4d1-6d0e-478f-bae7-53dc3913028e
	linux /vmlinuz root=/dev/sdc5
	initrd /initrd.img
}
menuentry "Ubuntu 10.04.3 LTS (10.04) (on /dev/sdc5)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos5)'
	search --no-floppy --fs-uuid --set=root 228db4d1-6d0e-478f-bae7-53dc3913028e
	linux /vmlinuz root=/dev/sdc5
	initrd /initrd.img
}
menuentry "Ubuntu, with Linux 3.0.0-19-generic (on /dev/sdc7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos7)'
	search --no-floppy --fs-uuid --set=root 7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089
	linux /boot/vmlinuz-3.0.0-19-generic root=UUID=7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-19-generic
}
menuentry "Ubuntu, with Linux 3.0.0-19-generic (recovery mode) (on /dev/sdc7)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos7)'
	search --no-floppy --fs-uuid --set=root 7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089
	linux /boot/vmlinuz-3.0.0-19-generic root=UUID=7bbd88fe-2e6b-4685-ad1d-edfe2ccdf089 ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-19-generic
}
menuentry "Ubuntu 12.04 LTS (12.04) (on /dev/sdc9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos9)'
	search --no-floppy --fs-uuid --set=root 4ed99c58-19a1-462b-b781-9e64248a9ec3
	linux /vmlinuz root=/dev/sdc9
}
menuentry "Ubuntu 12.04 LTS (12.04) (on /dev/sdc9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos9)'
	search --no-floppy --fs-uuid --set=root 4ed99c58-19a1-462b-b781-9e64248a9ec3
	linux /boot/vmlinuz-3.2.0-23-generic root=/dev/sdc9
}
menuentry "Ubuntu 12.04 LTS (12.04) (on /dev/sdc9)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd2,msdos9)'
	search --no-floppy --fs-uuid --set=root 4ed99c58-19a1-462b-b781-9e64248a9ec3
	linux /vmlinuz root=/dev/sdc9
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdc10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sdc10 during installation
UUID=e05bcd5b-36ce-4eed-a282-3b1dd77054a5  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sdc6 during installation
UUID=af1b2958-1cc7-4aea-9080-999703b43074  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdc7                                  /media/sdc7     ext4  users,user                0  0  
--------------------------------------------------------------------------------

=================== sdc10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/initrd.img-3.2.0-24-generic               1
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                boot/vmlinuz-3.2.0-24-generic                  1
               =                initrd.img                                     1
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ea 53 10 00 00 00 00 00  00 00 00 00 00 00 00 00  |.S..............|
00000010  00 00 00 00 00 00 00 00  21 00 00 00 00 00 00 00  |........!.......|
00000020  ea 53 10 00 00 00 00 00  00 00 00 00 00 00 00 00  |.S..............|
00000030  00 00 00 00 00 00 00 00  21 00 00 00 00 00 00 00  |........!.......|
00000040  ea 53 10 00 00 00 00 00  00 00 00 00 00 00 00 00  |.S..............|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  21 00 00 00 00 00 00 00  |........!.......|
00000070  ea 53 10 00 00 00 00 00  00 00 00 00 00 00 00 00  |.S..............|
00000080  20 00 00 00 00 00 00 00  af c1 0f 00 00 00 00 00  | ...............|
00000090  00 00 00 00 00 00 00 00  20 00 00 00 00 00 00 00  |........ .......|
000000a0  bd bf 0f 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000c0  00 00 00 00 00 00 00 00  21 00 00 00 00 00 00 00  |........!.......|
000000d0  ea 53 10 00 00 00 00 00  00 00 00 00 00 00 00 00  |.S..............|
000000e0  20 00 00 00 00 00 00 00  3a d3 10 00 00 00 00 00  | .......:.......|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  21 00 00 00 00 00 00 00  |........!.......|
00000110  ea 53 10 00 00 00 00 00  00 00 00 00 00 00 00 00  |.S..............|
00000120  20 00 00 00 00 00 00 00  3a d3 10 00 00 00 00 00  | .......:.......|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  21 00 00 00 00 00 00 00  |........!.......|
00000150  ea 53 10 00 00 00 00 00  00 00 00 00 00 00 00 00  |.S..............|
00000160  20 00 00 00 00 00 00 00  e5 1e 10 00 00 00 00 00  | ...............|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  21 00 00 00 00 00 00 00  |........!.......|
00000190  ea 53 10 00 00 00 00 00  00 00 00 00 00 00 00 00  |.S..............|
000001a0  20 00 00 00 00 00 00 00  97 c1 0f 00 00 00 00 00  | ...............|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d0 b7 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb3

00000000  03 11 07 06 53 0d 0e 05  08 12 07 09 0d 0c 0c 16  |....S...........|
00000010  3f 09 03 15 0e 06 08 04  03 17 0b 03 03 07 08 04  |?...............|
00000020  03 0b 28 5f 03 0e 03 ba  01 06 10 04 03 40 0a 05  |..(_.........@..|
00000030  4e 11 0b 05 4e 11 0b 05  4e 11 0b 67 01 0d 0a 06  |N...N...N..g....|
00000040  03 14 a8 03 d0 01 05 4e  11 0b 7c 01 38 02 64 09  |.......N..|.8.d.|
00000050  0b 21 09 09 09 09 09 07  11 08 04 05 0c 1d 08 07  |.!..............|
00000060  08 07 06 0b 07 0b 07 0d  07 0d 07 0d 07 0d 07 0d  |................|
00000070  76 d4 01 08 0c 0e 58 02  02 5f 23 24 dd 02 01 20  |v.....X.._#$... |
00000080  1d 26 88 03 a1 06 1d 18  a4 07 03 1c 01 04 03 06  |.&..............|
00000090  01 04 01 fa 02 02 9b 01  04 3f 03 41 03 b2 02 03  |.........?.A....|
000000a0  bf 01 03 06 4e 11 5e 62  61 0e 5e 5f ac 01 23 06  |....N.^ba.^_..#.|
000000b0  4d 10 9d 01 95 03 05 4e  11 0b a6 01 cb 02 85 02  |M......N........|
000000c0  31 f5 02 7b 11 04 c6 01  a4 02 18 b2 06 5c f6 01  |1..{.........\..|
000000d0  ea 02 18 57 50 17 dd 07  c6 03 8e 01 ab 01 8a 01  |...WP...........|
000000e0  8c 07 ed 05 dd 01 a0 08  cf 01 0b 23 3d 50 db 07  |...........#=P..|
000000f0  c0 01 ae 0b 4a bb 01 f4  02 5f 82 02 34 47 63 18  |....J...._..4Gc.|
00000100  e9 02 e1 01 78 55 64 3d  0e a0 01 41 9a 01 06 83  |....xUd=...A....|
00000110  05 4a 17 c9 01 73 c3 02  42 f1 06 75 ac 03 db 01  |.J...s..B..u....|
00000120  32 38 a7 02 59 a1 01 dc  02 b3 03 ea 04 e8 06 39  |28..Y..........9|
00000130  39 1a 2a 08 f3 04 8c 01  e9 02 fa 02 bc 05 c8 01  |9.*.............|
00000140  bf 01 1d 1b a6 06 0a 12  82 03 10 61 08 e0 01 26  |...........a...&|
00000150  2c aa 01 8f 06 d6 03 da  02 21 7d 14 0b 06 09 99  |,........!}.....|
00000160  04 9a 01 90 05 ec 01 ee  02 08 ac 01 c0 04 e6 01  |................|
00000170  5d 35 0f 9d 01 0a 15 06  67 09 3d 0b 00 04 60 13  |]5......g.=...`.|
00000180  b8 01 b1 01 40 76 03 be  04 00 26 24 1f 02 1a 04  |....@v....&$....|
00000190  16 07 07 07 06 09 03 07  f4 08 a3 01 06 0a 0a 0e  |................|
000001a0  0f 65 67 38 3b 53 6b e5  01 68 15 c7 01 04 26 04  |.eg8;Sk..h....&.|
000001b0  9f 01 14 09 12 0a 20 33  12 11 0f 08 32 12 00 fe  |...... 3....2...|
000001c0  ff ff 82 fe ff ff 89 e9  4f 00 75 a1 a9 00 00 00  |........O.u.....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by oldfred on 2012-05-06
Which way are you booting 11.10? It looks like the grub installs in both sda & sdb boot sdc7 (UUID as shown).

You also have entry in the menu for booting from sdc which boots 12.04 in sdc10. The menu entry for 11.10 does not mention version but just kernel version. If this is the most up to date I would try it.

Have you tried all 3 ways to boot?

I now looks like you only have swap on sda.

---

### Post by darkod on 2012-05-07
OK, first of all you have some kind of grub2 with embedded files on both /dev/sda and /dev/sdb.
The grub2 on /dev/sdc looks good and from 12.04 LTS. I would try to use this grub2 and I don't think you are using it right now since you needed to run update-grub to add 12.04 to your boot menu. So, go into BIOS and set the /dev/sdc disk, 1TB, to be first boot option.

That should give you a fully working boot menu with 12.04 as main option, then with 10.04.3 and 11.10, and one 12.04 install on sdc9 which seems broken.

Try that and try whether it can boot all three systems without any problem except the 12.04 on sdc9 which I am not sure can work right now.

Lets see what happens.

---

### Post by Oldhacker on 2012-05-07
Sad to report that when I went in BIOS the 1TB disk already was set to be my first boot option. (It was easy to determine which HD that was as my other two physical HD's are from the original computer construction and are of much smaller capacity.)

For information purposes, I tried booting into the first entry for 10.04.3 and that worked. Unfortunately, there is nothing there that I need.
All my important files and applications are on 11.10 and going to Devices from 12.04 shows that everything there is still intact. All I need is to be able to access them. 

I have been a real pest, haven't I?

---

### Post by oldfred on 2012-05-07
And if you boot this entry what happens?

Ubuntu, with Linux 3.0.0-19-generic (on /dev/sdc7)

---

### Post by darkod on 2012-05-07
So, the default 12.04 and the 10.04.3 work. As oldfred beat me to it, what happens if you try the 11.10 from sdc7?

Also, you might try booting the 12.04 and running
sudo update-grub

to see if it will recreate the grub.cfg better. But the current one looks OK, everything seems correct. This might be something related to the 11.10.

---

### Post by Oldhacker on 2012-05-07
Running sudo update-grub ended with the following encouraging lines:
Found Ubuntu 10.04.3 LTS (10.04) on /dev/sdc5
Found Ubuntu 11.10 (11.10) on /dev/sdc7
Found Ubuntu 12.04 LTS (12.04) on /dev/sdc9

***A little strange that it found 11.10 on /dev/sdc9 instead of on /dev/sdc10***

In any case, trying for 11.10 on /dev/sdc7 brought up the same black screen with a blinking cursor.
Trying the first 10.04 on /dev/sdc5 gave a page of data running fast on a black screen and then went into 10.04.3 just as before.

It is a "puzzlement" :-(

---

### Post by darkod on 2012-05-07
I noticed something in the fstab of sdc7.

Boot your 12.04, open sdc7, open /etc/fstab and look into the line specifying the root partition.

Instead of the options users,user put errors=remount-ro.

So, at the end it should be like:
UUID=XXXXX   /   ext4   errors=remount-ro   0   1

I guess you put the users,user there because in the install by default it's the above option.

Save and close the file after the edit. Restart and try booting 11.10 from sdc7.

And in your last post you made a small typo, there is no 11.10 detected on sdc9, but there is 12.04 detected on sdc9. I mentioned that, but that will be easy to sort out once you get your 11.10 going.

We are waiting further info about the above try. :)

---

### Post by Oldhacker on 2012-05-07
It worked! IT WORKED!! **YOU DID IT!!!**

If Y'all were a little closer to Texas, I'd take everyone who helped to lunch!

Thanks again  (I won't upset the results by doing any more editing unless I am exactly certain what i am doing):)

---

### Post by darkod on 2012-05-07
Glad we could help.

The next step will probably be to format sdc9 and that would get rid of the broken 12.04 on it. I say broken because from first glance at the results, it looks like it won't work and like it's some kind of earlier failed attempt. You have your working 12.04 on sdc10.

After you format sdc9 you can use it as data partition. And when you run update-grub it will delete the 12.04 (sdc9) from the boot menu. One entry less.

Also, I would consider removing the sdc7 mount in fstab in your 12.04.

Don't forget that is the root partition of the 11.10 and any "mistake" while working in it, can have effects on 11.10.

I would prefer not touching the root partitions of other installs. That's why you have separate data partition and you can work there no problem.

Even if you need to mount it sometimes, do it as temporary mount by clicking on it in the file manager. Not as permanent mount on every boot.

But that decision is up to you... :) You know what you use it for.

---

### Post by Oldhacker on 2012-05-08
Formating SDC9 really cleaned up the boot menu.

However, I am not quite clear on where the SDC7 mount is in fstab. Here is a printout of my fstab as it now stands:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc10 during installation
UUID=e05bcd5b-36ce-4eed-a282-3b1dd77054a5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=af1b2958-1cc7-4aea-9080-999703b43074 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by darkod on 2012-05-08
OK, it seems you already removed it. In your results in post #12 the fstab of sdc10 had a mount of /dev/sdc7 as the last line.

Can't copy-paste now because it doesn't keep the layout and looks like hell. :)

---

