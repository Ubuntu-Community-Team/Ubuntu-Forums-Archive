---
title: "Fresh 10.04 install can't boot"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by jasonabarnett on 2010-05-17
Dear All,

I've trawled the forums looking for an answer but nothing quite matches my situation.

I have a spare Dell laptop with a 250GB disk that was running Windows 7 (slowly).  I've installed 10.04 a-fresh on this machine and selected the entire disk and allowed the installer to configure the partitioning as it sees fit.

The install runs through and says it has worked and asks for a reboot.  Once the machine shuts down and pops the CD I get a stack of sector read errors and the machine just sits there.  I hold the power button down for a cold boot and when the machine starts up I get "error: out of disk" and the a grub rescue prompt.

As this is a fresh install and I'm not dual booting or anything fancy I'm very surprised by this.

The Live CD boots normally and detects all my hardware beautifully and I really want to let Unbuntu into my life but this sort of initial problem just makes things frustrating!

All advice is appreciated.

Regards,

Jason

---

### Post by MichealH on 2010-05-17
At the menu select the option "Check Disk for Defects"

---

### Post by jasonabarnett on 2010-05-17
Hi MichaelH,

Thank you for the reply.

To which menu are you referring?  I don't get anything between POST and the grub rescue prompt....


I've used Linux on and off for a few years, and I've support UNIX servers for years so I'm very frustrated by this as 10.04 is making me feel like a newbie!

Cheers,

JB

---

### Post by wilee-nilee on 2010-05-17
Post this boot script in code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

To post in code tags, just highlight the text in the reply window hit the # in the reply panel then submit reply.

---

### Post by MichealH on 2010-05-17
> **jasonabarnett said:**
> Hi MichaelH,

Thank you for the reply.

To which menu are you referring?  I don't get anything between POST and the grub rescue prompt....


I've used Linux on and off for a few years, and I've support UNIX servers for years so I'm very frustrated by this as 10.04 is making me feel like a newbie!

Cheers,

JB

The CD Boot menu? It should be on!

(Oh and I will be away for a few hours)

---

### Post by jasonabarnett on 2010-05-17
Hi MichealH,

Unfortunately I don't get any such option.  I boot to a menu offering me to try LiveCD or install 10.04.  If I proceed with either option I don't get any diagnostic options.

Hi wilee-nilee,

I'll try your suggestion now and post the results shortly.

Appreciate all the help.

Jason

---

### Post by jasonabarnett on 2010-05-17
Output of bootinfo script:

                                                                     
                                                                     
                                                                     
                                             
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   476,319,743   476,317,696  83 Linux
/dev/sda2         476,321,790   488,396,799    12,075,010   5 Extended
/dev/sda5         476,321,792   488,396,799    12,075,008  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        587d4479-b53d-4856-aec0-4ffa8c438a3c   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        da2531c1-6fdc-4ae1-b553-a64fa83ef05f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 587d4479-b53d-4856-aec0-4ffa8c438a3c
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
search --no-floppy --fs-uuid --set 587d4479-b53d-4856-aec0-4ffa8c438a3c
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 587d4479-b53d-4856-aec0-4ffa8c438a3c
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=587d4479-b53d-4856-aec0-4ffa8c438a3c ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 587d4479-b53d-4856-aec0-4ffa8c438a3c
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=587d4479-b53d-4856-aec0-4ffa8c438a3c ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 587d4479-b53d-4856-aec0-4ffa8c438a3c
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 587d4479-b53d-4856-aec0-4ffa8c438a3c
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=da2531c1-6fdc-4ae1-b553-a64fa83ef05f none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 240.6GB: boot/grub/core.img
  98.9GB: boot/grub/grub.cfg
 240.6GB: boot/initrd.img-2.6.32-21-generic
 240.6GB: boot/vmlinuz-2.6.32-21-generic
 240.6GB: initrd.img
 240.6GB: vmlinuz

---

