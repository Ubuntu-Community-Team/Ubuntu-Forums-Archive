---
title: "Ubuntu 10.04 LTS AMD64 - Upgrade to 2.6.32-33 Doesn't boot anymore"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by SteDolphin on 2011-07-18
Hi there,

This morning I switched my machine and the Update Manager prompted me to upgrade.

So, as usual I did it. After upgrade it asked me to restart.

Since then id didn't boot anymore. Now I have blank screen with a blinking cursor ... immediately after the BIOS screen, so it looks that no OS is loaded.

THANKS in advance.

Steve

---

### Post by lmarmisa on 2011-07-18
Did the Update Manager prompt you to update or to upgrade to a newer version of Ubuntu?.

---

### Post by SteDolphin on 2011-07-18
NO, it was just an update. I did not upgraded to 11.04, as 10.04 is an LTS.

---

### Post by lmarmisa on 2011-07-18
Are you able to boot into older kernel versions at startup?. 

Hold down SHIFT to display the GRUB menu during boot. In certain cases, pressing the ESC key may also display the menu.

---

### Post by SteDolphin on 2011-07-18
NO, I can't. Neither ESC or Shift brings the Grub menu ... :(

---

### Post by lmarmisa on 2011-07-18
> **SteDolphin said:**
> NO, I can't. Neither ESC or Shift brings the Grub menu ... :(

Check if you are able to switch to a tty terminal. Type Alt+Ctr+F1 (there are 6 ttys from F1 to F6) after you get the blank screen with the blinking cursor.

---

### Post by SteDolphin on 2011-07-18
That doesn't work too ...

The problem is that it hangs too fast after the boot. Like is not loading any module.

---

### Post by lmarmisa on 2011-07-18
Boot into an Ubuntu Live CD / USB, Try Ubuntu, open Firefox and go to the web page:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then follow the instructions of that page in order to download and run the boot info script.

Finally post the results in this thread.

Best regards,

Luis

---

### Post by SteDolphin on 2011-07-18
Here we go ... this is the result

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   390,625,279   390,623,232  83 Linux
/dev/sda2         390,627,326   391,604,223       976,898   5 Extended
/dev/sda5         390,627,328   391,604,223       976,896  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        fa50dc45-3ae0-40a8-85f4-4610e9dabe30   ext4       
/dev/sda5        ba7c825d-3836-48d9-95bf-6bad5f4066d6   swap       
/dev/sdb1        91a18bfc-e33c-4fc1-b39f-4101a5eb9a13   ext4       DataDisk

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	echo	'Loading Linux 2.6.32-33-generic ...'
	linux	/boot/vmlinuz-2.6.32-33-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	echo	'Loading Linux 2.6.32-32-generic ...'
	linux	/boot/vmlinuz-2.6.32-32-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-32-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/boot/vmlinuz-2.6.32-31-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/boot/vmlinuz-2.6.32-30-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	echo	'Loading Linux 2.6.32-29-generic ...'
	linux	/boot/vmlinuz-2.6.32-29-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/boot/vmlinuz-2.6.32-28-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	echo	'Loading Linux 2.6.32-27-generic ...'
	linux	/boot/vmlinuz-2.6.32-27-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fa50dc45-3ae0-40a8-85f4-4610e9dabe30
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
UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ba7c825d-3836-48d9-95bf-6bad5f4066d6 none            swap    sw              0       0

