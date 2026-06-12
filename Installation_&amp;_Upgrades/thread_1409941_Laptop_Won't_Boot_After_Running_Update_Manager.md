---
title: "Laptop Won't Boot After Running Update Manager"
date: 2010-02-18
forum: Installation &amp; Upgrades
---

### Post by peterdc on 2010-02-18
Hi experts,

I'm a little bit stuck and in need of advice from people who know what they're talking about.  I've had Ubuntu on my office PC, home PC and laptop for about a year now and never had a problem that I couldn't solve, until now.

I'd not turned my laptop (**Lenovo N 500 with Ubuntu 9.10 64 Bit using GRUB2**) on for about a month so when I did on Monday of this week I noticed that I'd not updated Ubuntu for 27 days, so ran the update manager.  After everything was updated I carried on using it as normal but when I tried to turn it on yesterday I get the following issue...

GRUB loads and gives me all the possible boot options.  Whatever one I choose, I get the same results.  It starts to boot (I see the black screen with the white Ubuntu logo) but this remains on the screen for a very long time, then it goes to a flashing cursor at the top left of the screen and it just sits there indefinitely.

I've tried playing with Super GRUB Disc but admittedly I'm not too sure what I'm doing with it.  I've tried using the Ubuntu Installation disc as a Live CD too but with no joy.  The main HDD appears fine when in Live CD mode, all my files are there etc...

Is this actually a GRUB issue or something else?  It's like GRUB's doing its bit and then it's failing slightly further down the line.

Please help, I'm totally out of my depth here and really don't want to have to reinstall everything, I'm sure there's a simply solution.

Many thanks!

---

### Post by darkod on 2010-02-18
Please follow these instructions:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

and post your results here. Maybe they will offer some explanation.

---

### Post by peterdc on 2010-02-18
Many thanks for your reply Darko.

Here's the results (I had my USB stick plugged in when I ran it, hence the sdb1 reference?):

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa99d4936

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   602,003,744   602,003,682  83 Linux
/dev/sda2         602,003,745   625,137,344    23,133,600   5 Extended
/dev/sda5         602,003,808   625,137,344    23,133,537  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  52    31,283,909    31,283,858   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        af8f0f09-bcb6-43ed-8e12-997f6e4f7692   ext3                                     
/dev/sda5        82d3a95d-bc23-4571-9df5-d3b2e50a48f2   swap                                     
/dev/sdb1        7816-8A9D                              vfat       PDC (T16GB)                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/PDC               (T16GB)    vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=af8f0f09-bcb6-43ed-8e12-997f6e4f7692

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Chainload into GRUB 2
uuid        af8f0f09-bcb6-43ed-8e12-997f6e4f7692
kernel        /boot/grub/core.img

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root
        
title        When you have verified GRUB 2 works, you can use this command to
root

title        complete the upgrade:  upgrade-from-grub-legacy
root

title        ÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄÄ
root

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        af8f0f09-bcb6-43ed-8e12-997f6e4f7692
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro quiet splash
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        af8f0f09-bcb6-43ed-8e12-997f6e4f7692
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        af8f0f09-bcb6-43ed-8e12-997f6e4f7692
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro quiet splash
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        af8f0f09-bcb6-43ed-8e12-997f6e4f7692
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, memtest86+
uuid        af8f0f09-bcb6-43ed-8e12-997f6e4f7692
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

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
search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
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
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro single vga=769
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro single vga=769
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro single vga=769
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro single vga=769
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro single vga=769
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro vga=769  quiet splash
    initrd    /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set af8f0f09-bcb6-43ed-8e12-997f6e4f7692
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 ro single vga=769
    initrd    /boot/initrd.img-2.6.28-16-generic
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
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=af8f0f09-bcb6-43ed-8e12-997f6e4f7692 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=82d3a95d-bc23-4571-9df5-d3b2e50a48f2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 172.3GB: boot/grub/core.img
 187.8GB: boot/grub/grub.cfg
 172.3GB: boot/grub/menu.lst
 185.2GB: boot/initrd.img-2.6.28-16-generic
 185.3GB: boot/initrd.img-2.6.31-14-generic
 185.7GB: boot/initrd.img-2.6.31-15-generic
 282.7GB: boot/initrd.img-2.6.31-16-generic
  20.7GB: boot/initrd.img-2.6.31-17-generic
 282.7GB: boot/initrd.img-2.6.31-19-generic
 248.5GB: boot/vmlinuz-2.6.28-16-generic
 248.5GB: boot/vmlinuz-2.6.31-14-generic
 185.2GB: boot/vmlinuz-2.6.31-15-generic
  77.4GB: boot/vmlinuz-2.6.31-16-generic
 196.9GB: boot/vmlinuz-2.6.31-17-generic
 284.6GB: boot/vmlinuz-2.6.31-19-generic
 282.7GB: initrd.img
  20.7GB: initrd.img.old
 284.6GB: vmlinuz
 196.9GB: vmlinuz.old
