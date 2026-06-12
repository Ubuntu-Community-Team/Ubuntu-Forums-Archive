---
title: "Grub or Grub2? - dual boot Ubuntu 9.10 and Arch"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by marpola on 2010-04-19
For two weeks I have been trying to install Ubuntu 9.10 and Arch on an old Dell 9300 laptop, freshly formatted with boot in a separate /dev/sda1. No Windows in my life.
I can install Ubuntu ok, default Grub2. I can install Arch ok, default Grub1. Either one can be installed first but neither recognizes the other.
After much reading of wikis and forum messages I still have no clear way to do this. I decided to stick with Grub2 for both since that is the future.
I am going to do a fresh install again. Where do I put the second install? In the boot directory of the second? If I install the second Grub2 into /dev/sda1 it overwrites the first.

---

### Post by Neds Moar Salt on 2010-04-19
If you want grub2 to be shown when you start up, install grub1 to your arch partition and grub2 to your mbr and then run `update-grub`.  It will recognize the chainload into grub1, but if not, drop into the grub console and type `chainloader (hd0,2)+1` and `boot` and it will chainload to grub legacy.

---

### Post by marpola on 2010-04-20
No change after two more installs. I installed arch /boot in /dev/sda1 and /root and /home in 2 other partitions. Grub1 was installed in /boot.
Reboot comes up with menu.lst screen and boots ok.
I installed Ubuntu 9.10 /boot in /dev/sda1 and formatted it. /root and /home went in 2 other partitions. No clue what bootloader is being installed. When I reboot I get only the grub console. 
Entering any commands gives only error messages.

Any more ideas?
This is the first time I tried a separate /boot partition. Do I need another partition for arch /boot? Maybe I should install the arch bootloader in arch /root partition.

I have four linux installs on my desktop and never had any problems. I upgraded Ubuntu to 9.10 from 9.04 and all os are in grub1 menu.lst.

---

### Post by oldfred on 2010-04-21
You cannot share /boot. Unless your system is old and your installs are inside the BIOS limits (depending on age) you do not need a separate /boot. Otherwise the /boot has to be inside the BIOS limit.

As Neds Moar Salt said, you can install grub legacy to the PBR partition boot record for the second install and chainboot from the first install.

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by marpola on 2010-04-21
Well,I am a little closer. I booted into Ubuntu 9.10 from the grub 1.97 menu which also included two entries for arch. That's a first.
When I rebooted to try arch it said you must install kernel first.

I did update-grub in Ubuntu terminal and it said done.
chainloader in the grub boot menu did not work.

I installed both bootloaders in their own boot partitions, arch grub1 first in /dev/sda9 and then Ubuntu grub2 (I assume) in /dev/sda1. They each have their own /root and /home partitions.
Searching thru your excellent grub2 reference in members.iinet I found the "easy" solution:
search -f /vmlinuz
no such device
search -f /sbin/init
hd0,6 hd0,3
These two / partitions are correct but without vmlinuz I couldn't  run the linux command. I guess I need another day of searching thru all the partitions in Ubuntu to find vmlinuz. 

Any more suggestions?

---

### Post by oldfred on 2010-04-21
In my system vmlinuz is just a link to the most current version of the kernel in my /  (boot/vmlinuz-2.6.31-21-generic). It is a shortcut in typing as you do not have to have the exact description and can use it even when the kernel is updated as its name does not change just the link.

Having a separate /boot changes some things.

Lets see where everything is at:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by marpola on 2010-04-23
I was reinstalling arch to have only one boot file when my install failed at Configure. Thinking it was a bad CD I downloaded two more but the same error appeared at the same place.

I will be on the arch forum until I find out what is wrong.
Be back later.

The Boot Info Script is a real treasure.

---

### Post by marpola on 2010-05-08
I am back to where I was 3 weeks ago. I had to replace my DVD drive and repartitioned hdd and installed over again.
I installed arch on /boot /dev/sda1 and / on /dev/sda7. Reboot was ok.
I installed Ubuntu 9.10 on /boot /dev/sda1 and on / /dev/sda5. Reboot was ok and still is. 

Arch will no longer boot.
Error: You need to install kernel first
Press any key.......

sudo grub-mkconfig created a new /boot/grub/grub.cfg file with arch included as follows:

### BEGIN /etc/grub.d/30_os-prober ###
Found Arch on /dev/sda7
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
        insmod ext2
        set root=(hd0,7)
        search --no-floppy --fs-uuid --set bef5e3b6-2401-475b-ad5a-fbd703b6bd0d
        linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ee082dc3-c4eb-44f3-8b96-016457051ff0 ro quiet splash
        initrd /boot/initrd.img-2.6.31-14-generic
}

Before I make any changes I would like some help. I have no idea what to do. grub2 is supposed find all installed systems.

How do I paste large files such as RESULTS.txt in a window?
Ubuntu doesn't provide wgetpaste.

---

### Post by oldfred on 2010-05-08
Just paste results.txt and then while still highlighted ( highlight the whole thing) and click on the code tags to put it in a scroll box and preserve formating. Code tags is the # on the right side of the edit panel above when editing.

I think the set root command has to refer to the boot partition hd0,1 where the UUID for kernel root has to refer to the root partition's UUID.

the set root line tells Grub where the /boot partition is.

---

### Post by marpola on 2010-05-08
Here is my RESULTS.txt file.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     2,104,514     2,104,452  83 Linux
/dev/sda2           2,104,515     6,249,284     4,144,770  82 Linux swap / Solaris
/dev/sda3           6,249,285   117,210,239   110,960,955   5 Extended
/dev/sda5           6,249,348    26,732,159    20,482,812  83 Linux
/dev/sda6          26,732,223    47,215,034    20,482,812  83 Linux
/dev/sda7          47,215,098    63,601,334    16,386,237  83 Linux
/dev/sda8          63,601,398    79,987,634    16,386,237  83 Linux
/dev/sda9          79,987,698   117,210,239    37,222,542  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6c2dfee0-bfd6-4f55-8f5f-6c5655f58e6d   ext3       boot                          
/dev/sda2        92b0493a-52bf-493d-8bfe-275a0ed386fd   swap                                     
/dev/sda5        ee082dc3-c4eb-44f3-8b96-016457051ff0   ext3                                     
/dev/sda6        2a09f1e2-0152-4a16-b205-a6d795329632   ext3                                     
/dev/sda7        bef5e3b6-2401-475b-ad5a-fbd703b6bd0d   ext3                                     
/dev/sda8        6d22fa63-2578-43c1-9a0e-5266aa421750   ext3                                     
/dev/sda9        383d4082-e953-408c-82f0-675bd2865ea1   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro)
/dev/sda6        /home                    ext3       (rw)
/dev/sda1        /boot                    ext3       (rw)
/dev/sda9        /spare                   ext3       (rw)


============================= sda1/grub/menu.lst: =============================

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   15
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /vmlinuz26 root=/dev/disk/by-uuid/bef5e3b6-2401-475b-ad5a-fbd703b6bd0d ro vga=773
initrd /kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,0)
kernel /vmlinuz26 root=/dev/disk/by-uuid/bef5e3b6-2401-475b-ad5a-fbd703b6bd0d ro
initrd /kernel26-fallback.img

# (2) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

============================= sda1/grub/grub.cfg: =============================

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
search --no-floppy --fs-uuid --set ee082dc3-c4eb-44f3-8b96-016457051ff0
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
	search --no-floppy --fs-uuid --set 6c2dfee0-bfd6-4f55-8f5f-6c5655f58e6d
	linux	/vmlinuz-2.6.31-14-generic root=UUID=ee082dc3-c4eb-44f3-8b96-016457051ff0 ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6c2dfee0-bfd6-4f55-8f5f-6c5655f58e6d
	linux	/vmlinuz-2.6.31-14-generic root=UUID=ee082dc3-c4eb-44f3-8b96-016457051ff0 ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set bef5e3b6-2401-475b-ad5a-fbd703b6bd0d
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ee082dc3-c4eb-44f3-8b96-016457051ff0 ro quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set bef5e3b6-2401-475b-ad5a-fbd703b6bd0d
	linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ee082dc3-c4eb-44f3-8b96-016457051ff0 ro single
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .1GB: grub/core.img
    .2GB: grub/grub.cfg
    .2GB: grub/menu.lst
    .2GB: grub/stage2
    .0GB: initrd.img-2.6.31-14-generic
    .1GB: vmlinuz26
    .0GB: vmlinuz-2.6.31-14-generic

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
UUID=ee082dc3-c4eb-44f3-8b96-016457051ff0 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=6c2dfee0-bfd6-4f55-8f5f-6c5655f58e6d /boot           ext3    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=2a09f1e2-0152-4a16-b205-a6d795329632 /home           ext3    defaults        0       2
# /spare was on /dev/sda9 during installation
UUID=383d4082-e953-408c-82f0-675bd2865ea1 /spare          ext3    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=92b0493a-52bf-493d-8bfe-275a0ed386fd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


   3.2GB: initrd.img
   3.2GB: vmlinuz