# DEV/SDB1
/dev/sdb1	/media/DataDisk	ext4	defaults,errors=remount-ro	0	0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   4.126247406 = 4.430524416    boot/grub/core.img                             1
 148.800361633 = 159.773171712  boot/grub/grub.cfg                             2
   4.258693695 = 4.572737536    boot/initrd.img-2.6.32-24-generic              1
   4.469680786 = 4.799283200    boot/initrd.img-2.6.32-25-generic              1
   0.411087036 = 0.441401344    boot/initrd.img-2.6.32-26-generic              2
   4.297740936 = 4.614664192    boot/initrd.img-2.6.32-27-generic              1
   4.313266754 = 4.631334912    boot/initrd.img-2.6.32-28-generic              1
   3.707958221 = 3.981389824    boot/initrd.img-2.6.32-29-generic              2
 149.271690369 = 160.279257088  boot/initrd.img-2.6.32-30-generic              2
   0.293895721 = 0.315568128    boot/initrd.img-2.6.32-31-generic              2
 149.293937683 = 160.303144960  boot/initrd.img-2.6.32-32-generic              2
 150.510818481 = 161.609760768  boot/initrd.img-2.6.32-33-generic              2
   4.153186798 = 4.459450368    boot/vmlinuz-2.6.32-24-generic                 1
   4.262466431 = 4.576788480    boot/vmlinuz-2.6.32-25-generic                 1
   4.289974213 = 4.606324736    boot/vmlinuz-2.6.32-26-generic                 1
   4.281707764 = 4.597448704    boot/vmlinuz-2.6.32-27-generic                 1
   4.268482208 = 4.583247872    boot/vmlinuz-2.6.32-28-generic                 1
   4.301517487 = 4.618719232    boot/vmlinuz-2.6.32-29-generic                 1
 149.190303802 = 160.191868928  boot/vmlinuz-2.6.32-30-generic                 2
   4.348506927 = 4.669173760    boot/vmlinuz-2.6.32-31-generic                 1
   4.340686798 = 4.660776960    boot/vmlinuz-2.6.32-32-generic                 1
   4.379871368 = 4.702851072    boot/vmlinuz-2.6.32-33-generic                 1
 150.510818481 = 161.609760768  initrd.img                                     2
 149.293937683 = 160.303144960  initrd.img.old                                 2
   4.379871368 = 4.702851072    vmlinuz                                        1
   4.340686798 = 4.660776960    vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 


```

And thanks a lot for your help !!!

---

### Post by lmarmisa on 2011-07-18
The results look pretty good. You have 10 different kernels but you are not able to boot into anyone!!!. :-(

I recommend to reinstall grub following this procedure:

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

I have added the change of one parameter in the file **/etc/default/grub** too.

Boot into an Ubuntu Live CD / USB, open a terminal and type:

```

sudo mount /dev/sda1 /mnt
sudo gedit /mnt/etc/default/grub

```Then add the char **#** to the line

```

# GRUB_HIDDEN_TIMEOUT=0

```Save & Quit.

Continue with these commands:

```

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
update-grub
grub-install /dev/sda
grub-install --recheck /dev/sda
exit
for i in /sys /proc /dev/pts /dev; do sudo umount /mnt$i; done
sudo umount /mnt/usr
sudo umount /mnt
sudo reboot

