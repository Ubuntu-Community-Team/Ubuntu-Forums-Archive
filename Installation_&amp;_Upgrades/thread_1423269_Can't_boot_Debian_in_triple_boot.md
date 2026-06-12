---
title: "Can't boot Debian in triple boot"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by kat3c on 2010-03-06
O.K., I'm a newbie, and I'm lost.  After reading hours on GRUB and bootloaders, I still don't understand much.  Here's my story:

I had (and still do) a working dual-boot XP/Karmic (GRUB version 1.97 beta4).  I shrank the Ubuntu partition and set up partitions and installed Debian 5.04.  When I got to the point of installing GRUB, I told Debian to install grub to MBR.  On rebooting, Ubuntu was not an option on the NEW (looked different) grub menu.  Maybe it was GRUB2?  Could boot to either XP or Debian though.

Thought easiest thing was to reinstall Ubuntu since it seems to "see" other OS's more reliably.  So I did, and installed GRUB again during its install to MBR.  Then, all three were in the GRUB menu (version 1.97 beta4 again), but when tried booting to Debian, got an error (forget the wording), but think it was because the partitions got renumbered when installing Ubuntu.

SO, reinstalled Debian, reformatting the partitions but not deleting them first so the numbering stayed the same.  When got to the part for installing GRUB, I told it to skip, hoping now the current GRUB would work.

Now, all three are on the GRUB menu, but when I try to boot Debian, I get "no such device" and a list of numbers/letters after it.  And "press any key to continue", which takes you back to the GRUB menu (version 1.97 beta4, by the way).

What to do?  Ideas?  When I try booting from Super GRUB USB, it only sees the Windows (by name) OS, and then lists a stage 1 and stage 1_5?  What's that?

Thanks for any help.

---

### Post by kat3c on 2010-03-06
O.K., did sudo update-grub in ubuntu and rebooted.  Now, Debian 5.04 shows as last entry in GRUB, and choosing it starts a boot, which hangs at "Begin:  Waiting for root file system....".

Ideas?

---

### Post by kat3c on 2010-03-06
One more piece of info.  Waiting long enough at the "Waiting for root file system..." hang results in a series of notifications:

WARNING bootdevice may be renamed.  Try root=dev/hda3
Gave up waiting for root device.  Common problems:
-Boot args (cat /proc/cmdline)
 -Check rootdelay= (did the system wait long enough?)
 -Check root= (did the sytem wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/sda3 does not exist.  Dropping to a shell!


In Gparted, the partition with Debian root is hdc3, although on the GRUB menu it's listed as /dev/sda3.  However, in Gparted the Windows partition is hdc1 and on GRUB it's /dev/sda1, and it boots fine.....


Is my Debian install just borked?  Did telling it to skip installing a bootloader (I got some kind of error that said "Install failed.  This is a fatal error.  You will have to boot with an external device..." ruin it?

If skipping the bootloader install did ruin it, how do you install Debian without borking your current GRUB?  That's what happened the first time.

---

### Post by khelben1979 on 2010-03-06
As a Linux newbie I think you should focus on making things easy instead of difficult and having different distributions installed on different harddrives instead of different partitions is a lot easier or stick to one distribution at a time.

Also, you have the possibility to use YouTube to educate yourself about how Linux works if you find reading documentation boring.

Okay, so good luck on this and one advice is to lower down your speed in how you do things to better understand what you're doing. There's no speed contest in understanding Linux in my opinion.

---

### Post by oldfred on 2010-03-06
To understand where everything is:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by kat3c on 2010-03-06
Below are the results.  I highlighted/noted what I think is of interest, doesn't mean it is......Thanks.               


 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

#Ubuntu root part#
[COLOR=Red][B]sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/B][/COLOR]

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

[COLOR=Red][B]#Debian root part#
sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /etc/fstab[/B][/COLOR]

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e550e54

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   129,596,354   129,596,292   7 HPFS/NTFS
/dev/sda2         147,171,465   234,436,544    87,265,080   5 Extended
/dev/sda5         147,171,591   151,460,819     4,289,229  82 Linux swap / Solaris
/dev/sda6         151,460,883   179,751,284    28,290,402  83 Linux
/dev/sda7         179,751,348   198,177,839    18,426,492  83 Linux
/dev/sda8         198,177,903   202,274,414     4,096,512  82 Linux swap / Solaris
/dev/sda9         202,274,478   234,436,544    32,162,067  83 Linux
/dev/sda3         129,596,355   147,171,464    17,575,110  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        56B09B48B09B2D8D                       ntfs       New old Dell laptop    

#Debian root part#       
[COLOR=Red]**/dev/sda3        eb7d1b5b-9dae-414a-b77e-0cb6f3c0ff61   ext3       9.0 GB Filesyste**[/COLOR]
              
/dev/sda5                                               swap                                     
/dev/sda6        37837804-fc55-4dbc-aa13-08b08bc89b79   ext3

#Ubuntu root part  #                                   
[COLOR=Red]**/dev/sda7        a3cc4cdd-c80d-48c0-be69-071e7366b6ef   ext3       ubuntu root**[/COLOR]   

                
/dev/sda8        b6a7e78e-5ddb-47da-b80c-8114b200d7e7   swap       swap                          
/dev/sda9        b8cd9e96-901d-45c2-9f3a-0329b8b7babf   ext3       ubuntu home                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,errors=remount-ro)
/dev/sda9        /home                    ext3       (rw)


