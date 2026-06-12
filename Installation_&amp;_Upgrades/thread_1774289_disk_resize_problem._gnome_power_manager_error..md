---
title: "disk resize problem. gnome power manager error."
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by vamunar on 2011-06-03
i have a problem that i cannot solve because i am a newbie to linux. i have had a satellite m70 toshiba laptop and i installed [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]linux [/FONT][/FONT][/COLOR][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]mint[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") 10 in it. i have used it for months and it was working great. until a few hours ago i decided to try out the new ubuntu 11.04.[COLOR=Lime]  i installed it to dualboot with linux mint 10. i resized the disk to  increase the disk for ubuntu but what i forgot is that linux has only 17  gb left before installation and that i partitioned ubuntu to  use 25 gb[/COLOR]. after playing around with ubuntu i decided to go  reboot and log in to mint. but when the log-in screen appeared this  error came out 
 
 [COLOR=Red]
" Installation problem! The configuration default for [[COLOR=blue][COLOR=blue !important][FONT=inherit !important][COLOR=blue !important][FONT=inherit !important]Gnome[/FONT][/FONT][/COLOR]]("http://www.linuxforums.org/forum/#")[/COLOR][[/COLOR]]("http://www.linuxforums.org/forum/#") Power Manager have not been installed correctly. Pls contact your computer administrator "[/COLOR]
 
i tried to log-in and it just showed a black screen and went back to the  log-in screen with the same message. it just comes back to the same  log-in screen everytime i try to log-in. PLS HELP ME. i have important  files in linux mint that i have to recover for my THESIS. pls help me  anyone. i need step by step procedure and line commands that i need to  type because i am not well-versed with it. thank you very much.

---

### Post by Hedgehog1 on 2011-06-03
We need to get a look at your install to get an idea what can be done.

Please boot off the Natty/11.04 LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

### Post by vamunar on 2011-06-03
> **Hedgehog1 said:**
> We need to get a look at your install to get an idea what can be done.

Please boot off the Natty/11.04 LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

Thank you for your reply Hedgehog1. I will do this now.

---

### Post by vamunar on 2011-06-03
attached are the results of the bootscript Hedgehog1

---

### Post by Hedgehog1 on 2011-06-03
Let me post the results so they are easier to read:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Linux Mint 10 Julia
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   259,846,903   259,844,856  83 Linux
/dev/sda2         259,848,190   312,580,095    52,731,906   5 Extended
/dev/sda5         309,512,192   312,580,095     3,067,904  82 Linux swap / Solaris
/dev/sda6         259,848,192   306,386,943    46,538,752  83 Linux
/dev/sda7         306,388,992   309,508,095     3,119,104  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        2d125df6-9538-40ef-9873-8ed476fa63e7   ext4       
/dev/sda5        a6a564b5-df91-42ea-8259-1f1e1630e9d2   swap       
/dev/sda6        a5512b7c-15d5-40c3-a9f0-0797537cbe8d   ext4       
/dev/sda7        2ecb5d7d-cbff-49b4-aefc-84ed89cdb6e4   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 2d125df6-9538-40ef-9873-8ed476fa63e7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 2d125df6-9538-40ef-9873-8ed476fa63e7
set locale_dir=($root)/boot/grub/locale
set lang=en
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

### BEGIN /etc/grub.d/06_mint_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 2d125df6-9538-40ef-9873-8ed476fa63e7
insmod png
if background_image /boot/grub/linuxmint.png ; then
  set color_normal=white/black
  set color_highlight=white/light-gray
else
  set menu_color_normal=white/black
  set menu_color_highlight=white/light-gray
fi
### END /etc/grub.d/06_mint_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sda1)' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2d125df6-9538-40ef-9873-8ed476fa63e7
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2d125df6-9538-40ef-9873-8ed476fa63e7 ro  splash quiet vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Linux Mint 10, 2.6.35-22-generic (/dev/sda1) -- recovery mode' --class linuxmint --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2d125df6-9538-40ef-9873-8ed476fa63e7
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2d125df6-9538-40ef-9873-8ed476fa63e7 ro single  splash quiet vga=773
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2d125df6-9538-40ef-9873-8ed476fa63e7
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 2d125df6-9538-40ef-9873-8ed476fa63e7
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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
UUID=2d125df6-9538-40ef-9873-8ed476fa63e7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a6a564b5-df91-42ea-8259-1f1e1630e9d2 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 116.135002136 = 124.699009024  boot/grub/core.img                             1
 122.363021851 = 131.386294272  boot/grub/grub.cfg                             1
  95.281696320 = 102.307942400  boot/initrd.img-2.6.35-22-generic              1
 123.901813507 = 133.038559232  boot/vmlinuz-2.6.35-22-generic                 1
   4.254978180 = 4.568748032    boot/vmlinuz-2.6.35-28-generic                 1
  95.281696320 = 102.307942400  initrd.img                                     1
 123.901813507 = 133.038559232  vmlinuz                                        1

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root a5512b7c-15d5-40c3-a9f0-0797537cbe8d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root a5512b7c-15d5-40c3-a9f0-0797537cbe8d
set locale_dir=($root)/boot/grub/locale
set lang=en_PH
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
if background_color 44,0,30; then
  clear
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a5512b7c-15d5-40c3-a9f0-0797537cbe8d
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a5512b7c-15d5-40c3-a9f0-0797537cbe8d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a5512b7c-15d5-40c3-a9f0-0797537cbe8d
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=a5512b7c-15d5-40c3-a9f0-0797537cbe8d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a5512b7c-15d5-40c3-a9f0-0797537cbe8d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root a5512b7c-15d5-40c3-a9f0-0797537cbe8d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda1) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 2d125df6-9538-40ef-9873-8ed476fa63e7
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=2d125df6-9538-40ef-9873-8ed476fa63e7 ro splash quiet vga=773 quiet splash
	initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Linux Mint 10, 2.6.35-22-generic (/dev/sda1) -- recovery mode (on /dev/sda1)" --class gnu-linux --class gnu --class os {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 2d125df6-9538-40ef-9873-8ed476fa63e7
	linux /boot/vmlinuz-2.6.35-22-generic root=UUID=2d125df6-9538-40ef-9873-8ed476fa63e7 ro single splash quiet vga=773
	initrd /boot/initrd.img-2.6.35-22-generic
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=a5512b7c-15d5-40c3-a9f0-0797537cbe8d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2ecb5d7d-cbff-49b4-aefc-84ed89cdb6e4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.049304962 = 150.376796160  boot/grub/core.img                             1
 132.036876678 = 141.773516800  boot/grub/grub.cfg                             1
 125.159404755 = 134.388887552  boot/initrd.img-2.6.38-8-generic               2
 140.047576904 = 150.374940672  boot/vmlinuz-2.6.38-8-generic                  1
 125.159404755 = 134.388887552  initrd.img                                     2
 140.047576904 = 150.374940672  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

