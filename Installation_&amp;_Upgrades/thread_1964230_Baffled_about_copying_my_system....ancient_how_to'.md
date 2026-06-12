---
title: "Baffled about copying my system....ancient how to's"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by thegoonden on 2012-04-23
Before attempting to upgrade my system from 11.10 to 12.04 I thought I would make a working copy of it so I had something to fall back to if it all went horribly wrong (which from my attempts at a clean install, it will).

What I have done......
booted from the 12.04 CD
mounted the old and new root partitions
copied, using cp -av thusly
cp -av /oldroot/* /newroot/
Edited the fstab on the newroot to point to itself (tried with both /dev style and using UUID)
rebooted to my oldroot
ran update-grub

Grub does indeed show a listing for a valid 11.10 installation on the appropriate new partition. However, when I select this, I somehow end up back in my original "old root".


Clearly I have missed a step.

All the guides I can find either depend on partimage (which will probably cr*p itself since I am moving to a smaller partition, 10GB instead of the vast and unnecessary 20GB it resides in now) OR they refer to hideously outdated things like editing grub's config file....you know, the one with "don't you dare edit this file!!" at the top of it.

I feel I am but one small step away from having two identical installations, one of which I can chuck a 12.04 upgrade onto....which will make me happy ;)

Thank you kindly folks

---

### Post by darkod on 2012-04-23
Take a look at FS Archiver. It can restore to a smaller partition than the original one as long as it's big enough for the data.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by thegoonden on 2012-04-23
> **darkod said:**
> Take a look at FS Archiver. It can restore to a smaller partition than the original one as long as it's big enough for the data.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)


Thanks, but I THINK I've already gotten past what this will do for me, I will still be left having to make it bootable if you see what I mean.
However, if I have to go back and re-copy, I will indeed take a closer look at this program.

---

### Post by thegoonden on 2012-04-23
As you can see, grub has the UUID for the original/current/running root in one field, and the UUID for the new root in another.......

```


menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos6)'
        search --no-floppy --fs-uuid --set=root 2adbef4d-5d27-413c-b0f0-7d579d09a407
        linux /boot/vmlinuz-3.0.0-12-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro quiet splash vt.handoff=7
        initrd /boot/initrd.img-3.0.0-12-generic


```
 



If I manually edit it when presented with the grub menu, boot failure occurs and I am left at the initramfs busybox prompt.

I'm losing my mind over this, I've moved gentoo systems around like this with no trouble before.

IS there something about Ubuntu that would make cp -av insufficient to copy the contents across, or is the problem with grub?

---

### Post by oldfred on 2012-04-23
If you have two different UUID's, do you have a separate /boot? That is typical for a separate /boot.

And there are exceptions to not editing grub.cfg but very few. You may be one of them to get it to boot the first time, so a grub reinstall or sudo update-grub is run against the correct UUIDs.

bootinfoscript will tell you where everything is installed and what are your UUIDs.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by thegoonden on 2012-04-23
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    15312864 of the same hard drive for core.img. core.img is at this location 
    and looks for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             32    48,828,415    48,828,384  83 Linux
/dev/sda2          48,828,446   125,042,687    76,214,242   5 Extended
/dev/sda5          48,828,448    97,656,831    48,828,384  83 Linux
/dev/sda6          97,656,864   121,137,332    23,480,469  83 Linux
/dev/sda7         121,139,200   125,042,687     3,903,488  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   937,505,204   937,505,142  83 Linux
/dev/sdb2         937,505,266 1,953,523,054 1,016,017,789   5 Extended
/dev/sdb5         937,505,268 1,875,010,409   937,505,142  83 Linux
/dev/sdb6    *  1,875,010,473 1,894,545,449    19,534,977  83 Linux
/dev/sdb7       1,894,545,513 1,953,523,054    58,977,542  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   976,559,219   976,559,157  83 Linux
/dev/sdc2         976,559,220 1,953,520,064   976,960,845   5 Extended
/dev/sdc5         976,559,283 1,914,064,424   937,505,142  83 Linux
/dev/sdc6       1,914,064,488 1,953,520,064    39,455,577  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        78d29c12-a163-441b-9329-9cd6ae12ee6e   ext4       
/dev/sda5        9728afa3-eefa-4f1c-b289-44a9afe07e92   ext4       
/dev/sda6        9b1fd8d8-8155-4c4c-90da-3c2962b04ae8   ext3       
/dev/sda7        1004807a-4b91-44b4-a5d5-d21983dde679   swap       
/dev/sdb1        c910605f-5c34-4c26-9891-17f957a9299f   ext4       
/dev/sdb5        cd639c5e-c55e-4d9f-946e-ebceef9885f7   ext3       
/dev/sdb6        2adbef4d-5d27-413c-b0f0-7d579d09a407   ext4       
/dev/sdb7        f1668367-b609-410d-be34-460afc3e5f20   ext4       
/dev/sdc1        631ccd1d-026c-425c-a349-ebeffe05ebdb   ext3       
/dev/sdc5        9ea62ecf-413f-4748-83b8-60cb64e9e883   ext3       
/dev/sdc6        d3ebc642-f6d9-4d7c-9c5e-1876e4d7ee48   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /home                    ext4       (rw,commit=0)
/dev/sdb1        /mnt/media               ext4       (rw,commit=0)
/dev/sdb5        /mnt/dump                ext3       (rw,commit=0)
/dev/sdb6        /mnt/test                ext4       (rw)
/dev/sdc1        /mnt/play                ext3       (rw,commit=0)
/dev/sdc5        /mnt/work                ext3       (rw,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 0,71,115; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9b1fd8d8-8155-4c4c-90da-3c2962b04ae8
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b1fd8d8-8155-4c4c-90da-3c2962b04ae8 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9b1fd8d8-8155-4c4c-90da-3c2962b04ae8
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b1fd8d8-8155-4c4c-90da-3c2962b04ae8 ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 2adbef4d-5d27-413c-b0f0-7d579d09a407
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 2adbef4d-5d27-413c-b0f0-7d579d09a407
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 2adbef4d-5d27-413c-b0f0-7d579d09a407
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 2adbef4d-5d27-413c-b0f0-7d579d09a407
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro recovery nomodeset
	initrd /boot/initrd.img-2.6.38-8-generic
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=9728afa3-eefa-4f1c-b289-44a9afe07e92 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=1004807a-4b91-44b4-a5d5-d21983dde679 none            swap    sw              0       0


/dev/sdb1 	        /mnt/media	ext4   defaults 1 2
/dev/sdc1               /mnt/play 	ext3 defaults 1 2
/dev/sdc5               /mnt/work	ext3 defaults 1 2
/dev/sdb5               /mnt/dump 	ext3 defaults 1 2

--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   6.890781403 = 7.398920192    boot/grub/core.img                             1
   6.849807739 = 7.354925056    boot/grub/grub.cfg                             1
  15.804702759 = 16.970170368   boot/initrd.img-2.6.38-8-generic               3
  22.414077759 = 24.066932736   boot/initrd.img-3.0.0-12-generic               2
  20.785480499 = 22.318239744   boot/vmlinuz-2.6.38-8-generic                  1
  11.492202759 = 12.339658752   boot/vmlinuz-3.0.0-12-generic                  2
  22.414077759 = 24.066932736   initrd.img                                     2
  11.492202759 = 12.339658752   vmlinuz                                        2

=========================== sda6/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 9b1fd8d8-8155-4c4c-90da-3c2962b04ae8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 9b1fd8d8-8155-4c4c-90da-3c2962b04ae8
set locale_dir=($root)/boot/grub/locale
set lang=
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 9b1fd8d8-8155-4c4c-90da-3c2962b04ae8
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=9b1fd8d8-8155-4c4c-90da-3c2962b04ae8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 9b1fd8d8-8155-4c4c-90da-3c2962b04ae8
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=9b1fd8d8-8155-4c4c-90da-3c2962b04ae8 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 9b1fd8d8-8155-4c4c-90da-3c2962b04ae8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 9b1fd8d8-8155-4c4c-90da-3c2962b04ae8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Gentoo Base System release 1.12.13 (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 87464a36-dfa3-42b5-aa1a-1570daa2827c
	linux /boot/vmlinuz-2.6.20-gentoo-r8 root=/dev/sda1
}
menuentry "Gentoo Base System release 1.12.13 (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 87464a36-dfa3-42b5-aa1a-1570daa2827c
	linux /boot/vmlinuz-2.6.25-gentoo-r7 root=/dev/sda1
}
menuentry "Gentoo Base System release 1.12.13 (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 87464a36-dfa3-42b5-aa1a-1570daa2827c
	linux /boot/vmlinuz-2.6.25-gentoo-r7.old root=/dev/sda1
}
menuentry "Gentoo Base System release 1.12.13 (on /dev/sda1)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 87464a36-dfa3-42b5-aa1a-1570daa2827c
	linux /boot/vmlinuz-2.6.31-gentoo-r6 root=/dev/sda1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###


# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.


menuentry "Gentoo 2.6.31 (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 87464a36-dfa3-42b5-aa1a-1570daa2827c
	linux /boot/kernel-genkernel-x86_64-2.6.31-gentoo-r6 root=/dev/sda1 vga=794 doscsi

menuentry "Gentoo 2.6.25 (on /dev/sda1)" {
        insmod ext2
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 87464a36-dfa3-42b5-aa1a-1570daa2827c
        linux /boot/kernel-genkernel-x86_64-2.6.25-gentoo-r7 root=/dev/sda1 vga=794 doscsi
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=9b1fd8d8-8155-4c4c-90da-3c2962b04ae8 /               ext3    errors=remount-ro 0       1
# Commented out by Dropbox
# /dev/sda5		/home				ext3 defaults 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sdb1       /mnt/media      ext3   defaults 1 2
/dev/sdc1               /mnt/play ext3 defaults 1 2
/dev/sdc5               /mnt/work ext3 defaults 1 2
/dev/sdb5               /mnt/dump ext3 defaults 1 2



//guzunda/shared /mnt/shared cifs username=steve,password=steve,uid=steve,gid=users,noauto,user,defaults 0 0



//guzunda/shared/store/download/ /mnt/shared/store/download cifs username=steve,password=steve,uid=steve,gid=users,noauto,user,defaults 0 0



/dev/sda5 /home ext4 defaults,user_xattr 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  47.219715118 = 50.701783040   boot/grub/core.img                             1
  47.105499268 = 50.579144704   boot/grub/grub.cfg                             1
  47.134552002 = 50.610339840   boot/initrd.img-2.6.35-24-generic              8
  47.185607910 = 50.665160704   boot/vmlinuz-2.6.35-24-generic                 6
  47.134552002 = 50.610339840   initrd.img                                     8
  47.185607910 = 50.665160704   vmlinuz                                        6

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_GB
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
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
insmod png
if background_image /usr/share/images/desktop-base/spacefun-grub.png; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 0,71,115; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 78d29c12-a163-441b-9329-9cd6ae12ee6e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.35-24-generic (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9b1fd8d8-8155-4c4c-90da-3c2962b04ae8
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b1fd8d8-8155-4c4c-90da-3c2962b04ae8 ro quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 2.6.35-24-generic (recovery mode) (on /dev/sda6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set=root 9b1fd8d8-8155-4c4c-90da-3c2962b04ae8
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=9b1fd8d8-8155-4c4c-90da-3c2962b04ae8 ro single
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 2adbef4d-5d27-413c-b0f0-7d579d09a407
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=2adbef4d-5d27-413c-b0f0-7d579d09a407 ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 3.0.0-12-generic (recovery mode) (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 2adbef4d-5d27-413c-b0f0-7d579d09a407
	linux /boot/vmlinuz-3.0.0-12-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro recovery nomodeset
	initrd /boot/initrd.img-3.0.0-12-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 2adbef4d-5d27-413c-b0f0-7d579d09a407
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro quiet splash vt.handoff=7
	initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, with Linux 2.6.38-8-generic (recovery mode) (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos6)'
	search --no-floppy --fs-uuid --set=root 2adbef4d-5d27-413c-b0f0-7d579d09a407
	linux /boot/vmlinuz-2.6.38-8-generic root=UUID=78d29c12-a163-441b-9329-9cd6ae12ee6e ro recovery nomodeset
	initrd /boot/initrd.img-2.6.38-8-generic
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

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=2adbef4d-5d27-413c-b0f0-7d579d09a407 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=9728afa3-eefa-4f1c-b289-44a9afe07e92 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
# UUID=1004807a-4b91-44b4-a5d5-d21983dde679 none            swap    sw              0       0


/dev/sdb1 	        /mnt/media	ext4   defaults 1 2
/dev/sdc1               /mnt/play 	ext3 defaults 1 2
/dev/sdc5               /mnt/work	ext3 defaults 1 2
/dev/sdb5               /mnt/dump 	ext3 defaults 1 2

--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 899.805382252 = 966.158672384  boot/grub/core.img                             1
 898.340298176 = 964.585550336  boot/grub/grub.cfg                             1
 896.764336109 = 962.893373952  boot/initrd.img-2.6.38-8-generic               1
 896.733547688 = 962.860315136  boot/initrd.img-3.0.0-12-generic               1
 896.766380787 = 962.895569408  boot/vmlinuz-2.6.38-8-generic                  2
 896.774319172 = 962.904093184  boot/vmlinuz-3.0.0-12-generic                  1
 916.488728046 = 984.072278528  initrd.img                                     2
 896.774319172 = 962.904093184  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ff ff ff ff ff ff ff ff  ff 7f fd ff ff 7f ff ff  |................|
00000010  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff fe ff  |................|
00000020  ff ff ff ff ff fe ff ff  ff ff ff ff ff df bf ff  |................|
00000030  ff ff ff ff fb ff ff ff  ff ff ff ff ff ff ff ff  |................|
00000040  ff ff ff ff ff ff ff ff  ff bf ff ff ff ff ff ff  |................|
00000050  ff ff ff ff ff ff fd ff  ff ff ff ff ff ff ff ff  |................|
00000060  ff ff ff ff ff ff ff ff  ff ff ff ff ff 7f ff ff  |................|
00000070  ff ff ff ff ff ff f7 ff  fd ff ff ff ff ff ff ff  |................|
00000080  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
00000090  ff ff ff ff ff ff ff ff  ff ff ff fe ff ff ff fb  |................|
000000a0  ff ff bf ff ff ff ff ff  ff ff ff ff ff ff fd ff  |................|
000000b0  ff ff ff ff ff ff ff ff  ff ff ff 7f f7 ff ff ff  |................|
000000c0  ff ff ff ff ff ff ff f7  ff ff ff ff ff ff ff ff  |................|
000000d0  ff ff ff ff ff ff ff 7f  ff ff ff ff f7 ff ff ff  |................|
000000e0  ff ff ff ff ff ff ff ff  ff ff bf ff ff ff ff ff  |................|
000000f0  ff ff ff ff ff ff ff ff  ff ff fe ff ff ff ff ff  |................|
00000100  ff ff ff ff fe f7 ff ff  ff ff ff ff ff ff ff ff  |................|
00000110  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
00000160  ff ff ff ff ff ff f7 ff  ff ff ef ff ff ff ff ff  |................|
00000170  ff ff fe ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
00000180  ff f7 ff fe ff ff ff df  ff ff ff ff ff ff ff ff  |................|
00000190  fd ff ff ff df ff ff fd  ff ff ff bf ff ff ff ff  |................|
000001a0  ff ef ff ff ff ff ff ff  ff ff ff ff fd ff ff ff  |................|
000001b0  ff ff ff ff fe ff ff ff  ff ff 7f ff fe ff 00 3f  |...............?|
000001c0  e0 ff 83 3f e0 ff 02 00  00 00 e0 0f e9 02 00 fe  |...?............|
000001d0  ff ff 05 fe ff ff e2 0f  e9 02 b5 48 66 01 00 00  |...........Hf...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb2

00000000  f1 81 7e ed 96 8b 6e cd  8f c1 57 2c 96 2a 3f 7c  |..~...n...W,.*?||
00000010  61 71 4d e7 17 ce 69 96  3f b9 67 15 9b 9d 42 9b  |aqM...i.?.g...B.|
00000020  48 f1 44 53 17 c6 5d c9  62 9b d7 77 0b 2c 43 5b  |H.DS..].b..w.,C[|
00000030  a2 41 f5 5e e5 7f 1d 99  8c 9f 56 6d e3 9c 20 8b  |.A.^......Vm.. .|
00000040  7b e6 72 2e a7 e5 97 b9  61 6f 3d 9d 7f 15 4a f1  |{.r.....ao=...J.|
00000050  f4 95 8f d0 c3 06 41 f8  4a c9 c1 dc e1 d1 a7 50  |......A.J......P|
00000060  ef 13 5b 65 f1 c5 b3 b0  e9 b5 72 ee ec 2c 29 be  |..[e......r..,).|
00000070  a5 f7 d1 c5 d5 37 92 8b  9d d7 dc b9 c7 4a 16 57  |.....7.......J.W|
00000080  33 f5 f0 c2 2b 93 f1 d1  88 94 dc f4 8e 07 51 8b  |3...+.........Q.|
00000090  aa df b9 f1 d1 73 f0 9b  c1 7a f8 f1 b4 29 38 ff  |.....s...z...)8.|
000000a0  77 33 87 92 5b 9e a8 f3  9f 84 dc 2f 7d 13 70 f1  |w3..[....../}.p.|
000000b0  d8 df dc 2e 7d 29 6e d3  ee 8f 4b 9b 8d 8b 95 d7  |....})n...K.....|
000000c0  d6 3c eb 37 94 ac 53 cb  26 9b e0 2d 33 dd 71 e3  |.<.7..S.&..-3.q.|
000000d0  9c 4e 32 eb c6 9f b8 7b  a7 53 65 0d 7a 4b 71 d8  |.N2....{.Se.zKq.|
000000e0  0c 43 fc 6b 8f 27 1e fe  a2 bb ac 68 ef 4e b1 d7  |.C.k.'.....h.N..|
000000f0  a1 ed 32 17 f2 5e 43 ae  7f e3 96 9a 49 71 4a ab  |..2..^C.....IqJ.|
00000100  f7 2e 59 b7 df 48 8c 67  2b f2 8d 9f b3 f8 4f 0f  |..Y..H.g+.....O.|
00000110  13 dc 62 a5 3b ae 8c 98  9a 1b be 46 17 54 55 7e  |..b.;......F.TU~|
00000120  95 0d ac 4e c6 ab f2 74  f1 54 d9 14 6c 6d 73 32  |...N...t.T..lms2|
00000130  97 59 ec 07 82 8e be 92  95 e7 c5 e3 3d 97 ef 70  |.Y..........=..p|
00000140  f7 b7 48 f1 99 3f 9c 4b  83 77 ab 98 f4 f9 92 82  |..H..?.K.w......|
00000150  7e be 64 7d b7 bc a7 fc  f1 8a c5 b5 af 83 c5 5d  |~.d}...........]|
00000160  0f a6 8a 07 bc 7b 9a 1f  40 ce 3b a3 75 99 52 e7  |.....{..@.;.u.R.|
00000170  25 59 0f 9d e2 c5 d7 16  21 17 ff 5f 76 f9 c4 7f  |%Y......!.._v...|
00000180  c0 ca 0b 77 94 2e af 59  9c 2b 8e 14 b7 3b 70 50  |...w...Y.+...;pP|
00000190  b1 26 f4 b3 53 3b f2 f7  ec 6f 77 94 3d c8 df 6b  |.&..S;...ow.=..k|
000001a0  9e 25 88 a7 8f 6a a0 6c  1a 3a da f9 34 19 7f 4e  |.%...j.l.:..4..N|
000001b0  3d 0a 94 cf 2a 59 ec c9  4e 15 0f 88 0f 54 00 fe  |=...*Y..N....T..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 76 31 e1 37 00 fe  |..........v1.7..|
000001d0  ff ff 05 fe ff ff 78 31  e1 37 c0 14 2a 01 00 00  |......x1.7..*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt

```


PLEASE NOTE THE FOLLOWING:
/dev/sda1 is the current "old" system.
/dev/sb6 is the new/target system
**I have manually edited /etc/fstab on the target partition (including the comment line that did read /dev/sda1....don't ask, desperation had kicked in LOL)
I have, as you can see, no separate /boot.

Also, there is something iffy with /dev/sda in that grub works from it, and reflects updates no problem, but refuses to reinstall to it, so I've been using /dev/sdb ....hence the presence of a bootloader on that drive (I can select it in bios boot menu)


Thanks :D

***ALSO****
My last attempt to install a working grub was using
udo grub-setup -d /mnt/test/boot/grub /dev/sdb
Which clearly went badly wrong...it failed to give me a boot menu.....grub is looking for the rest of its files in a silly place according to this readout.

---

### Post by oldfred on 2012-04-23
If you can correctly boot into sda1.

sudo grub-install /dev/sda

But grub also remembers which drive's MBR to reinstall to on major updates:

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If not sda then:
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

You can edit grub.cfg or add a boot stanza to 40_custom. I think the os-prober finds the grub.cfg on sdb6 and creates a boot stanza based on that which will be wrong. If fstab is correct (you are using same /home?) then this will boot you directly so you can run the same commands as above but using sdb to clean up the boot entries.

#Add menu entry to 40_custom on your sda1 install, change example from sdb6 to your partition(I updated it).
gksudo gedit /etc/grub.d/40_custom
#update grub menu - note auto generated entry will not be correct.
sudo update-grub

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sdb6 change all 6's to your partition number.

menuentry "Ubuntu on sdb6" {
    set root=(hd1,6)
        linux /vmlinuz root=/dev/sdb6 ro quiet splash
        initrd /initrd.img
}

---

### Post by thegoonden on 2012-04-23
Thanks

This looks like the core problem.........
"You can edit grub.cfg or add a boot stanza to 40_custom. I think the os-prober finds the grub.cfg on sdb6 and creates a boot stanza based on that which will be wrong. If fstab is correct (you are using same /home?) then this will boot you directly so you can run the same commands as above but using sdb.
"

I shall have a try at the manual entry and see what happens...........

---

### Post by thegoonden on 2012-04-23
Added this to /etc/grub.d/40_custom


menuentry "Ubuntu on sdb6" {
set root=(hd1,5)
linux /vmlinuz root=/dev/sdb6 ro quiet splash
initrd /initrd.img
}


Which is right isn't it?

It gave me 
"file not found
first you must load the kernel"

So I guess I have to specify it.
will try that, but I may have to sleep quite soon ;)

---

### Post by thegoonden on 2012-04-23
OK......progress has been made.

I edited the auto-generated grub entry, using the bootloader line editor, but instead of putting in the UUID for the new root..... I put /dev/sdb6 And it booted onto the new partition without a hitch (running it now).

I am burned out now :D
But I will mess about a bit tomorrow with regards to updating and installing grub FROM the "new" Ubuntu.

Will post back when I have got it all singing and dancing.

But for now.....avoiding UUID seemed to help.

Thanks for the help ;)

---

### Post by oldfred on 2012-04-23
It looks like you had the old grub partition numbering?

menuentry "Ubuntu on sdb6" {
set root=([COLOR=Red]hd1,5[/COLOR])
linux /vmlinuz root=/dev/sdb6 ro quiet splash
initrd /initrd.img
}

It should be hd1,6 with grub2.

But if you have it working that is great. From a grub menu, you can manually edit boot stanzas to correct or change to boot something else.

Once booted into your copied install you should just need to do all the updates from inside it to get it to correctly update.

---

### Post by darkod on 2012-04-24
Since you simply copied the whole installation to another partition, I guess grub config files take over some info from the old partition.

Another option would be, after the copy enter the new partition with chroot, purge grub2 totally (that will get rid of all settings and config), reinstall grub2 and recreate the config files. It should work.

---

### Post by thegoonden on 2012-04-24
Once Grub was re-installed (to sdb IN THIS CASE, due to some previous atrocity committed against sda....that I'll have to get to the bottom of another time). Everything played nice.

SO.....the key points are.
bootinfo is bloody useful
And if you edit a boot entry at boot time be ready to try Ye Olde /dev/sd* type entries if UUID fails.

I'm now sitting in 12.04 :D
And aside from an issue that requires searching and/or its own thread, it's running a treat. :D

Thanks one and all.

---

### Post by NTL2009 on 2012-04-24
I'm glad you got this working - this is exactly the kind of thing I want to be able to do. Esp before a re-install, I want to copy my installation to a bootable drive that has smaller partitions than my main install (lots of free space on the original - I don't need to 'copy' free space, and I don't have enough space on my external drive anyhow).

You had problems along the way, and I kinda got lost in all this. Can you explain:

**If you were to repeat this process - what steps would you take to make it go as smoothly as possible the first time?**


Thanks - NTL2009

---

### Post by thegoonden on 2012-04-24
Basically the same things listed in the first post.

"What I have done......
booted from the 12.04 CD
mounted the old and new root partitions
copied, using cp -av thusly
cp -av /oldroot/* /newroot/
Edited the fstab on the newroot to point to itself (tried with both /dev style and using UUID)
rebooted to my oldroot
ran update-grub"

Now, where it fell down on me was that the boot entry in grub for the new install had two different root partitions defined in it. I edited the entry at boot time (select the entry hit e) and put the UUID of the new root in both places where a root is specified, and it fell on its bum. What I had to do to get booted into the new/copied system was put the old style /dev/sd(whatever) type of drive description in (the first "root=" line was already OK, it was the one after the kernel is specified that was wrong.....so the boot entry ended up like...........
"Ubuntu, with Linux 3.0.0-12-generic (on /dev/sdb6)" --class gnu-linux --class gnu --class os {
        insmod part_msdos
        insmod ext2
        set root='(hd1,msdos6)'
        search --no-floppy --fs-uuid --set=root 2adbef4d-5d27-413c-b0f0-7d579d09a407
        linux /boot/vmlinuz-3.0.0-12-generic root=/dev/sdb6 ro quiet splash vt.handoff=7
        initrd /boot/initrd.img-3.0.0-12-generic"

As soon as I got into the "new" Os, I re-ran update-grub and grub-install from there (I had complications that you wont have ;) )

If you need any of the steps explained in more detail, just sing out :D

---

### Post by NTL2009 on 2012-04-24
Thanks for the reply and offer for further help. I need it!

Here's where I'm getting confused - when you say:

*Now, where it fell down on me ..*

was that due to something that you did in those first steps that you would do different now to avoid that problem? Maybe I'm misunderstanding, but it seems like a number of the steps were to get around some issues - so what I'm asking is, can those issues be avoided ahead of time?


Another thing that you mention, and I now remember being confused about when looking through fstab or other config files before - I see these references to entries like "/dev/sdb6". But I know (or at east I think I know, I do get confused here), that if I plug in another external drive or USB stick, those "sdb6" terms can change on a re-boot (they seem to be dynamically assigned at boot-up, according to their overall priorities in the boot settings, and/or the order they come up or something). I just don't understand how these files can use those refs in place of UUIDs (which remain the same until we change them).

Hope that makes some sense. Thanks.


-NTL2009

---

### Post by thegoonden on 2012-04-24
I think, as one of the folks above said, that something was getting picked up from the old grub settings on the new partition. OR it's just because my system is well and truly scrambled ;)

As for the /dev/ method of hard drive description. You are quite correct, they are somewhat dynamic. The can be affected by external drives, but if you make sure all externals are off line at boot time, there is no problem. They will also change if you plug a new disc in that sits "between" two already installed disc (in IDE terms, imagine you already have a primary and secondary master, and you install a primary slave, that will knock your former /dev/sdb to /dev/sdc as they are assigned in BIOS order.....the same is true of SATA, if you have something in the first and third SATA sockets on the motherboard and add something to the second, it will again turn what was sdb into sdc.
Having said all that........
1. That's WHY Ubuntu uses UUID, which is a huge random label assigned to the device, it does not change regardless of configuration of the machine, so the system will always find the right partition.
2. What I had to do with putting in a /dev style entry was only to get me booted the first time, once into the copied version of the system, when I ran grub it re-installed a new grub loader, with everything using UUID (and the right ones).


I suspect you will find that it will work first time for you......my system was probably just getting its own back for previous abuse ;)

---

### Post by oldfred on 2012-04-24
The main things are to edit fstab and then modify grub to boot correct 'new' install. 

Several choices on editing grub. You can edit grub.cfg even though you normally would not (just need to change the first boot stanza). You can manually edit with e on grub menu to change boot stanza to be correct for the location it is with either correct UUIDs or device (/dev/sdXY). Or even use Supergrub to bypass grub and directly boot. Once booted then you can finish the update.

If a removeable device then it is a bit more complicated as the device numbers may change. The device you boot from with BIOS will always be hd0 in grub, numbers then seem to go in SATA port number but external devices may be anything. With one flash drive install I had to use e on grub menu and experiment with every hdX and sdXY until I got it correct.

Ubuntu has links in / (root) to the most current installed kernal and any manual boot is often easier to use the links. Similar to my post above in using the links in a 40_custom entry to boot a partition.

More info rescue mode or manual booting:
[https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting)
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