================================ sda1/boot.ini: ================================

[COLOR=Red][boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn [/COLOR]

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set a3cc4cdd-c80d-48c0-be69-071e7366b6ef
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a3cc4cdd-c80d-48c0-be69-071e7366b6ef
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=a3cc4cdd-c80d-48c0-be69-071e7366b6ef ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a3cc4cdd-c80d-48c0-be69-071e7366b6ef
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=a3cc4cdd-c80d-48c0-be69-071e7366b6ef ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a3cc4cdd-c80d-48c0-be69-071e7366b6ef
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a3cc4cdd-c80d-48c0-be69-071e7366b6ef ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a3cc4cdd-c80d-48c0-be69-071e7366b6ef
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a3cc4cdd-c80d-48c0-be69-071e7366b6ef ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 56b09b48b09b2d8d
    drivemap -s (hd0) ${root}
    chainloader +1
}
[COLOR=Red][B]menuentry "Debian GNU/Linux (5.0.4) (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set eb7d1b5b-9dae-414a-b77e-0cb6f3c0ff61
    linux /boot/vmlinuz-2.6.26-2-686 root=/dev/sda3
    initrd /boot/initrd.img-2.6.26-2-686[/B][/COLOR]
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=a3cc4cdd-c80d-48c0-be69-071e7366b6ef /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=b8cd9e96-901d-45c2-9f3a-0329b8b7babf /home           ext3    defaults        0       2
/dev/sda5       none            swap    sw              0       0
# swap was on /dev/sda8 during installation
UUID=b6a7e78e-5ddb-47da-b80c-8114b200d7e7 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  99.8GB: boot/grub/core.img
  99.8GB: boot/grub/grub.cfg
  99.8GB: boot/initrd.img-2.6.31-14-generic
 100.0GB: boot/initrd.img-2.6.31-20-generic
  99.8GB: boot/vmlinuz-2.6.31-14-generic
 100.0GB: boot/vmlinuz-2.6.31-20-generic
 100.0GB: initrd.img
  99.8GB: initrd.img.old
 100.0GB: vmlinuz
  99.8GB: vmlinuz.old

#Debian root part#
[COLOR=Red][B]=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc3       /               ext3    errors=remount-ro 0       1
/dev/hdc6       /home           ext3    defaults        0       2
/dev/hdc5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0[/B][/COLOR]

=================== sda3: Location of files loaded by Grub: ===================


  66.9GB: boot/initrd.img-2.6.26-2-686
  67.0GB: boot/initrd.img-2.6.26-2-686.bak
  66.9GB: boot/vmlinuz-2.6.26-2-686
  66.9GB: initrd.img
  66.9GB: vmlinuz

---

