---
title: "GRUB 'no such disk' error, dual boot XP"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by Killy01 on 2010-02-07
Well last night I tried to install ubuntu, everything went fine. I installed it by using the live cd, and then just following the prompts on the screen. After the install finished and I rebooted grub came up with an error of "no such disk" so I did some research and tried to fix it myself using this [wiki]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode") entry, which I found on another thread. But that didn't help either. I also ran the shell script that is asked for on most of the GRUB related threads to see if that helps anyone figure it out. The text file says that ubuntu is installed on sdb5, which I *think* translates to hd1,5. However, in the grub recovery mode there is no hd1,5 when I run the ls command, there is only hd0; hd0,1 ; hd1; hd1,0. So does anyone know what is happening? any help would be greatly appreciated, because in the end I had to put the XP disk back in and run fixboot and fixmbr just so I could get the PC in a working state again.
Results of text file below:

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfea0fea0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    80,276,804    80,276,742   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   573,665,084   573,665,022   7 HPFS/NTFS
/dev/sdb2         573,665,085   976,768,064   403,102,980   5 Extended
/dev/sdb5         573,665,148   970,759,754   397,094,607  83 Linux
/dev/sdb6         970,759,818   976,768,064     6,008,247  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1385dc4c

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   312,576,704   312,576,642   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AC94A50D94A4DADA                       ntfs                                     
/dev/sdb1        4848DDC948DDB642                       ntfs       Data                          
/dev/sdb5        81305bee-9595-4bbd-b013-17191fcfd6ab   ext4                                     
/dev/sdb6        dd961095-7c5d-471e-910a-84ed70bc689b   swap                                     
/dev/sdc1        2E01-14F5                              vfat       USB-HDD                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set 81305bee-9595-4bbd-b013-17191fcfd6ab
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
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 81305bee-9595-4bbd-b013-17191fcfd6ab
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=81305bee-9595-4bbd-b013-17191fcfd6ab ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 81305bee-9595-4bbd-b013-17191fcfd6ab
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=81305bee-9595-4bbd-b013-17191fcfd6ab ro single 
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
    search --no-floppy --fs-uuid --set ac94a50d94a4dada
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=81305bee-9595-4bbd-b013-17191fcfd6ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=dd961095-7c5d-471e-910a-84ed70bc689b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 293.7GB: boot/grub/core.img
 293.7GB: boot/grub/grub.cfg
 293.7GB: boot/initrd.img-2.6.31-14-generic
 293.7GB: boot/vmlinuz-2.6.31-14-generic
 293.7GB: initrd.img
 293.7GB: vmlinuz

```


Thanks

James

---

### Post by darkod on 2010-02-07
Try to reinstall grub2 first. Boot with 9.10 cd, Try Ubuntu option, and in terminal execute:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Set in BIOS to boot from /dev/sdb, the 500GB disk. See if that sorted it out.

Maybe it won't, because of this:

=================== sdb5: Location of files loaded by Grub: ===================


 [COLOR=Red]293.7GB[/COLOR]: boot/grub/core.img
 293.7GB: boot/grub/grub.cfg
 293.7GB: boot/initrd.img-2.6.31-14-generic
 293.7GB: boot/vmlinuz-2.6.31-14-generic
 293.7GB: initrd.img
 293.7GB: vmlinuz

If you computer is older, some of the older BIOSes can't read boot files that are beyong 137GB on the hdd. Not sure if this is your case, maybe the grub2 reinstall with the commands above will sort everything out.

---

### Post by presence1960 on 2010-02-07
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

At the GRUB menu highlight the Ubuntu kernel -DO NOT PRESS ENTER-press "e" instead. use the arrow keys to navigate to the ```
search --no-floppy --fs-uuid --set 86d32ee3-aec6-490b-8dab-e5cfff9c7af9
```
 and delete only that. press Ctrl + x to boot ubuntu

Once the desktop loads run in terminal ```
gksudo gedit /usr/lib/grub/grub-mkconfig_lib
```

Scroll down to this:
```

 # If there's a filesystem UUID that GRUB is capable of identifying, use it;
    # otherwise set root as per value in device.map.
    echo "set root=`${grub_probe} --device ${device} --target=drive`"
    if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
       echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
    fi
```

Add a # before the last 3 lines like this:

 ```
# If there's a filesystem UUID that GRUB is capable of identifying, use it;
    # otherwise set root as per value in device.map.
    echo "set root=`${grub_probe} --device ${device} --target=drive`"
    # if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
    # echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
    # fi
```

Click Save on top toolbar & close file. Run in terminal ```
sudo update-grub
```

You should be good to go. reboot & try it.

---

### Post by Killy01 on 2010-02-07
Thanks for the replies.

Darkod - I'll give it a go, thanks for the help, hopefully it will work. Yeah it is quite an old PC. Maybe about 2003-2004 but it might work.

presence1960 - Sorry to be a pain but how do I get to the grub menu? when grub was the bootloader all that was happening was that I was getting the grub recovery system thing. How would I get to the menu?

Thanks

---

### Post by Killy01 on 2010-02-07
Update: Well I tried what 'darkod' said and I think i've moved forward, the error message has come up with saying "no such partition" so i think this means it's found the disk?

---

