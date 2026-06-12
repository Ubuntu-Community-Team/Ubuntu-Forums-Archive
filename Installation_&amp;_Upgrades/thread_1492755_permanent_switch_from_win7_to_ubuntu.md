---
title: "permanent switch from win7 to ubuntu"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by Metrop021 on 2010-05-25
So i installed the new ubuntu on my system as a side by side installation, i've been using it for about 2 weeks now. ported over or found linux equivalents of any applications and games i use onto my ubuntu partition, and now i've decided i want to have ubuntu use the entire drive and just delete windows! The problem is, i'm not sure if i can do that... I shrank my windows partition half a gig and booted lupu (the ubuntu partitioner wasn't even showing this half a gig of free space) to see if i could just extend my linux partition (in the case that this did work, i was just planning on deleting my windows partition and just extending my linux to the full size of my drive). I really want to avoid a full reformat of the drive because i have customized my ubuntu a decent bit and i don't want to have to redo all of that (not to mention the data, but i could always back that up on an external hdd).

Here is a screenie of gparted:
[img]http://img42.imageshack.us/img42/9927/puppyscreenie.png[/img]
i don't really know too much about partitioning...
so is there any way to remove windows and give linux the rest of the drive without having to completely reinstall ubuntu?

also: this is 64 bit ubuntu and the win7 is 32 bit. that shouldn't matter but i feel it's worth mentioning

---

### Post by ronparent on 2010-05-25
If you intend to leave Ubuntu as the only OS on the drive, the solution can be fairly simple. 

1) Working from the live CD (you can't easily manipulate mounted partitions if booted to your installed system) use gparted to cut and paste your installed ext4 system from the extented partition to the front of the unallocated space. This effectively moves your entire install including its uuid to a primary partition.

2) Do the same for the swap.

3) Delete the empty extended space.

4) move the swap too the end of the unallocated space.

5) You can resize your ext4 to as big as you want to make it even to occupy all of the remaing unallocated space.

Keep something in mind. You would now have only two primary partitions on the drive devoted to Ubuntu. If in the future you would want to reinstall windows, create a separate /home, or any combination of partitions for any reason, the system will not let you create more than four primary partitions in total, One of those can be an extemded partition within which can exist several separate extended partitions. Windows always should be installed in a primary partition. Ubuntu and any related partitions such as swap and possibly /home etc. can function perfectly well within an extended partition. Although, for simplicty sake, it would make little sense to keep the entirety of your system within an extended partition, if you have more complex plans it would be perfectly reasonable. If your future plans are uncertain you could certainly expand your extended partition into the unallocated space formerly occupied by win7, and then expand your OS ext4 to fill that space.

Only you can know what you envision the future of you system. I'm sure you have enough to think about now. If you need mere help just post here. :)

---

### Post by Metrop021 on 2010-05-25
all right so i went ahead and did what you said, removed windows, copied the linux partition over, but i couldn't copy over the linux-swap partition (it was locked for some reason). i figured it didn't really matter too much, thought i could just use lupus grub installer to install grub to the mbr then everything should be peachy. but that doesnt seem to be the case. whenever i try any of the options on the installed grub i get a 'File not found' error. i've been fidling with it for a bit now but i'm not really getting anywhere. i've had major headaches given to me before by grub and i really wanna avoid another migrane. any idea on the best way to go about fixing this using the live cd?

---

### Post by darkod on 2010-05-25
> **Metrop021 said:**
> all right so i went ahead and did what you said, removed windows, copied the linux partition over, but i couldn't copy over the linux-swap partition (it was locked for some reason). i figured it didn't really matter too much, thought i could just use lupus grub installer to install grub to the mbr then everything should be peachy. but that doesnt seem to be the case. whenever i try any of the options on the installed grub i get a 'File not found' error. i've been fidling with it for a bit now but i'm not really getting anywhere. i've had major headaches given to me before by grub and i really wanna avoid another migrane. any idea on the best way to go about fixing this using the live cd?

Run the boot info script so we can see the current setup:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

