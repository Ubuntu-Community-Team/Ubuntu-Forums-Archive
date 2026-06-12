---
title: "Grub No Longer Active!"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by freesparks on 2010-11-17
Hello All,

   I recently upgraded a laptop that already had Ubuntu 9.04 and Windows partitioned on it's internal hard drive and upgraded the Windows partition to Windows XP Professional.  Well, everything went well on the Windows side, but in doing so the upgrade erased Grub version 1.92 and now I just have the regular Windows start up screen.  And, I am pretty sure that during the installation Windows installed itself on (hd0) or /dev/sda, all I need to know is if I am to resolve this by first booting with the Ubuntu 9.04 disk and then edit the Grub Menu list file, and what to change it to specifically so that Grub is the first to boot.  I also am sure that I did not install Windows Professional over the Ubuntu 9.04 install because I used the Disk Utility in Windows and the 3 Ubuntu partitions, (swap, root, and home) are still there.  Any help on this would be greatly appreciated.

Best Regards,

freesparks

---

### Post by freesparks on 2010-11-17
Hello All,

   This is my output for when I boot from the Ubuntu 9.04 install cd:

>  sudo fdisk -lI get this:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        5105    40957717+   7  HPFS/NTFS
/dev/sda3            5106        9274    33487492+   5  Extended
/dev/sda4            9275        9729     3654787+  db  CP/M / CTOS / ...
/dev/sda5            5106        6807    13671283+  83  Linux
/dev/sda6            6808        8909    16884283+  83  Linux
/dev/sda7            8910        9274     2931831   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

/dev/sda2 is where Windows XP Professional is installed.

---

### Post by sikander3786 on 2010-11-17
You need to re-install Grub as it has been wiped out by Windows.

But it would better to post the output of bootinfoscript as per instructions here as it would give us a better idea of what-is-where and therefore advise accordingly.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Please wrap your output with proper code tags # from post menu.

**[COLOR="Red"]Edit:[/COLOR]** And 9.04 is no longer supported. It would be better to do a clean install with 10.04 or 10.10, if there is not a lot of settings/data involved.

---

### Post by freesparks on 2010-11-17
Hello sikander3786,

Thanks so much for the quick reply!!

As you advised,

This is my output from the results.txt file:

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390    82,011,824    81,915,435   7 HPFS/NTFS
/dev/sda3          82,011,825   148,986,809    66,974,985   5 Extended
/dev/sda5          82,011,888   109,354,454    27,342,567  83 Linux
/dev/sda6         109,354,518   143,123,084    33,768,567  83 Linux
/dev/sda7         143,123,148   148,986,809     5,863,662  82 Linux swap / Solaris
/dev/sda4         148,986,810   156,296,384     7,309,575  db CP/M / CTOS / ...


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D5-0406                              vfat       DellUtility                   
/dev/sda2        04A0EA13A0EA0B4E                       ntfs                                     
/dev/sda4                                               vfat       DellRestore                   
/dev/sda5        ac86e7ee-48f4-4682-ba18-c1d3349df988   ext4                                     
/dev/sda6        57effbbc-93e4-4151-9fa8-d4b74932f4f6   ext4                                     
/dev/sda7        83d2af15-c581-4e74-a7d6-2e7ca740d3e8   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda5        /media/ac86e7ee-48f4-4682-ba18-c1d3349df988 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda6        /media/57effbbc-93e4-4151-9fa8-d4b74932f4f6 ext4       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda2        /media/04A0EA13A0EA0B4E  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS2 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS2="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set ac86e7ee-48f4-4682-ba18-c1d3349df988
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ac86e7ee-48f4-4682-ba18-c1d3349df988
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=ac86e7ee-48f4-4682-ba18-c1d3349df988 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ac86e7ee-48f4-4682-ba18-c1d3349df988
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=ac86e7ee-48f4-4682-ba18-c1d3349df988 ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ac86e7ee-48f4-4682-ba18-c1d3349df988
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ac86e7ee-48f4-4682-ba18-c1d3349df988 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set ac86e7ee-48f4-4682-ba18-c1d3349df988
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ac86e7ee-48f4-4682-ba18-c1d3349df988 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 04a0ea13a0ea0b4e
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=ac86e7ee-48f4-4682-ba18-c1d3349df988 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=57effbbc-93e4-4151-9fa8-d4b74932f4f6 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=83d2af15-c581-4e74-a7d6-2e7ca740d3e8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  45.9GB: boot/grub/core.img
  45.9GB: boot/grub/grub.cfg
  42.8GB: boot/initrd.img-2.6.31-14-generic
  45.9GB: boot/initrd.img-2.6.31-22-generic
  45.0GB: boot/vmlinuz-2.6.31-14-generic
  42.9GB: boot/vmlinuz-2.6.31-22-generic
  45.9GB: initrd.img
  42.8GB: initrd.img.old
  42.9GB: vmlinuz
  45.0GB: vmlinuz.old

---

### Post by sikander3786 on 2010-11-17
So you are using 9.10. I thought it was 9.04 :-)

Boot from your Live CD of 9.10 or higher. Go to terminal and type these commands,

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot and you should be able to boot into Ubuntu. If Windows doesn't show up in the Grub menu, from Ubuntu, try this command.

```
sudo update-grub
```

And you should be dual boot now.

---

### Post by freesparks on 2010-11-17
Hello sikander3786,

   That was excellent!!  It worked perfectly.  After many attempts, I failed to install 10.04, for some reason, it does not work on this machine.  I tried posting to get some resolution, however no one replied.  My guess is that its a hardware/operating issue, most likely driver related.  The only thing now that seems to be quirky is the sound drivers.  I'm gonna try to dive into that today.  Anyway, thanks so much for the quick reply.  

Best Regards,

freesparks

---

### Post by sikander3786 on 2010-11-17
You are Welcome :-)

Please mark the thread Solved using [COLOR="Red"]**Thread Tools**[/COLOR] near the top of the page.

Happy Ubuntu-ing!

---