```

---

### Post by darkod on 2010-02-18
You have kernel 2.6.28 so this was an upgrade from 9.04 to 9.10. Grub1 needs to be upgraded to grub2 separately and maybe that process is not completely done.

Just to make sure which version of grub are you running, what does:

sudo grub-install -v

say? 1.97 is for grub2, 0.97 for grub1 or grub legacy.

You can see in your menu.lst file there is a remark to finish the upgrade with

sudo upgrade-from-grub-legacy

Did you ever run this command?

---

### Post by peterdc on 2010-02-18
Yes I ran those commands months ago to manually upgrade to GRUB2 when I upgraded from Ubuntu  9.04 to 9.10 and it all worked fine then and has been ever since.  In fact I did a complete/clean install of 9.10 when it came out on one of my machines and I think that was my laptop, so that should have installed GRUB2 by default.  Either way I've had 9.10 and GRUB2 running on here for months with no problems.

I've also tried running those commands this moring (just in case) using the live CD but nothing would work, I'll try again and post the errors here.

---

### Post by peterdc on 2010-02-18
If I run **sudo grub-install -v**, I get:

```
grub-install (GNU GRUB 1.97~beta4)
```If I try **sudo upgrade-from-grub-legacy**, I get:

```
core.img doestn't exist, trying to create it.

grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
```I get confused when running commands from a Live CD - is that error genuine or is it because it's looking at the 'Live CD' file system and not that on my HDD?

---

### Post by darkod on 2010-02-18
> **peterdc said:**
> I get confused when running commands from a Live CD - is that error genuine or is it because it's looking at the 'Live CD' file system and not that on my HDD?

I'm not sure in this case either. I think you might be right.
But on another note, I really don't see anything wrong with your results file. You could try reinstalling grub2 to the MBR of /dev/sda but that is more of a desperation move.

And make sure you are using a 9.10 cd for reinstalling grub2. From live desktop do:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot without the cd, but honestly, I don't hope for much. :(

---

### Post by theozzlives on 2010-02-18
Everything looks okay in your results.txt. I'm thinking an incompatibility in the video arena. Like you said GRUB loads fine. Have you tried recovery mode? What kinda video do you have?

---

### Post by arizonalarry2 on 2010-02-18
I just did an update and now my system won't start either ( thank god for live CDs ). I'll try the things suggested above and post the results in a bit.

---

### Post by peterdc on 2010-02-18
> **darkod said:**
> 

And make sure you are using a 9.10 cd for reinstalling grub2. From live desktop do:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Reboot without the cd, but honestly, I don't hope for much. :(
No, like you say, that's not achieved anything sadly. :(  Many, many thanks for taking the time to help, it's really appreciated! :)

> **theozzlives said:**
> Have you tried recovery mode? What kinda video do you have?
Yes, have tried every option in the GRUB menu, including the Recovery Mode ones.  I'm not sure what video hardware is in the laptop, how would I go about finding out in Ubuntu?

I wish there was a way of dumping and posting the information that's printed on the screen when trying the Recovery Modes - it prints out about 40 lines and then just sits there and I have to turn the laptop off and on again.

---

### Post by arizonalarry2 on 2010-02-18
Okay, here's what happened-

I booted up, got the grub menu and tried booting as normal. I get the white Ubuntu logo on the black background with messages scrolling by that say 'Filesystem check in process'. Then I got a 'Mount of filesystem failed' message and the maintenance shell started.

While in the maintenance shell I ran sudo grub-install -v with the result of - 'grub-install (GNU GRUB 1.97~beta4)

I then ran sudo upgrade-from-grub-legacy with the result of -
0
debconf: DbDriver "config": could not write /var/cache/debconf/config.dat-new: Read-only file system

I then rebooted the live CD and ran the boot_info_script with this result - 

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

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000427cf

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   151,043,129   151,043,067  83 Linux
/dev/sda2         151,043,130   156,296,384     5,253,255   5 Extended
/dev/sda5         151,043,193   156,296,384     5,253,192  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ffe66c16-6863-401b-a562-c9c7e59bda9c   ext4                                     
/dev/sda5        cb0c1ac1-b030-4457-bf3e-5b1a5820237b   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
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
search --no-floppy --fs-uuid --set ffe66c16-6863-401b-a562-c9c7e59bda9c
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ffe66c16-6863-401b-a562-c9c7e59bda9c
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=ffe66c16-6863-401b-a562-c9c7e59bda9c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ffe66c16-6863-401b-a562-c9c7e59bda9c
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=ffe66c16-6863-401b-a562-c9c7e59bda9c ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ffe66c16-6863-401b-a562-c9c7e59bda9c
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=ffe66c16-6863-401b-a562-c9c7e59bda9c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ffe66c16-6863-401b-a562-c9c7e59bda9c
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=ffe66c16-6863-401b-a562-c9c7e59bda9c ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ffe66c16-6863-401b-a562-c9c7e59bda9c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ffe66c16-6863-401b-a562-c9c7e59bda9c ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set ffe66c16-6863-401b-a562-c9c7e59bda9c
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=ffe66c16-6863-401b-a562-c9c7e59bda9c ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ffe66c16-6863-401b-a562-c9c7e59bda9c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cb0c1ac1-b030-4457-bf3e-5b1a5820237b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  13.0GB: boot/grub/core.img
  10.6GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .8GB: boot/initrd.img-2.6.31-17-generic
   1.3GB: boot/initrd.img-2.6.31-19-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-17-generic
   1.2GB: boot/vmlinuz-2.6.31-19-generic
   1.3GB: initrd.img
    .8GB: initrd.img.old
   1.2GB: vmlinuz
    .6GB: vmlinuz.old
```