=============================== sda7/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
#/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

/dev/sda1 /boot ext3 defaults 0 1
/dev/sda2 swap swap defaults 0 0
/dev/sda7 / ext3 defaults 0 1
/dev/sda8 /home ext3 defaults 0 1
/dev/sda9 /spare ext3 defaults 0 1








```

---

### Post by oldfred on 2010-05-08
I think you have been using the same /boot for everyone. As I said 2 weeks ago you cannot share /boot. You either have to have a /boot for every install or just keep the boot directory in the root install. You keep overwriting the /boot with last installs data and then it cannot find the others.

grub does not like to be installed with grub2 but you can easily chainboot from grub2 to grub. 

I would reinstall arch and leave its /boot inside root, no separate /boot. I would also install it's grub to the arch partition sda7 so you can chainboot to it.

---

### Post by brc816 on 2010-05-08
I vehemently disagree that you can chainload from Grub2 to Grub(0.97).

I have Ubuntu 10.04LTS (32 bit) installed on a 16GB thumb drive and also on a 1TB USB drive and in NEITHER case can I chainload from Ubuntu's GRUB2 <stuff> into Grub(0.97).

What's even more irritating is that everything in each of the grub.cfg's leads me to believe that Grub2 sized everything properly. For example, it properly sets things up to look for Windows XP to be chainloaded off of (hd0,1), which is where it really is - on the first partition of the first internal hard drive. But when I try to boot it, Grub2 complains that it's NOT there. My laptop is set up with Grub (0.97) boot sector in the MBR of the first hard drive from which it "bounces" into the /boot directory on the second partition of my second hard drive.
It's been working properly that way for about 2.5 years.

Furthermore, if when I boot Ubuntu (either installation) to Grub2's menu, and then hit 'c' to get a Grub2 command prompt, and then issue an 'ls' command, it tells me, in effect, that (hd0) is the USB drive. (On the Cruzer thumb drive, the Ubuntu root file system is at partition 1 and the swap area is on partition 5. There is no partition 5 on either of the internal hard drive, so there's no mistaking this issue.) The 'ls' command displays only one of the other hard drives, as (hd1), which turns out to be my openSUSE 11.2 installation. There is no (hd2) displayed, yet the grub.cfg specifically calls out (hd2) as being the Ubuntu system "disk".

I see similar issues with the 1TB USB drive even though it has a GPT and an LVM on it - it refuses to see all 3 spindles, and adamantly refuses to boot Windows.

In both cases, it attempts to boot openSUSE from the selected menu item, but generally fails in its initialization routines because openSUSE appears to have problems finding its drives.
I have to manually fsck the /home partition and then mount it and manually kick it to 'init 5', and even then it comes up as logged in under root instead of my user account.

So, it's beginning to appear that there is something radically wrong with the drive enumeration/sizing routines in Grub2 V1.98.

I've seen at least a half dozen different threads in the Ubuntu installation forums complaining about various similar problems. It's been very difficult to reconcile my problems as well as the other complaints with the open bugs on the GRUB2 web site, so I can't clearly state if this is really a "known" problem or not.

---

### Post by marpola on 2010-05-09
I have installed arch boot on to arch root and all the boot info is there now. 
The problem was the arch install menu. At the time of selecting the boot partition the choices were either a separate /boot, or none which terminates the install, or ignore with a warning. This time I selected ignore and all the boot info went into arch root. 
I ran sudo grub-mkconfig from Ubuntu and the new grub.cfg appeared on the screen and appeared to be correct. But the file is not updated.
Now what? Here is the console output of grub-mkconfig and the ls -l before and after.

```
  