```

---

### Post by SteDolphin on 2011-07-18
The two procedure the one which you have linked and the one in your posts are quite the same, do I have to do both or just the one in your post ???

I have done only the one in your post. It looks that it worked, but I have exactly the same behaviour ... black screen with blinking cursor ...

---

### Post by lmarmisa on 2011-07-18
> **SteDolphin said:**
> The two procedure the one which you have linked and the one in your posts are quite the same, do I have to do both or just the one in your post ???

I have done only the one in your post. It looks that it worked, but I have exactly the same behaviour ... black screen with blinking cursor ...

Both procedures are really the same. The first link tried to be only a reference. My second procedure adds a change to the file **/mnt/etc/default/grub** in order to show the GRUB menu at startup.

I recommend to take a look to the logs of your system. You will have access to these files after the first mount command (**sudo mount /dev/sda1 /mnt** ). They are located at **/mnt/var/log** . The files **syslog** , **boot.log **and **Xorg.0.log** could give you some clues about the causes of your troubles if the proposed procedure do not fix the problem.

Best regards,

Luis

---

### Post by SteDolphin on 2011-07-18
This will be a last try ... otherwise I think I have to re-install everything from scratch :(

syslog

```
Jul 17 08:36:18 RDZUGW-SP003 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="964" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jul 17 08:36:19 RDZUGW-SP003 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="964" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jul 17 08:36:19 RDZUGW-SP003 anacron[15119]: Job `cron.daily' terminated
Jul 17 08:36:19 RDZUGW-SP003 anacron[15119]: Normal exit (1 job run)
Jul 17 09:17:01 RDZUGW-SP003 CRON[16119]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 10:17:01 RDZUGW-SP003 CRON[16597]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 11:17:01 RDZUGW-SP003 CRON[17028]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 12:03:48 RDZUGW-SP003 dhclient: DHCPREQUEST of 10.170.2.113 on eth0 to 10.170.2.1 port 67
Jul 17 12:03:48 RDZUGW-SP003 dhclient: DHCPACK of 10.170.2.113 from 10.170.2.1
Jul 17 12:03:48 RDZUGW-SP003 dhclient: bound to 10.170.2.113 -- renewal in 33635 seconds.
Jul 17 12:17:01 RDZUGW-SP003 CRON[17491]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 13:17:01 RDZUGW-SP003 CRON[17952]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 14:17:01 RDZUGW-SP003 CRON[18381]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 15:17:01 RDZUGW-SP003 CRON[18841]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 16:17:01 RDZUGW-SP003 CRON[19319]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 17:17:01 RDZUGW-SP003 CRON[19748]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 18:17:01 RDZUGW-SP003 CRON[20208]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 19:17:01 RDZUGW-SP003 CRON[20668]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 20:17:01 RDZUGW-SP003 CRON[21129]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 21:17:01 RDZUGW-SP003 CRON[21558]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 21:24:23 RDZUGW-SP003 dhclient: DHCPREQUEST of 10.170.2.113 on eth0 to 10.170.2.1 port 67
Jul 17 21:24:23 RDZUGW-SP003 dhclient: DHCPACK of 10.170.2.113 from 10.170.2.1
Jul 17 21:24:23 RDZUGW-SP003 dhclient: bound to 10.170.2.113 -- renewal in 41902 seconds.
Jul 17 22:17:01 RDZUGW-SP003 CRON[22040]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 17 23:17:01 RDZUGW-SP003 CRON[22500]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 18 00:17:01 RDZUGW-SP003 CRON[22929]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 18 01:17:01 RDZUGW-SP003 CRON[23411]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 18 02:17:01 RDZUGW-SP003 CRON[23874]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 18 03:17:01 RDZUGW-SP003 CRON[24335]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 18 04:17:01 RDZUGW-SP003 CRON[24782]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 18 05:17:01 RDZUGW-SP003 CRON[25242]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 18 06:17:01 RDZUGW-SP003 CRON[25700]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 18 06:25:01 RDZUGW-SP003 CRON[25746]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Jul 18 07:17:01 RDZUGW-SP003 CRON[26129]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 18 07:30:01 RDZUGW-SP003 CRON[26243]: (root) CMD (start -q anacron || :)
Jul 18 07:30:01 RDZUGW-SP003 anacron[26246]: Anacron 2.3 started on 2011-07-18
Jul 18 07:30:01 RDZUGW-SP003 anacron[26246]: Will run job `cron.daily' in 5 min.
Jul 18 07:30:01 RDZUGW-SP003 anacron[26246]: Jobs will be executed sequentially
Jul 18 07:35:01 RDZUGW-SP003 anacron[26246]: Job `cron.daily' started
Jul 18 07:35:01 RDZUGW-SP003 anacron[26287]: Updated timestamp for job `cron.daily' to 2011-07-18
Jul 18 08:08:29 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Jul 18 08:08:29 RDZUGW-SP003 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Jul 18 08:08:29 RDZUGW-SP003 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jul 18 08:08:29 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Jul 18 08:08:29 RDZUGW-SP003 50mounted-tests: debug: /dev/sda5 is a swap partition; skipping
Jul 18 08:08:29 RDZUGW-SP003 os-prober: debug: os detected by /usr/lib/os-probes/50mounted-tests
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdb1
Jul 18 08:08:30 RDZUGW-SP003 10freedos: debug: /dev/sdb1 is not a FAT partition: exiting
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdb1
Jul 18 08:08:30 RDZUGW-SP003 10qnx: debug: /dev/sdb1 is not a QNX4 partition: exiting
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdb1
Jul 18 08:08:30 RDZUGW-SP003 macosx-prober: debug: /dev/sdb1 is not an HFS+ partition: exiting
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdb1
Jul 18 08:08:30 RDZUGW-SP003 20microsoft: debug: /dev/sdb1 is not a MS partition: exiting
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdb1
Jul 18 08:08:30 RDZUGW-SP003 30utility: debug: /dev/sdb1 is not a FAT partition: exiting
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdb1
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdb1
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdb1
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdb1
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdb1
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sdg1
Jul 18 08:08:30 RDZUGW-SP003 10freedos: debug: /dev/sdg1 is a FAT32 partition
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sdg1
Jul 18 08:08:30 RDZUGW-SP003 10qnx: debug: /dev/sdg1 is not a QNX4 partition: exiting
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sdg1
Jul 18 08:08:30 RDZUGW-SP003 macosx-prober: debug: /dev/sdg1 is not an HFS+ partition: exiting
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sdg1
Jul 18 08:08:30 RDZUGW-SP003 20microsoft: debug: /dev/sdg1 is a FAT32 partition
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sdg1
Jul 18 08:08:30 RDZUGW-SP003 30utility: debug: /dev/sdg1 is a FAT32 partition
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sdg1
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sdg1
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sdg1
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sdg1
Jul 18 08:08:30 RDZUGW-SP003 os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sdg1
Jul 18 08:08:30 RDZUGW-SP003 dkms_autoinstaller: vboxhost (4.0.2): Installing module on kernel 2.6.32-33-generic.
Jul 18 08:09:09 RDZUGW-SP003 dkms_autoinstaller: nvidia-current (195.36.24): Installing module on kernel 2.6.32-33-generic.
Jul 18 08:09:44 RDZUGW-SP003 AptDaemon: INFO: Initializing daemon
Jul 18 08:11:15 RDZUGW-SP003 pulseaudio[2026]: ratelimit.c: 323 events suppressed
Jul 18 08:11:23 RDZUGW-SP003 kernel: [2910423.245747] device eth0 left promiscuous mode
Jul 18 08:11:24 RDZUGW-SP003 kernel: [2910423.519952] usb 2-1.6: reset low speed USB device using ehci_hcd and address 15
Jul 18 08:11:49 RDZUGW-SP003 init: tty4 main process (1340) killed by TERM signal
```

Xorg.0.log

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux RDZUGW-SP003 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-32-generic root=UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 ro quiet splash
Build Date: 08 March 2011  08:22:34AM
xorg-server 2:1.7.6-2ubuntu7.6 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 14 14:26:33 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0a20:19da:1132 nVidia Corporation GT216 [GeForce GT 220] rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf2000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/524288
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 19:52:00 PDT 2010
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 19:18:54 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) Jun 14 14:26:34 NVIDIA(0): Enabling RENDER acceleration
(II) Jun 14 14:26:34 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Jun 14 14:26:34 NVIDIA(0):     enabled.
(II) Jun 14 14:26:36 NVIDIA(0): NVIDIA GPU GeForce GT 220 (GT216) at PCI:1:0:0 (GPU-0)
(--) Jun 14 14:26:36 NVIDIA(0): Memory: 1048576 kBytes
(--) Jun 14 14:26:36 NVIDIA(0): VideoBIOS: 70.16.28.00.00
(II) Jun 14 14:26:36 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Jun 14 14:26:36 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Jun 14 14:26:36 NVIDIA(0): Connected display device(s) on GeForce GT 220 at PCI:1:0:0:
(--) Jun 14 14:26:36 NVIDIA(0):     ACI VW246 (DFP-0)
(--) Jun 14 14:26:36 NVIDIA(0): ACI VW246 (DFP-0): 330.0 MHz maximum pixel clock
(--) Jun 14 14:26:36 NVIDIA(0): ACI VW246 (DFP-0): Internal Dual Link TMDS
(II) Jun 14 14:26:36 NVIDIA(0): Assigned Display Device: DFP-0
(==) Jun 14 14:26:36 NVIDIA(0): 
(==) Jun 14 14:26:36 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Jun 14 14:26:36 NVIDIA(0):     will be used as the requested mode.
(==) Jun 14 14:26:36 NVIDIA(0): 
(II) Jun 14 14:26:36 NVIDIA(0): Validated modes:
(II) Jun 14 14:26:36 NVIDIA(0):     "nvidia-auto-select"
(II) Jun 14 14:26:36 NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) Jun 14 14:26:36 NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
(--) Jun 14 14:26:36 NVIDIA(0):     option
(==) Jun 14 14:26:36 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Jun 14 14:26:36 NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
(II) Jun 14 14:26:36 NVIDIA(0): Initialized GPU GART.
(II) Jun 14 14:26:36 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Jun 14 14:26:36 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Jun 14 14:26:36 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(==) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ch"
(**) Option "xkb_variant" "de_nodeadkeys"
(II) XKB: reuse xkmfile /var/lib/xkb/server-F924D37780F51C7D73983061B02A58BFD335116F.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ch"
(**) Option "xkb_variant" "de_nodeadkeys"
(II) config/udev: Adding input device Fujitsu Siemens Computers GmbH FSC KB USB (/dev/input/event3)
(**) Fujitsu Siemens Computers GmbH FSC KB USB: Applying InputClass "evdev keyboard catchall"
(**) Fujitsu Siemens Computers GmbH FSC KB USB: always reports core events
(**) Fujitsu Siemens Computers GmbH FSC KB USB: Device: "/dev/input/event3"
(II) Fujitsu Siemens Computers GmbH FSC KB USB: Found keys
(II) Fujitsu Siemens Computers GmbH FSC KB USB: Configuring as keyboard
(II) XINPUT: Adding extended input device "Fujitsu Siemens Computers GmbH FSC KB USB" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ch"
(**) Option "xkb_variant" "de_nodeadkeys"
(II) config/udev: Adding input device Fujitsu Siemens Computers GmbH FSC KB USB (/dev/input/event4)
(**) Fujitsu Siemens Computers GmbH FSC KB USB: Applying InputClass "evdev keyboard catchall"
(**) Fujitsu Siemens Computers GmbH FSC KB USB: always reports core events
(**) Fujitsu Siemens Computers GmbH FSC KB USB: Device: "/dev/input/event4"
(II) Fujitsu Siemens Computers GmbH FSC KB USB: Found keys
(II) Fujitsu Siemens Computers GmbH FSC KB USB: Configuring as keyboard
(II) XINPUT: Adding extended input device "Fujitsu Siemens Computers GmbH FSC KB USB" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "ch"
(**) Option "xkb_variant" "de_nodeadkeys"
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event5)
(**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event5"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Found relative axes
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Jun 28 07:57:19 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Power Button: Device reopened after 1 attempts.
(II) Power Button: Device reopened after 1 attempts.
(II) Fujitsu Siemens Computers GmbH FSC KB USB: Device reopened after 1 attempts.
(II) Fujitsu Siemens Computers GmbH FSC KB USB: Device reopened after 1 attempts.
(II) Logitech USB Optical Mouse: Device reopened after 1 attempts.
(II) Macintosh mouse button emulation: Device reopened after 1 attempts.
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-CCC6AA6FE777F5854801F7A53E354259EBA58EC0.xkm
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Fujitsu Siemens Computers GmbH FSC KB USB: Close
(II) UnloadModule: "evdev"
(II) Fujitsu Siemens Computers GmbH FSC KB USB: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```