Thanks for any help!

---

### Post by darkod on 2010-02-18
I can't see anything wrong here either. Is something wrong with this -19 update???

Anyone?

---

### Post by darkod on 2010-02-18
I'm wondering if removing the -19 kernel can resolve this. Provided that was the problematic update.

But I have never tried to do that and it could mess it up more. :) Otherwise, the process would be:

1. Boot the recovery entry from the 2.6.31-17 kernel. In the next menu select something like "netroot with networking".

2. Once the command prompt loads (you only get a text based command prompt in recovery mode), try:

sudo apt-get remove --purge linux-image-2.6.31-19-generic
sudo update-grub

That should remove the -19 kernel and update the grub menu. Reboot just with

reboot

and see if it helped. Hopefully it won't be worse. :)

---

### Post by peterdc on 2010-02-18
> **darkod said:**
> 1. Boot the recovery entry from the 2.6.31-17 kernel. In the next menu select something like "netroot with networking".
I can't do this because even the Recovery Mode will fail (just prints a few things to the screen then freezes) - is step 2 something I can try from the Live CD?

---

### Post by darkod on 2010-02-18
> **peterdc said:**
> I can't do this because even the Recovery Mode will fail (just prints a few things to the screen then freezes) - is step 2 something I can try from the Live CD?

In theory, yes if you chroot into your ubuntu root partition. But success is not guaranteed even with the first procedure.

To chroot from live desktop:

```
sudo -i
mount /dev/sda1 /mnt
mount --bind /proc /mnt/proc
mount --bind /dev /mnt/dev
mount --bind /sys /mnt/sys
chroot /mnt

apt-get remove --purge linux-image-2.6.31-19-generic
update-grub

umount /mnt/sys
umount /mnt/dev
umount /mnt/proc
exit
```

That should be it.

---

### Post by Nick Brohman on 2010-02-19
G'day peterdc,

I share your pain, I've been trying to boot my Presario CQ61 since last Sunday, have searched the forums but probably did the search on the wrong pages. Same error as yourself...'Mount filesystem failed.'

Go to this thread...post 2

[http://ubuntuforums.org/showthread.php?t=1408486&highlight=Failed+mount+filesystem](http://ubuntuforums.org/showthread.php?t=1408486&highlight=Failed+mount+filesystem)

I ran that command but got no result.

I then ran it again making using /dev/sda1.

That's started the ball rolling, so to say...I'm currently watching sript just rolling over.

I've been told that it can take a long time.

I'll let you know if it works, read the thread because another command might be required to finish the job.
 
While there is a flashing dash,  fsck is working for you. You might want to make a pot of coffee.

When you get a blank screen, I'd say that is just the power manager kicking in, just hit the space bar to bring back the script.

It has just come to an end and the second command has not worked for me, I'm now getting a Bus error....the solution has worked for others but not for me.

I'm going to start again to see if I can get 2.6.31-17 to boot.

**Update of this post: I appear to have a program running which is blocking this and, as a complete computer novice, I am at a loss as to what to do next. I'm running fsck now after trying to boot in recovery mode using the 17 Kernel.**

Cheers

---

### Post by peterdc on 2010-03-02
Just a quick update.  I didn't have the time or knowledge to try fixing it any further, so went in on a Live CD, backed up my home directory and re-installed 9.10 64 Bit from scratch, ran all updates, then re-installed all my applications and restored my settings.  To date, no problems.

Rebuilding a Ubuntu machine is a hell of a lot quicker than a Windoze environment, I've spent days/weeks getting them back to the way they were before (and believe me, I've had practice).

Many thanks for all the help and advice above, it is much appreciated. :p

---

