---
title: "Ubuntu Won't Boot"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by vipes27 on 2010-06-30
Maybe this isn't a problem, but I'm a complete Ubuntu newb and am having trouble getting it to boot. I previously had Ubuntu 9.10 installed but had a HD failure, so after using an old hard drive and installing Ubuntu, it doesn't seem to boot up. During the boot process a screen comes up that says, "GNU Grub 1.97 beta." It lists 4 options, I apologize for not writing them down, but each one I select, it says something to the effect of, "No boot device." Again, sorry for not writing that down, but I was hoping someone would be able to figure it out. If you need more information, I can copy it down tonight. I guess I'm just not sure what to do next. When I previously installed Ubuntu, it just went straight to the desktop.

Thanks in advance for suggestions.

---

### Post by darkod on 2010-06-30
If you are using only ubuntu, grub2 doesn't need to use the boot flag to boot. So it doesn't set a boot flag on any partition. But some BIOS might refuse to continue the startup process if you have no boot flag, even if grub2 doesn't need it.

Boot with the ubuntu cd in live mode, open Gparted in System-Administration, and right click the root partition for example and set a boot flag on it. Try to boot again without the cd.

---

### Post by vipes27 on 2010-06-30
Thanks, darkod. Yes, it only has Ubuntu on it, I got rid of Windows. I'll give that a shot tonight and hopefully will be up and running.

Thanks again.

---

### Post by vipes27 on 2010-06-30
Sorry, meant to post this in the last reply, but just to make sure; in Gparted, I just have to right-click on the partition and there will be an option for, "Set Boot Flag," or something similar? Sorry, still trying to figure all of this out.

---

### Post by darkod on 2010-06-30
I'm actually not sure right now, with the right click in the menu that open I think there will be Flags option, and when you move the pointer over it it will expand with the flag options and there should be boot there.

---

### Post by oldfred on 2010-06-30
When you right click on the partition, one of the choices is manage flags. Select boot flag.

You can use gparted, right click on partition & manage flags, Disk Utility, or command line:
set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda

---

### Post by vipes27 on 2010-06-30
Okay, I'm on my Ubuntu machine with the live CD. I opened Gparted and it showed the following partitions:

[B]/dev/dsa1        ext4           147GB
/dev/dsa2        extended    1.42GB[/B]

It showed dsa1 marked with Boot, so I unchecked it and checked it again. I rebooted and took out the CD, but I still got the following screen:

[B]Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory Test (memtest86+)
Memory Test (memtest86+, serial console 115200[/B]

No matter which option I choose it gives me the error, "error: no such device."

I still don't know what the problem is. Am I doing something wrong? I've never had a problem installing/running Ubuntu. Any thoughts?

Thanks

---

### Post by darkod on 2010-06-30
1. If you are running only ubuntu it shouldn't show you a boot menu at all. Did you set it up to show?

2. "error: no such device" is not the same as "no boot device" :)

Follow the boot info script link in my signature, run it and post the content of the results file as explained. You can do all that from live mode.

---

### Post by vipes27 on 2010-06-30
I only have Ubuntu on here. When doing the install I chose to use the entire disk, writing over the copy of XP. Here are the results of the script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b36bdea

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   309,588,614   309,588,552  83 Linux
/dev/sda2         309,588,615   312,576,704     2,988,090   5 Extended
/dev/sda5         309,588,678   312,576,704     2,988,027  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        c0337bdf-9e32-4620-bfac-d10091aeea45   ext4                                     
/dev/sda5        2975bbf5-c8e5-4ea9-b6ac-5a0876c0e298   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
search --no-floppy --fs-uuid --set c0337bdf-9e32-4620-bfac-d10091aeea45
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
    search --no-floppy --fs-uuid --set c0337bdf-9e32-4620-bfac-d10091aeea45
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c0337bdf-9e32-4620-bfac-d10091aeea45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set c0337bdf-9e32-4620-bfac-d10091aeea45
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=c0337bdf-9e32-4620-bfac-d10091aeea45 ro single 
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
UUID=c0337bdf-9e32-4620-bfac-d10091aeea45 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2975bbf5-c8e5-4ea9-b6ac-5a0876c0e298 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: boot/grub/core.img
    .2GB: boot/grub/grub.cfg
    .2GB: boot/initrd.img-2.6.31-14-generic
    .1GB: boot/vmlinuz-2.6.31-14-generic
    .2GB: initrd.img
    .1GB: vmlinuz
```

---

### Post by darkod on 2010-06-30
Try this: start the computer but in the boot menu don't hit Enter, just highlight the ubuntu normal mode entry. Then hit 'e'. It will show you the boot lines.
Delete the line starting with search.
Hit Ctrl+X to boot. If that helps we can make the fix permanent.

---

### Post by oldfred on 2010-06-30
UUIDs look correct.

Try  deleting the search line per this link:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

Sometimes just reinstalling grub after you have booted it fixes it.

If you can boot then run this:

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub

sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

---

### Post by vipes27 on 2010-06-30
Thanks darkod, taking out the search line allowed it to boot. How do I make that change permanent, or is it?

Thanks again.

---

### Post by darkod on 2010-06-30
This time it was only temporary. The first link oldfred provided in his last post is the solution to make it permanent. Because we already located the problem, start from Step 4, the first steps are to search for the problem.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

### Post by vipes27 on 2010-07-01
Thanks to the both of you, it's now booting up to the desktop. Thanks again for your help.

---

### Post by vipes27 on 2010-07-01
Thanks to the both of you, it's now booting to the desktop. Thanks again for your help.

---