and boot.log

```
fsck from util-linux-ng 2.17.2

/dev/sda1: clean, 374255/12214272 files, 3216368/48827904 blocks

init: ureadahead-other main process (872) terminated with status 4


 * Starting AppArmor profiles       [80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox


[74G[ OK ]

 * Setting sensors limits       [80G 
[74G[ OK ]
```

---

### Post by lmarmisa on 2011-07-18
I have found a couple of references related to your problem:

[http://tech--help.blogspot.com/2009/12/ubuntu-solved-ureadahead-other-main.html](http://tech--help.blogspot.com/2009/12/ubuntu-solved-ureadahead-other-main.html)

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677)

I propose some commands that could help.

Re-boot the system into an Ubuntu Live CD and type these commands for repairing your two EXT4 partitions:

```

sudo fsck -f /dev/sda1
sudo fsck -f /dev/sdb1

```

The first link propose to comment the manual entries of the file fstab. At least one of the users of the second link was able to fix this problem with this procedure:

```

sudo mount /dev/sda1 /mnt
sudo gedit /mnt/etc/fstab

```

Add a char # to the line marked in blue:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fa50dc45-3ae0-40a8-85f4-4610e9dabe30 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ba7c825d-3836-48d9-95bf-6bad5f4066d6 none            swap    sw              0       0

