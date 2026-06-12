---
title: "problem with unetbootin install on hard disk"
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by el_carpintero on 2010-11-13
hi. I have been using ubuntu for an year now and I wanted to install it on my second desktop which is an old P-III with no USB boot option in bios and 40gb HDD. The cd drive was also giving problems (not reading the installation cds I created again and again!), so I decided to install it through unetbootin. I have win XP on its first partition (NTFS) and data on 2nd NTFS partition. i made a 1.5gb logical partition as swap and another 10.5gb ext4 partition and tried installing ubuntu- however, it seems unetbootin cannot be used to install ubuntu on same hard disk, even if it is a different partition. with unetbootin, the 1st partition gets mounted as 'cdrom' during install, and i kept on getting the message-"....cannot unmount cdrom..." (which it needs to write the partion information), even though I was not changing the partition during install. Unmounting cdrom manually didnot help. I gave up, I tried unetbootin install by i different way. I attached the hark disk from another desktop that i have (a P-IV) that has windows and ubuntu 10.04 dual boot on it (an 80gb HDD), made this other hard disk as master, and my original 40gb hard disk as slave, and booted. some of the features did not load properly but it did boot into ubuntu, and i was able to install unetbootin ni it. i then installed ubuntu on my "slave" hark disk (the original 40gb one) on its ext4 logical partition, with bootloader installed on this hark disk itself. then i removed the 80gb hdd, booted with the original (and only) hdd, and at grub prompt, I manually loaded the kernels:
">root (hd0,7)
>linux /boot/vmlinuz-2.6.*etc.....* root=/dev/sda7
>initrd /bot/initrd.img-2.6.*etc.....*
>boot

and i was able to boot into my ubuntu. once inside, i re-installed grub with grub-install and update commands. it returned no errors.

However, the problem now is- at reboot, i get the grub options menu, but on selecting ubuntu, i get some error message which i cannot read because it stays on screen for a very short period, and then i get the grub prompt. "......minimal bash commands possible...etc etc....,>"
when i manually load the kernels, i easily boot into my ubuntu and have no problems therafter, but on reboot, same problem persists. it even got updates from net and got upgraded from 2.6.32-24-generic to 2.6.32-5-generic, and i thought that with the upgrade, it must have reinstalled the grub2 and problem wuld have solved, but no- at reboot, I get the same message and i have to manually load the kernels. i can post my boot info script if needed. please advise what is wrong now with my installation and how can i correct it.
thanx.

---

### Post by el_carpintero on 2010-11-14
```
 <!--  /* Style Definitions */  p.MsoNormal, li.MsoNormal, div.MsoNormal 	{mso-style-parent:&quot;&quot;; 	margin:0in; 	margin-bottom:.0001pt; 	mso-pagination:widow-orphan; 	font-size:12.0pt; 	font-family:&quot;Times New Roman&quot;; 	mso-fareast-font-family:&quot;Times New Roman&quot;;} p.MsoPlainText, li.MsoPlainText, div.MsoPlainText 	{margin:0in; 	margin-bottom:.0001pt; 	mso-pagination:widow-orphan; 	font-size:10.0pt; 	font-family:&quot;Courier New&quot;; 	mso-fareast-font-family:&quot;Times New Roman&quot;;} @page Section1 	{size:8.5in 11.0in; 	margin:1.0in 65.95pt 1.0in 65.95pt; 	mso-header-margin:.5in; 	mso-footer-margin:.5in; 	mso-paper-source:0;} div.Section1 	{page:Section1;} -->                   Boot Info Script 0.55    dated February 15th, 2010                    

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,100,319    39,100,257   7 HPFS/NTFS
/dev/sda2          39,100,381    78,140,159    39,039,779   f W95 Ext d (LBA)
/dev/sda5          39,100,383    53,449,199    14,348,817   7 HPFS/NTFS
/dev/sda6          53,449,263    56,533,679     3,084,417  82 Linux swap / Solaris
/dev/sda7          56,533,743    78,140,159    21,606,417   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        24CCBA9DCCBA68A6                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8024D71324D70B54                       ntfs                                     
/dev/sda6        bd3b79a4-6bfa-40ab-bc7e-c422c3347558   swap                                     
/dev/sda7        f1842b90-b2fc-4010-b8f8-f7b8251fd9f6   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/24CCBA9DCCBA68A6  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
  timeout=30
  default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
  [operating systems]
  multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
   
  =========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set f1842b90-b2fc-4010-b8f8-f7b8251fd9f6
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set f1842b90-b2fc-4010-b8f8-f7b8251fd9f6
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod ext2
      set root='(hd0,7)'
      search --no-floppy --fs-uuid --set f1842b90-b2fc-4010-b8f8-f7b8251fd9f6
      linux /boot/vmlinuz-2.6.32-25-generic root=UUID=f1842b90-b2fc-4010-b8f8-f7b8251fd9f6 ro   quiet splash
      initrd      /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod ext2
      set root='(hd0,7)'
      search --no-floppy --fs-uuid --set f1842b90-b2fc-4010-b8f8-f7b8251fd9f6
      echo  'Loading Linux 2.6.32-25-generic ...'
      linux /boot/vmlinuz-2.6.32-25-generic root=UUID=f1842b90-b2fc-4010-b8f8-f7b8251fd9f6 ro single 
      echo  'Loading initial ramdisk ...'
      initrd      /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod ext2
      set root='(hd0,7)'
      search --no-floppy --fs-uuid --set f1842b90-b2fc-4010-b8f8-f7b8251fd9f6
      linux /boot/vmlinuz-2.6.32-24-generic root=UUID=f1842b90-b2fc-4010-b8f8-f7b8251fd9f6 ro   quiet splash
      initrd      /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
      recordfail
      insmod ext2
      set root='(hd0,7)'
      search --no-floppy --fs-uuid --set f1842b90-b2fc-4010-b8f8-f7b8251fd9f6
      echo  'Loading Linux 2.6.32-24-generic ...'
      linux /boot/vmlinuz-2.6.32-24-generic root=UUID=f1842b90-b2fc-4010-b8f8-f7b8251fd9f6 ro single 
      echo  'Loading initial ramdisk ...'
      initrd      /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
      insmod ext2
      set root='(hd0,7)'
      search --no-floppy --fs-uuid --set f1842b90-b2fc-4010-b8f8-f7b8251fd9f6
      linux16     /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
      insmod ext2
      set root='(hd0,7)'
      search --no-floppy --fs-uuid --set f1842b90-b2fc-4010-b8f8-f7b8251fd9f6
      linux16     /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
      insmod ntfs
      set root='(hd0,1)'
      search --no-floppy --fs-uuid --set 24ccba9dccba68a6
      drivemap -s (hd0) ${root}
      chainloader +1
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=f1842b90-b2fc-4010-b8f8-f7b8251fd9f6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=bd3b79a4-6bfa-40ab-bc7e-c422c3347558 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


  31.4GB: boot/grub/core.img
  37.8GB: boot/grub/grub.cfg
  30.4GB: boot/initrd.img-2.6.32-24-generic
  31.5GB: boot/initrd.img-2.6.32-25-generic
  31.4GB: boot/vmlinuz-2.6.32-24-generic
  31.5GB: boot/vmlinuz-2.6.32-25-generic
  31.5GB: initrd.img
  30.4GB: initrd.img.old
  31.5GB: vmlinuz
  31.4GB: vmlinuz.old
 
  
```