When trying to expand and move partitions around you have to be prepared for some hiccups. You could have left alone the root partition and just format the space that win7 was taking as a data partition or similar.

---

### Post by Metrop021 on 2010-05-25
Done
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 288063 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    68,308,379    68,308,317  83 Linux
/dev/sda2         553,818,110   625,141,759    71,323,650   5 Extended
/dev/sda5         553,818,112   622,117,124    68,299,013  83 Linux
/dev/sda6         622,120,960   625,141,759     3,020,800  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b   ext4                                     
/dev/sda6        a4cc3f9a-790f-44b6-8cd4-22a60f5dcd1c   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/menu.lst: ===========================

# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Tue May 25 13:13:56 2010
#
# The backup copy of the MBR for drive '/dev/sda' is
# here '/boot/grub/mbr.sda.13021'.  You can restore it like this.
# dd if=/boot/grub/mbr.sda.13021 of=/dev/sda bs=512 count=1
#
# Start GRUB global section
#timeout 30
color light-gray/blue black/light-gray
# End GRUB global section
# Linux bootable partition config begins
  title Linux (on /dev/sda1)
  root (hd0,0)
  kernel /boot/vmlinuz root=/dev/sda1 ro vga=normal
# Linux bootable partition config ends
# Linux bootable partition config begins
  title Linux (on /dev/sda5)
  root (hd0,4)
  kernel /boot/vmlinuz root=/dev/sda5 ro vga=normal
# Linux bootable partition config ends
# Linux bootable initrd config begins
  title Linux initrd /tmp/boot/boot/initrd.img-2.6.32-22-generic (on /dev/sda1)
  root (hd0,0)
  kernel /boot/vmlinuz root=/dev/sda1 ramdisk_size=23572 root=/dev/ram0 rw
  initrd /tmp/boot/boot/initrd.img-2.6.32-22-generic
# Linux bootable initrd config ends
title Install GRUB to floppy disk (on /dev/fd0)
pause Insert a formatted floppy disk and press enter.
root (hd0,0)
setup (fd0)
pause Press enter to continue.
title Install GRUB to Linux partition (on /dev/sda1)
root (hd0,0)
setup (hd0,0)
pause Press enter to continue.
title -     For help press 'c', then type: 'help'
root (hd0)
title -     For usage examples, type: 'cat /boot/grub/usage.txt'
root (hd0)

=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
set locale_dir=($root)/boot/grub/locale
set lang=fr
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
menuentry 'Ubuntu, avec Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-22-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
    echo    'Chargement de Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b ro single 
    echo    'Chargement du disque mémoire initial...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-21-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
    echo    'Chargement de Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b ro single 
    echo    'Chargement du disque mémoire initial...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c250a35450a34dcb
    chainloader +1
}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a4cc3f9a-790f-44b6-8cd4-22a60f5dcd1c none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.5GB: boot/grub/core.img
  22.1GB: boot/grub/grub.cfg
   6.5GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
   6.7GB: boot/initrd.img-2.6.32-21-generic
   6.7GB: boot/initrd.img-2.6.32-22-generic
   6.5GB: boot/vmlinuz-2.6.32-21-generic
    .6GB: boot/vmlinuz-2.6.32-22-generic
   6.7GB: initrd.img
   6.7GB: initrd.img.old
    .6GB: vmlinuz
   6.5GB: vmlinuz.old

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
set locale_dir=($root)/boot/grub/locale
set lang=fr
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
menuentry 'Ubuntu, avec Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-22-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
    echo    'Chargement de Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b ro single 
    echo    'Chargement du disque mémoire initial...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, avec Linux 2.6.32-21-generic (mode de récupération)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
    echo    'Chargement de Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b ro single 
    echo    'Chargement du disque mémoire initial...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set c250a35450a34dcb
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=cb12ee7b-b66b-4174-ba1c-29eee2cc8b7b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a4cc3f9a-790f-44b6-8cd4-22a60f5dcd1c none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 290.1GB: boot/grub/core.img
 305.6GB: boot/grub/grub.cfg
 290.2GB: boot/initrd.img-2.6.32-21-generic
 290.2GB: boot/initrd.img-2.6.32-22-generic
 290.1GB: boot/vmlinuz-2.6.32-21-generic
 284.1GB: boot/vmlinuz-2.6.32-22-generic
 290.2GB: initrd.img
 290.2GB: initrd.img.old
 284.1GB: vmlinuz
 290.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  1d 83 f9 04 74 18 83 f9  09 74 13 6a 01 52 68 0d  |....t....t.j.Rh.|