turtle@laptop:/boot/grub$ ls -l grub.cfg
-rw-r--r-- 1 root root 3189 2010-05-08 22:59 grub.cfg
turtle@laptop:/boot/grub$ sudo grub-mkconfig
Generating grub.cfg ...
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
search --no-floppy --fs-uuid --set ee082dc3-c4eb-44f3-8b96-016457051ff0
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
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6c2dfee0-bfd6-4f55-8f5f-6c5655f58e6d
	linux	/vmlinuz-2.6.31-14-generic root=UUID=ee082dc3-c4eb-44f3-8b96-016457051ff0 ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6c2dfee0-bfd6-4f55-8f5f-6c5655f58e6d
	linux	/vmlinuz-2.6.31-14-generic root=UUID=ee082dc3-c4eb-44f3-8b96-016457051ff0 ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /memtest86+.bin
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Arch on /dev/sda7
menuentry "Arch Linux (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set bef5e3b6-2401-475b-ad5a-fbd703b6bd0d
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/bef5e3b6-2401-475b-ad5a-fbd703b6bd0d ro
	initrd /boot/kernel26.img
}
menuentry "Arch Linux Fallback (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set bef5e3b6-2401-475b-ad5a-fbd703b6bd0d
	linux /boot/vmlinuz26 root=/dev/disk/by-uuid/bef5e3b6-2401-475b-ad5a-fbd703b6bd0d ro
	initrd /boot/kernel26-fallback.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
done
turtle@laptop:/boot/grub$ ls -l grub.cfg
-rw-r--r-- 1 root root 3189 2010-05-08 22:59 grub.cfg
 


```

---

### Post by oldfred on 2010-05-09
Does Arch give you a choice on where to install grub or can you use it to install its grub to its partition and chainboot it?

---

### Post by marpola on 2010-05-09
Yes, arch gives a choice of where to install the bootloader. This time I put it into / and all the install files are there.

I placed it once before in sda1. When I reinstalled ubuntu /boot into sda1 I did not format it first and now I still have a menu.lst and boot files for arch left there. This may cause some confusion in grub2.

I am going to format sda1 and install ubuntu 9.10 once more so I know I have a clean install of both.

One more install won't hurt. I have both processes memorized now.

I read thru some of the posts in "Does anyone else hate Grub2?"
Not very encouraging.

---

### Post by marpola on 2010-05-09
Finally! A dual boot with ubuntu 9.10 and arch.

I reinstalled ubuntu with a format of /boot, /dev/sda1.
I did nothing else but reboot and the menu showed the correct arch line and it booted. Another reboot and it was back in ubuntu.

I guess the secret is a clean install of arch first in its own default boot partition and ubuntu into a separate boot partition.

How do you mark a thread as solved?

Thanks for your help oldfred.

---

### Post by brc816 on 2010-05-12
I will agree that booting Grub Legacy (0.97) and chainbooting from it into a Grub2 installation will work nicely - I did so several months ago on my 250GB USB drive with Karmic Koala.

My issues have to do with initially booting Grub2 and then trying to chainload into a Grub Legacy (0.97) - it simply doesn't work for me so far, and I've tried using an installation on a 16GB Cruzer thumbdrive and also a 1TB USB drive.

I suspect there is an issue with the way Grub2 "sizes" the various disks that it can see through the BIOS. It might not be designed to deal with two internal hard drives and then boot from an attached USB drive,  and/or it is iterating the buses in reverse order for whatever reason. I haven't tried to analyze the Grub2 code - I'm simply reporting the symptoms I've seen.

---

### Post by oldfred on 2010-05-12
You may be correct as I had no problem chainbooting with my 3 fixed drives. The issue probably is the chainboot does not use UUID but drive, partition and with USB devices those numbers can change.

---

### Post by brc816 on 2010-05-13
Precisely, and I was able to work around it (i.e. in a Grub Legacy 0.97 environment) by manually editing my menu.lst appropriately.

I know I could have edited device.map instead, but chose not to.

So, given that we're not supposed edit grub.cfg, I'm out of options.

What's really annoying is that everything in grub.cfg and the onscreen menu *appears* to be correct - I'm relatively inexperienced with Grub2, but what I'm seeing looks fairly logical.

However, when I drop to a (grub2) command prompt and do an 'ls' to determine what it's seen/seeing, that I realize it isn't seeing all of my spindles and what it does see is in a different order from the way Grub Legacy (0.97) did things.

So, I'm going to punt on trying to boot a Grub Legacy disk from within a Grub2 menu and now concentrate on installing other distros onto LVM partitions and trying to boot those.

Oldfred - thank you so much for your help so far. I'll keep checking around to see if someone comes up with a workaround or fix.

---

### Post by oldfred on 2010-05-13
It is a kluge but you can enter a multiple of alternatives into /etc/grub.d/40_custom and then see what works.

Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
OR:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.

---