**EDIT:** For other readers of the script output - be aware that this contains a mix of the Mint data from /dev/sda1 (sda1/boot/grub/grub.cfg) and data from the Ubuntu 11.04 /dev/sda6 partition (the fstab file).

---

### Post by Hedgehog1 on 2011-06-03
vamunar,

Are you able to mount and read the Mint partition /dev/sda1 from Ubuntu on the hard disk or Ubuntu on the LiveCD/LiveUSB?

If you can, you might want to copy your documents you need for your theses from the Mint partition to a USB stick or external drive just to be sure you have them safe somewhere.

Now let me see if I can figure out why this is misbehaving...

---

### Post by vamunar on 2011-06-03
omg i'm such a noob that i didn't know i can read the mint files from ubuntu LOL. i'm about to transfer them to a hard disk. YOU SAVED MY LIFE.

---

### Post by Hedgehog1 on 2011-06-03
Mint is based on Ubuntu; so many things are the same 'under the hood'.

You can use a Mint or Ubuntu LiveCD/LiveUSB to read data from a hard drive on a PC where Windows is crashed or infected; it reads FAT, FAT32 and NTFS partitions fine.


Once your data is safe, I believe you will want to return to running Mint as your primary OS.

Right now the Grub boot menu you are using is the one installed by Ubuntu 11.04, so if you choose to uninstall Ubuntu 11.04, you will need to update the Grub back to the version carried on Mint before you delete the Ubuntu 11.04 partitions.