00000010  00 00 c0 68 a8 15 4f 89  52 e8 b0 aa fa ff 50 e8  |...h..O.R.....P.|
00000020  97 e2 fa ff 5d c2 0c 00  90 90 90 90 90 8b ff 55  |....]..........U|
00000030  8b ec 56 ff 75 08 e8 21  fd f4 ff 8b f0 33 d2 3b  |..V.u..!.....3.;|
00000040  f2 75 60 8b 45 10 8b 40  30 3b c2 74 41 39 50 2c  |.u`.E..@0;.tA9P,|
00000050  74 3c 8b 48 28 83 f9 02  74 0a 83 f9 04 74 05 83  |t<.H(...t....t..|
00000060  f9 09 75 2a 50 39 55 08  75 12 e8 28 f8 03 00 85  |..u*P9U.u..(....|
00000070  c0 74 30 6a 01 e8 40 03  04 00 eb 25 e8 16 f8 03  |.t0j..@....%....|
00000080  00 85 c0 74 1e 6a 01 e8  f8 fe 03 00 eb 15 6a 01  |...t.j........j.|
00000090  52 68 0d 00 00 c0 68 d8  15 4f 89 52 e8 2d aa fa  |Rh....h..O.R.-..|
000000a0  ff 8b f0 56 e8 12 e2 fa  ff 5e 5d c2 0c 00 90 90  |...V.....^].....|
000000b0  90 90 90 8b ff 55 8b ec  ff 75 08 e8 9c fc f4 ff  |.....U...u......|
000000c0  33 d2 3b c2 75 34 8b 4d  10 8b 49 30 3b ca 74 17  |3.;.u4.M..I0;.t.|
000000d0  39 51 2c 74 12 8b 49 28  83 f9 02 74 1d 83 f9 04  |9Q,t..I(...t....|
000000e0  74 18 83 f9 09 74 13 6a  01 52 68 0d 00 00 c0 68  |t....t.j.Rh....h|
000000f0  08 16 4f 89 52 e8 d4 a9  fa ff 50 e8 bb e1 fa ff  |..O.R.....P.....|
00000100  5d c2 0c 00 90 90 90 90  90 8b ff 55 8b ec 8b 45  |]..........U...E|
00000110  08 6a 04 83 c0 78 50 e8  46 3c fa ff 84 c0 74 0c  |.j...xP.F<....t.|
00000120  33 c9 b8 78 8d 50 89 41  f0 0f c1 08 5d c2 04 00  |3..x.P.A....]...|
00000130  90 90 90 90 90 8b ff 55  8b ec 51 56 8b 75 08 8b  |.......U..QV.u..|
00000140  06 89 45 08 8d 45 fc 50  e8 f9 cd 03 00 8d 45 08  |..E..E.P......E.|
00000150  50 e8 97 d3 03 00 83 26  00 8d 45 fc 50 e8 20 ce  |P......&..E.P. .|
00000160  03 00 5e c9 c2 04 00 90  90 90 90 90 8b ff 55 8b  |..^...........U.|
00000170  ec ff 75 10 8b 45 08 6a  24 ff 70 08 ff 70 04 ff  |..u..E.j$.p..p..|
00000180  75 0c e8 53 18 f8 ff 5d  c2 0c 00 90 90 90 90 90  |u..S...]........|
00000190  8b ff 55 8b ec 8b 45 08  48 ff 75 10 ff 75 0c 74  |..U...E.H.u..u.t|
000001a0  13 83 e8 05 74 07 e8 d8  c1 03 00 eb 0c e8 f1 c1  |....t...........|
000001b0  03 00 eb 05 e8 0a c2 03  00 8b 4d 14 89 01 00 fe  |..........M.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 05 29 12 04 00 fe  |...........)....|
000001d0  ff ff 05 fe ff ff 07 29  12 04 fb 26 2e 00 00 00  |.......)...&....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

And yeah i know :(, i was just hoping that it wouldn't have any hiccups. it's not a big deal though really, my last resort is just gonna be to backup my data onto an external then do a clean full install.

---

### Post by darkod on 2010-05-25
Look carefully in the results.
First of all, it now seems you have two ubuntu installs, on sda1 and sda5. Not sure whether that is because you tried to move the partition, I guess.
Second, what is really puzzling me, you have grub1 installed on the MBR and also grub1 files in sda1. You said this was a new install (not upgrade), and 10.04 comes with grub2. So what are those grub1 files and grub1 on the MBR doing there? Did you try some grub recovery procedures but you used older cd version and commands for grub1?

Anyway, lets try to get any of those ubuntus booting. Get your 10.04 cd, boot into live mode, and do:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

It might still show menu with option for win7 but don't worry, that's because it's not updated yet. If you can boot into your sda5 ubuntu, run:

sudo update-grub

Then look around whether all your files are there, and whether everything is working fine.

In fact, when running update-grub it might detect the 'other' ubuntu on sda1 and create an entry for it in the menu. If it does, after making sure the sda5 ubuntu is working fine, try to boot the sda1 ubuntu and see what comes up.

---

### Post by Metrop021 on 2010-05-25
> **darkod said:**
> Look carefully in the results.
First of all, it now seems you have two ubuntu installs, on sda1 and sda5. Not sure whether that is because you tried to move the partition, I guess.
Second, what is really puzzling me, you have grub1 installed on the MBR and also grub1 files in sda1. You said this was a new install (not upgrade), and 10.04 comes with grub2. So what are those grub1 files and grub1 on the MBR doing there? Did you try some grub recovery procedures but you used older cd version and commands for grub1?

Anyway, lets try to get any of those ubuntus booting. Get your 10.04 cd, boot into live mode, and do:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

It might still show menu with option for win7 but don't worry, that's because it's not updated yet. If you can boot into your sda5 ubuntu, run:

sudo update-grub

Then look around whether all your files are there, and whether everything is working fine.

In fact, when running update-grub it might detect the 'other' ubuntu on sda1 and create an entry for it in the menu. If it does, after making sure the sda5 ubuntu is working fine, try to boot the sda1 ubuntu and see what comes up.
Yeah, the reason that theres an older grub version on there is because i used a different linux distro boot disk to try to reinstal grub, so it musta used an older version. And the 2 ubuntus are sda5 the original leftover from the side by side install, and sda1 is the one i just recently copied into the space where my win7 used to be.

i ran those terminal commands and rebooted and success! i was able to boot into my sda5 ubuntu partition, everything appeared to be in order so i just repeated the commands for sda1 instead (the partition i'd like to keep) rebooted and i'm able to boot into sda1! so i went ahead and wiped out sda5. and using gparted i grew my sda1 partition to take up the entire drive. rebooted, and then set the timeout to 0 so that i could instantly boot, then ran update-grub again. and everything is working just fine. :)

headache avoided, thanks for the help!!!!

---

### Post by ronparent on 2010-05-25
Going back to your original post, gparted did not show any windows partition on the drive. You had apparently deleted it already at that point. Apparently you did get your install copied to the now vacant space for a primary partition. Swap didn't copy because it was n use and had to be disabled in gparted to copy it. No big deal because it is basically empty and a new swap can be established. You didn't do a cut and paste however and the original partition with the complete install still remains in the extended partition, You should delete that because both partitions have the same uuid and grub will have trouble finding the right one. To follow through in the direction you chose to go, you need to get your grub swuared away so that grub2 is installed on **sda1** as described by darkrod.

---

### Post by ronparent on 2010-05-25
I see my post occured after you had thought through and solved the problem. Congratulations and good work.

---

