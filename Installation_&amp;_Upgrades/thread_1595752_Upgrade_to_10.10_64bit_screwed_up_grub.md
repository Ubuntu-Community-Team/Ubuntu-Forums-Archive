---
title: "Upgrade to 10.10 64bit screwed up grub"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by u5001 on 2010-10-13
Hi,

until 2 hours ago I had Ubuntu 10.04 64 bit in an encryped LVM installed with seperate /boot partition. The boot partition is the only partition which is not encrypted.

Then I ran the uprade program to upgrade to 10.10 and rebooted.
However, after the reboot I got the error message:

**error: the symbol `grub_xputs` not found**

I then fired up the 10.10 live CD and wanted to reinstall grub using this:[FONT=monospace]
[/FONT]sudo mount /dev/sda1 /mnt[FONT=monospace]
s[/FONT]udo grub-install --root-directory=/mnt /dev/sda

But after i run update-grub I get:


/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Did I kill my Ubuntu?

Please help.

---

### Post by franklamoureux on 2010-10-13
I have the same issue. I found the thread [http://ubuntuforums.org/showthread.php?t=1580752](http://ubuntuforums.org/showthread.php?t=1580752) and tried the steps in [http://ubuntuforums.org/showpost.php?p=9836539&postcount=5](http://ubuntuforums.org/showpost.php?p=9836539&postcount=5), still no luck.

Below is the output of Boot Info Script.

Some info:
- sda is my old XP drive (SATA)
- sdf is my new HD with Ubuntu 10.10 (upgraded from 10.04) (SATA)
- sdb/c/d/e is a 4 in 1 SD card internal reader
- During the upgrade to 10.10, I chose the option to "Keep my current grub settings", as I had done some customization to it (nothing fancy: background image, fonts, screen resolution).
- Using the steps in the second link above, I used /dev/sdf and /dev/sdf5 only.

RESULTS.TXT:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdf and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 17082069 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 17084269 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdf1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              15,120   102,392,639   102,377,520   f W95 Ext d (LBA)
/dev/sda5              15,183   102,392,639   102,377,457   7 HPFS/NTFS
/dev/sda2    *    102,402,048   625,139,711   522,737,664   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63    16,803,989    16,803,927  82 Linux swap / Solaris
/dev/sdf2          16,803,990 1,568,763,314 1,551,959,325   5 Extended
/dev/sdf5          16,804,053    79,698,464    62,894,412  83 Linux
/dev/sdf6          79,698,528   562,114,349   482,415,822  83 Linux
/dev/sdf7         562,114,413 1,558,208,609   996,094,197  83 Linux
/dev/sdf8       1,558,208,673 1,568,763,314    10,554,642  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1: PTTYPE="dos" 
/dev/sda2        2440BABD40BA94D0                       ntfs       Data                          
/dev/sda5        DAA0EBB0A0EB90F5                       ntfs       System                        
/dev/sda: PTTYPE="dos" 
/dev/sdf1        c23e9508-78a4-46cc-8021-56367f5000d4   swap                                     
/dev/sdf2: PTTYPE="dos" 
/dev/sdf5        dd19da89-ed60-451e-bcd0-056769263ae6   ext4                                     
/dev/sdf6        7c628d22-2124-41cb-a06d-b57df51af62c   ext4                                     
/dev/sdf7        16234dd9-9acf-4186-8cce-982115688371   ext4                                     
/dev/sdf8        c1851f41-c308-457c-9da7-a2a271543b87   ext4                                     
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=alwaysoff /fastdetect /usepmtimer /PAE

=========================== sdf5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set dd19da89-ed60-451e-bcd0-056769263ae6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set dd19da89-ed60-451e-bcd0-056769263ae6
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
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set dd19da89-ed60-451e-bcd0-056769263ae6
insmod tga
if background_image /usr/share/images/grub/Windbuchencom.tga ; then
  set color_normal=red/black
  set color_highlight=red/white
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dd19da89-ed60-451e-bcd0-056769263ae6
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dd19da89-ed60-451e-bcd0-056769263ae6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dd19da89-ed60-451e-bcd0-056769263ae6
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dd19da89-ed60-451e-bcd0-056769263ae6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dd19da89-ed60-451e-bcd0-056769263ae6
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=dd19da89-ed60-451e-bcd0-056769263ae6 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set dd19da89-ed60-451e-bcd0-056769263ae6
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=dd19da89-ed60-451e-bcd0-056769263ae6 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 2440babd40ba94d0
    drivemap -s (hd0) ${root}
    chainloader +1
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

=============================== sdf5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=dd19da89-ed60-451e-bcd0-056769263ae6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=16234dd9-9acf-4186-8cce-982115688371 /home           ext4    defaults        0       2
# /opt/vm was on /dev/sda6 during installation
UUID=7c628d22-2124-41cb-a06d-b57df51af62c /opt/vm         ext4    defaults        0       2
# /tmp was on /dev/sda8 during installation
UUID=c1851f41-c308-457c-9da7-a2a271543b87 /tmp            ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=c23e9508-78a4-46cc-8021-56367f5000d4 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdf5: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  19.5GB: boot/grub/grub.cfg
  17.6GB: boot/initrd.img-2.6.32-25-generic
  17.7GB: boot/initrd.img-2.6.35-22-generic
  10.3GB: boot/vmlinuz-2.6.32-25-generic
  14.6GB: boot/vmlinuz-2.6.35-22-generic
  17.7GB: initrd.img
  17.6GB: initrd.img.old
  14.6GB: vmlinuz
  10.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

[COLOR="Red"]**Update**[/COLOR]
I resolved my issue by changing the SATA boot order in the BIOS to boot on new new drive first (see [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/496435"))

My initial boot order was set to 
1. Old drive
2. Externally connected drives
3. New drive

I changed it to
1. New drive
2. Old drive
3. Externally connected drives

Note that this is the SATA boot order, which is different than the boot order (CD, USB, Floppy, HD).
I think one could also swap cables between the two drives, if possible.

---

### Post by eosrei on 2010-10-19
I changed my boot order to boot from the drive I installed 10.10 on, and it started right up. Straight to terminal ran "sudo grub-install /dev/sda" and everything was back to normal. Thanks franklamoureux!

---

### Post by drs305 on 2010-10-19
> **u5001 said:**
> I then fired up the 10.10 live CD and wanted to reinstall grub using this:[FONT=monospace]
[/FONT]sudo mount /dev/sda1 /mnt[FONT=monospace]
s[/FONT]udo grub-install --root-directory=/mnt /dev/sda


Since you have a separate /boot folder, you also have to mount it if you are trying to install Grub2 from the LiveCD. Change X,Y to the appropriate values. This also assumes *sda1* is your Ubuntu installation partition:
```

sudo mount /dev/sda1 /mnt
sudo mount /dev/sd**[COLOR="DarkRed"]XY[/COLOR]** /mnt/boot
```

I don't know if that is the only issue, as I haven't used encrypted partitions/LVM, but make that change and see if the install command now works.

---

