---
title: "Can't access my own files after upgrading to 10.10. I'm desperate :("
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by Fury161 on 2011-04-13
Please, I need help!

I tried the Beta 1 of Ubuntu 11.04. Yesterday night it crashed, screen went black, white and defigured. I couldn't solve it so I reinstalled from Beta CD.

Then, I got this problem: "/usr/lib/libconf-2-4/gconf-sanity-check-2". Nothing worked. I used the recomendations for it in the web but it didn't work. I tried with 10.10 but the same problem and also for 10.04

I have two partitions on the hard drive. One for / and one for /home

Now, I have installed the whole Ubuntu in the former "/ partition". But it's impossible for me to recover my personal files in the former "home partition" :'( It says I'm not the owner. I cannot change permissions, cannot copy them, cannot do anything :'(

Please help!!

---

### Post by Hedgehog1 on 2011-04-13
We can help!

Please do this for the info we need to help:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-04-13
Also - if you reinstall 10.10 or 10.04, we can return the old '/home' partition to be what it was was before the Natty 'experiment', with your data there and accessible (use the SAME login name as you used to before the experiment).

Which do you want to run? 10.10 or 10.04.02 LTS?


***The Hedge***

:KS

---

### Post by Fury161 on 2011-04-13
I have always done that when I had a problem. Reinstall and use the same login so I could access my files in the home partition. But now I reinstall (11.04 Beta, 10.10 or 10.04) and it crashes at the begining, no icons, no toolbars, nothing. So I thought it would be easier to "clean" my home from any configuration file and leave just with personal documents. So I installed the whole Ubuntu in the former "/ partition". Now Ubuntu works but I cannot access my files. I have used the same user too this time. What can I do?

I have tried to move all the folders (from programs in home) to another one so it got "inactive" if I mounted the "/home" there so it didn't crash but they are protected so I can not move them. Do you understand me? :$

---

### Post by Fury161 on 2011-04-13
Ok, I've managed to erase everything in my "/home" except my personal files. So now, I can enter Ubuntu without it crashing. Ok, my user as always, mount the partition as /home. But I keep on having the problem with permissions. I cannot open the folders :'(

It says it belongs to "500 - user #500"

---

### Post by Hedgehog1 on 2011-04-13
Fury161,

If the issue is just down to a an old internal value for your user ID is still attached to the files and directories, then changing the ownership of them is the correct next step.

The chown (**Ch**ange **Own**ership) commnand is used for this.

To read more about it, you can look here: [http://en.wikipedia.org/wiki/Chown]("http://en.wikipedia.org/wiki/Chown")

or:

```
man chown
```

So, we need to change ownership to the current internal value your user name has. 

First, lets mount the old partition:

```
sudo mkdir /media/oldhome
```

Change the 'x' of sda**x** to the partition number that holds your old '/home' directory:
```
sudo mount /dev/sda**_x_** /media/oldhome
```

Change the user name of '**hedgehog**' to the **user name you log in as**:
```
sudo chown -R **hedgehog** /media/oldhome/home
```

The directories and files in /media/oldhome/home will now be assigned the current internal value that now matches your user name (most likely 501, since 500 was already taken).

You should be able to read your 'old home' data now; you are the owner again.


***The Hedge***

:KS

---

### Post by Fury161 on 2011-04-13
Done!! It worked!! 

I really really thank you. I was so worried!! You really helped me a lot :P

Thanks again!!

---

### Post by Hedgehog1 on 2011-04-13
I am sorry I didn't realize the real issue sooner.  I am often working several threads at a time, and occasionally I get a little muddled (***Little Hedgie Brain***, you know). :D


But with no data lost and you happy, I am happy, too.


***The Hedge***

:KS

---

### Post by entarr on 2011-08-03
Im having this exact same problem. Only I upgraded from 10.04 to 11.04. I tried doing the steps you've posted, but apparently I am a complete n00b and can't seem to get it to work. Here's the results from my boot script. I don't know how much of this that you need/don't need. I'm sorry if I posted too much..

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   224,827,391   224,825,344  83 Linux
/dev/sda2         224,829,438   234,440,703     9,611,266   5 Extended
/dev/sda5         224,829,440   234,440,703     9,611,264  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        75eddd84-9f0a-4bf8-b84c-11419136edcf   ext4       
/dev/sda5        ec5af82a-d6af-4ead-b7a2-6f2d2245335a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 75eddd84-9f0a-4bf8-b84c-11419136edcf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 75eddd84-9f0a-4bf8-b84c-11419136edcf
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 75eddd84-9f0a-4bf8-b84c-11419136edcf
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=75eddd84-9f0a-4bf8-b84c-11419136edcf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 75eddd84-9f0a-4bf8-b84c-11419136edcf
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=75eddd84-9f0a-4bf8-b84c-11419136edcf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 75eddd84-9f0a-4bf8-b84c-11419136edcf
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=75eddd84-9f0a-4bf8-b84c-11419136edcf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 75eddd84-9f0a-4bf8-b84c-11419136edcf
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=75eddd84-9f0a-4bf8-b84c-11419136edcf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 75eddd84-9f0a-4bf8-b84c-11419136edcf
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=75eddd84-9f0a-4bf8-b84c-11419136edcf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 75eddd84-9f0a-4bf8-b84c-11419136edcf
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=75eddd84-9f0a-4bf8-b84c-11419136edcf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 75eddd84-9f0a-4bf8-b84c-11419136edcf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 75eddd84-9f0a-4bf8-b84c-11419136edcf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=75eddd84-9f0a-4bf8-b84c-11419136edcf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ec5af82a-d6af-4ead-b7a2-6f2d2245335a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   8.137611389 = 8.737693696    boot/grub/core.img                             1
  88.159080505 = 94.660091904   boot/grub/grub.cfg                             1
   1.758003235 = 1.887641600    boot/initrd.img-2.6.35-28-generic              2
  12.520763397 = 13.444067328   boot/initrd.img-2.6.38-10-generic              1
  92.829101562 = 99.674488832   boot/initrd.img-2.6.38-8-generic               2
   8.258975983 = 8.868007936    boot/vmlinuz-2.6.35-28-generic                 1
  11.665348053 = 12.525572096   boot/vmlinuz-2.6.38-10-generic                 1
   8.789196014 = 9.437327360    boot/vmlinuz-2.6.38-8-generic                  1
  12.520763397 = 13.444067328   initrd.img                                     1
  92.829101562 = 99.674488832   initrd.img.old                                 2
  11.665348053 = 12.525572096   vmlinuz                                        1
   8.789196014 = 9.437327360    vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