# DEV/SDB1
[COLOR="Blue"]#/dev/sdb1	/media/DataDisk	ext4	defaults,errors=remount-ro	0	0[/COLOR]

```

Save & Quit.

Continue with:

```

sudo gedit /mnt/etc/default/grub

```

And add a char # to the line:

```

[COLOR="blue"]# GRUB_HIDDEN_TIMEOUT=0[/COLOR]

```

Save & Quit.

Type these commands:

```

for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
update-grub
exit

```

Finally reboot the system normally.

---

### Post by lmarmisa on 2011-07-18
An additional comment.

According to the results of Boot Info Script there is a blank line in the file **fstab**. I have recommended to edit that file for adding a comment to the partition /dev/sdb1. Please, check if this blank line really exists and, if so, remove it.

---

### Post by benneton on 2011-07-27
It's some kind of bug in kernel in last update. (2.6.32-33)

Solution (for me):

1. Boot using 2.6.32-33 kernel by pressing ESC (this will skip BUSYBOX - because of UUID block device identification problem) or while in BUSYBOX type "exit" and press ENTER to continue loading Ubuntu

2. Go to System ->  Administration -> Synaptic Package Manager
3. Remove linux-image-2.6.32-33-generic (it will remove linux-generic & linux-image-generic - click "Mark" and "Apply")
4. Click on linux-image-2.6.32-**32**-generic and then Right click -> Mark for Reinstallation
(it'll install previous version of linux-image and it will automatically setup GRUB)
5. Apply
6. Click on linux-image-2.6.32-32-generic and then click Package -> Lock Version
(it will lock this version of kernel)

Hope this helps!

Regards

---

### Post by lsaffre on 2011-07-29
> **benneton said:**
> It's some kind of bug in kernel in last update. (2.6.32-33)

Solution (for me):

1. Boot using 2.6.32-33 kernel by pressing ESC (this will skip BUSYBOX - because of UUID block device identification problem) or while in BUSYBOX type "exit" and press ENTER to continue loading Ubuntu

2. Go to System ->  Administration -> Synaptic Package Manager
3. Remove linux-image-2.6.32-33-generic (it will remove linux-generic & linux-image-generic - click "Mark" and "Apply")
4. Click on linux-image-2.6.32-**32**-generic and then Right click -> Mark for Reinstallation
(it'll install previous version of linux-image and it will automatically setup GRUB)
5. Apply
6. Click on linux-image-2.6.32-32-generic and then click Package -> Lock Version
(it will lock this version of kernel)

Hope this helps!

Regards

Thanks for your post, benneton. I had the same problem. On a HPHP Compaq Presario CQ61 laptop. My temporary solution was to uncomment the ``GRUB_HIDDEN_TIMEOUT=0`` line in `/etc/default/grub` and now selecting manually the 3rd menu option (2.6.32-32) on each boot. Is that a known bug? Should I report my problem somewhere?

---

### Post by benneton on 2011-07-30
It's my pleasure, lsaffre...

Maybe it's already reported?
I will try next version of kernel. It will be issued very soon.

Regards,

Benneton

---

### Post by SteDolphin on 2011-08-03
Thanks a lot for all the answers.

In the mean time I had to install new Ubuntu, as unfortunately I was not able to wait for your answers :( (which are anyway really appreciated)

Don't know what happened, but after new installation, I was able to upgrade to the latest kernel 2.6.32.33 without any problem ...

So I really don't know what to say :(

Steve

@lmarmisa blank lines in fstab does not create any problem.

---

### Post by YannBuntu on 2011-08-04
**@lmarmisa :** for your reference, [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") v3 does in 1 clic ( :guitar: ) all that you recommended :
- GRUB reinstall by chroot method
- unhide GRUB menu  (comment GRUB_HIDDEN_TIMEOUT ...)
- repair filesystem

Much easier for beginners ;)

---