---

### Post by wilee-nilee on 2010-11-14
Thanks for posting the script. I can't really tell what is going on or what you really want. Can you say exactly what your goals are here without the I did this because I wanted this when it isn't relevant.

Use paragraphs when posting, make it easy to help you.;)

The first post is unreadable to me and just confusing to be honest. I don't have the patience to decipher it and I have no learning disabilities. (Detected anyway)

---

### Post by el_carpintero on 2010-11-14
My apologies for that confusing post....

My problem is- on booting, i get the grub options menu, but on  selecting ubuntu, i get some error message which i cannot read because  it stays on screen for a very short period, and then i get the grub  prompt with "......minimal bash commands possible...etc etc....,>".

By manually loading the kernels, i easily boot into my ubuntu and have  no problems therafter, but on reboot, same problem persists. I have tried re-installing grub but with no effect. At reboot, I  get the same message and i have to manually load the kernels.

Can you figure out why it is not loading by itself?
Thanks for your help...

---

### Post by wilee-nilee on 2010-11-14
Have you run when you manually boot into Lucid.
```
sudo update-grub
```

Except for a lba flag on the extended=sda2 which shouldn't be a problem, really the script looks okay, but I could easily be missing something. generally we try to get group help when we can so maybe a other will step in with some ideas.

---

### Post by wilee-nilee on 2010-11-14
Yesterday I reinstalled W7 on a hard drive that had Maverick on it, I did all the correct procedures, both OS were there. But I could not get grub to load and boot Ubuntu at all I could get was a blank screen. I just used a supergrub disc 1.3 to boot in. I can do it manually but I'm lazy. I ran sudo update-grub and everything loaded and is working now.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

The super grub might tide you over with a easier boot until this is resolved.

---

### Post by el_carpintero on 2010-11-14
dear [wilee-nilee]("http://ubuntuforums.org/member.php?u=906928"), 
Problem solved! after you assured me that my script looked okay, i reistalled my grub again and agin-3 times. got the same error after the first 2 times, but 3 rd time, it somehow worked and my system is now booting fine!!

I just don't know why my system behaved in such an idiosyncratic way, but all's well that ends well....
thanks again for the help and reassurance!

---

### Post by wilee-nilee on 2010-11-14
> **el_carpintero said:**
> dear [wilee-nilee]("http://ubuntuforums.org/member.php?u=906928"), 
Problem solved! after you assured me that my script looked okay, i reistalled my grub again and agin-3 times. got the same error after the first 2 times, but 3 rd time, it somehow worked and my system is now booting fine!!

I just don't know why my system behaved in such an idiosyncratic way, but all's well that ends well....
thanks again for the help and reassurance!

It must be a full moon on mars or something I had never run into this problem myself. I don't think it was grub itself in my case but, something was amiss, glad you got your up and running toooooo.;)

---