Once your data is safely backed up, and we will attempt a rescue of Mint.

---

### Post by Hedgehog1 on 2011-06-03
This next step needs to be done from the Ubuntu 11.04 LiveCD/LiveUSB (remember that the Mint LiveCD/LiveUSB has an earlier version of grub).

So, once your data is safely backed up and your running from the Ubuntu 11.04 LiveCD/LiveUSB, in the terminal please do these two commands:

```
sudo mount /dev/sda6 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Once these are done, you can reboot and see if Mint will come up properly.  If it does boot up properly, you then only have to decide if you are keeping Ubuntu 11.04 on this system.

If it does not come up properly, then we move to the next logical step.


***The Hedge***

:KS

---

### Post by vamunar on 2011-06-03
Thanks Hedgehog1! I will transfer my files first and I will get back to you after executing the commands you have provided.

---

### Post by Hedgehog1 on 2011-06-03
vamunar,

I lost track of time; it is nearly 3:00 a.m. in the morning here in Portland and I need to go to bed.

Please post any issues/errors you might have, and hopefully other forum members in a time zone closer to yours can continue to help.

I will be back tomorrow.


***The Hedge***

:KS

---

### Post by vamunar on 2011-06-03
> **Hedgehog1 said:**
> This next step needs to be done from the Ubuntu 11.04 LiveCD/LiveUSB (remember that the Mint LiveCD/LiveUSB has an earlier version of grub).

So, once your data is safely backed up and your running from the Ubuntu 11.04 LiveCD/LiveUSB, in the terminal please do these two commands:

```
sudo mount /dev/sda6 /mnt
```

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Once these are done, you can reboot and see if Mint will come up properly.  If it does boot up properly, you then only have to decide if you are keeping Ubuntu 11.04 on this system.

If it does not come up properly, then we move to the next logical step.


***The Hedge***

:KS

i tried this code:

```
sudo mount /dev/sda6 /mnt
``` 

but this came out 

"mount: can't find /dev/sda6/mnt in /etc/fstab or /etc/mtab"

then i tried the code:

```
sudo grub-install --root-directory=/mnt /dev/sda
```

and this came out:

"/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it. This software may cause boot or other problems in the future. Please ask its authors not to store data in the boot track. Installation finished. No error reported."

that's about it. then i restarted and it doesn't get to choosing ubuntu or linux. "grub rescue>" comes out and i don't know what to do, nothing happens.

---

### Post by vamunar on 2011-06-03
hedgehog1, hope you can reply tomorrow. i am thinking about clearing the whole disk (since i have my important files) and installing ubuntu 11.04 alone or linux mint but i'll just wait for your opinion. i'll be back by 9:00 pm (philippines GMT +8). thank you for your help.

---

### Post by Hedgehog1 on 2011-06-03
Hi Again - just checking the this thread during a break.

The command you ran was missing a space:

"mount: can't find **/dev/sda6/mnt** in /etc/fstab or /etc/mtab"

sudo mount /dev/sda6 /mnt <- space between sda6 and /mnt.

However, I think a clean install of you OS of choice is you best plan of attack; you can:

* Reinstall mint 10
* download and install mint 11
* install Ubuntu 11.04

Now, I use and like Ubuntu 10.04 and Unity; but really the choice should be based on what Linux distribution you are most comfortable with.

Whichever of the 3 you choose to install, I would suggest a disk/partition layout like this:

/dev/sda1 ext4 '/' (root) 20 gigs
/dev/sda2 ext4 '/home' all spacw not used by root and swap
/dev/sda3 swap Size of ram + 10%

I will post a guide with pictures...

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-06-03
You can wipe the disk clean, and then begin your Ubuntu install by using gparted and do this:

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]

[IMG]http://img858.imageshack.us/img858/9979/mbrpariondemo03.png[/IMG]

**Then begin creating 3 partitions for '/' (root) '/home' & Swap:**

[IMG]http://img853.imageshack.us/img853/503/mbrpariondemo04.png[/IMG]

**Make your root partition 20-30 gigs**

[IMG]http://img7.imageshack.us/img7/2554/mbrpariondemo05.png[/IMG]

**Make your '/home' partition all the rest of the disk space except that you need for swap (swap = RAM size + 10%)**

[IMG]http://img851.imageshack.us/img851/2815/mbrpariondemo06.png[/IMG]

**Next your swap partition:**

[IMG]http://img132.imageshack.us/img132/8353/mbrpariondemo07.png[/IMG]

**Press the 'check mark' button to make the changes real:**

[IMG]http://img402.imageshack.us/img402/5460/mbrpariondemo08.png[/IMG]

---

### Post by Hedgehog1 on 2011-06-03
**gparted will ask this:**

[IMG]http://img826.imageshack.us/img826/7826/mbrpariondemo09.png[/IMG]

**Then it updates your partitions:**

[IMG]http://img101.imageshack.us/img101/5706/mbrpariondemo10.png[/IMG]

**You can see a list of the changes made once the work is done:**

[IMG]http://img862.imageshack.us/img862/7135/mbrpariondemo11.png[/IMG]

**And a view of what the partitions look like after the update:**

[IMG]http://img600.imageshack.us/img600/4516/mbrpariondemo12.png[/IMG]

**Same layout, but as seen using the Disk Utility:**

[IMG]http://img825.imageshack.us/img825/2018/mbrpariondemo13.png[/IMG]

Begin the install. When you get to the 'allocate disk space' screen:

If you are installing Natty/11.04, select the '**Something Else**' option.

If you are installing 10.04 or 10.10, select the '**Specify Partitions Manually (Advanced)**' option.

And tell the install to use the three partitions this way **(Your Drive is likely /dev/sda, not the /dev/sdc this screen shot was taken from)**:

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]

**Please install the boot loader in /dev/sda **(not sda1 or sda2, just /dev/sda)

***The Hedge***

---

### Post by vamunar on 2011-06-04
hey hedgehog1, i've installed ubuntu 11.04 alone. now i'm having a problem. i cannot connect to the internet (wired). it does not connect automatically. what happens is the "signal" symbol just loads then stops and a message comes out that say wired network disconnected something like that. i don't know why that comes out because it hasn't even connected.

then i go to "edit connections" and edit under the "wired" tab. device MAC address and Cloned MAC address is empty and MTU is in automatic. i tried 

```
ifconfig
```

and got the MAC address from eth0 HWaddr but i don't know what to put for Cloned MAC address. i left MTU as automatic. i still can't connect. i tried searching from other forums about the same problem but i can't find any. pls help me. ](*,)

---

### Post by Hedgehog1 on 2011-06-04
I just looked at my setup for "Auto eth0".

I have my cards mac address populated, the cloned mac address empty and MTU set to automatic.

In my case I have a router that does DHCP, and then a cable modem who's MAC address is the one the cable company has 'registered' in their data base.

I do not know the layout you have; if your PC is behind a router with DHCP this should really be setting itself up.

We have a forum for network issues; and I have to be honest and say that I have not really had any network issues so I have not learned a whole lot about solving them in Ubuntu (I am sure my turn will come).

***The Hedge***

:KS

---