### Post by wilee-nilee on 2010-05-17
I reposted it in code tags as it is close to impossible to read otherwise.
```
Boot Info Script 0.55 dated February 15th, 2010

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
partition #1 for /boot/grub.

sda1: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info:
Operating System: Ubuntu 10.04 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: -
Boot sector info:

sda5: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 2,048 476,319,743 476,317,696 83 Linux
/dev/sda2 476,321,790 488,396,799 12,075,010 5 Extended
/dev/sda5 476,321,792 488,396,799 12,075,008 82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL

/dev/loop0 squashfs
/dev/sda1 587d4479-b53d-4856-aec0-4ffa8c438a3c ext4
/dev/sda2: PTTYPE="dos"
/dev/sda5 da2531c1-6fdc-4ae1-b553-a64fa83ef05f swap
/dev/sda: PTTYPE="dos"

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

aufs / aufs (rw)
/dev/sr0 /cdrom iso9660 (ro,noatime)
/dev/loop0 /rofs squashfs (ro,noatime)


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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 587d4479-b53d-4856-aec0-4ffa8c438a3c
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
search --no-floppy --fs-uuid --set 587d4479-b53d-4856-aec0-4ffa8c438a3c
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 587d4479-b53d-4856-aec0-4ffa8c438a3c
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=587d4479-b53d-4856-aec0-4ffa8c438a3c ro quiet splash
initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 587d4479-b53d-4856-aec0-4ffa8c438a3c
echo 'Loading Linux 2.6.32-21-generic ...'
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=587d4479-b53d-4856-aec0-4ffa8c438a3c ro single
echo 'Loading initial ramdisk ...'
initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 587d4479-b53d-4856-aec0-4ffa8c438a3c
linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 587d4479-b53d-4856-aec0-4ffa8c438a3c
linux16 /boot/memtest86+.bin console=ttyS0,115200n8
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
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
/dev/sda1 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=da2531c1-6fdc-4ae1-b553-a64fa83ef05f none swap sw 0 0

=================== sda1: Location of files loaded by Grub: ===================


240.6GB: boot/grub/core.img
98.9GB: boot/grub/grub.cfg
240.6GB: boot/initrd.img-2.6.32-21-generic
240.6GB: boot/vmlinuz-2.6.32-21-generic
240.6GB: initrd.img
240.6GB: vmlinuz
```

---

### Post by jasonabarnett on 2010-05-17
Whilst I wait to see what develops I'm re-installing 10.04 with a custom partition scheme:

8GB swap at the start of the disk
80GB primary JFS partition - /
rest of disk primary JFS partition - /home

I don't have any great hope but it beats doing nothing.

Right, it's installed and I get a load of I/O errors from sr0 when the CD ejects.  Not very neat but that's life sometimes.

Cold boot and fingers crossed.....

Back of the net!  No errors, machine is booting straight into the GUI.

I did wonder if the partition size was causing the issue....

Any recommendations on partitioning?  Is JFS better than EXT4 etc.?

JB

---

### Post by jasonabarnett on 2010-05-17
> **wilee-nilee said:**
> I reposted it in code tags as it is close to impossible to read otherwise.


Sorry wilee-nilee, my bad.  I didn't read your post properly.

Doh.

Anyway I have a system up and running so I'm feeling pretty dapper about life.

---

### Post by wilee-nilee on 2010-05-17
> **jasonabarnett said:**
> Whilst I wait to see what develops I'm re-installing 10.04 with a custom partition scheme:

8GB swap at the start of the disk
80GB primary JFS partition - /
rest of disk primary JFS partition - /home

I don't have any great hope but it beats doing nothing.

Right, it's installed and I get a load of I/O errors from sr0 when the CD ejects.  Not very neat but that's life sometimes.

Cold boot and fingers crossed.....

Back of the net!  No errors, machine is booting straight into the GUI.

I did wonder if the partition size was causing the issue....

Any recommendations on partitioning?  Is JFS better than EXT4 etc.?

JB

It sounds like it's working is this correct? you don't really need that much swap, usually swap is equal to the amount of ram that you have or a little more. Ext4 runs fine on all of my machines, I suspect that the ISO is corrupted. AS far as I can tell the boot script looked as it should, but I don't understand every line. If it is working I would't worry about the swap.

---

### Post by jasonabarnett on 2010-05-17
Hi wilee-nilee,

Yes it's working and it's bloomin' fast for a five year old machine.

I'll leave my partitions as they are.  I've got lots of disk space so too much swap won't kill me.

Thanks for taking the time to help.

Jason

---

