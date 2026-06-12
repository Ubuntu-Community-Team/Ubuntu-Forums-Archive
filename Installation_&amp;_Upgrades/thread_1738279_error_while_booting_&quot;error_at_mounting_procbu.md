---
title: "error while booting &quot;error at mounting /proc/bus/usb&quot;"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by nicolaas3 on 2011-04-24
After upgrading from 9.10 to 10.4 at booting I get everytime the message (translated from Dutch to English) "error at mounting /proc/bus/usb. Press  S to skip mouting or M to manualy fix the problem" :sad:

When I press S, booting goes on and the system is working fine afterwards.

---

### Post by Dutch70 on 2011-04-24
Lets have a look at your boot info script.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags. Do not skip this step or you will lose the formatting & I doubt anyone will look at it.

---

### Post by nicolaas3 on 2011-04-25
Here the content of RESULTS.txt. I hope you can help me further.

```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=47ffcc6d-21cd-4422-96aa-c9a14c42de6e)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Schijf /dev/sda: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    18,434,047    18,432,000  27 Hidden HPFS/NTFS
/dev/sda2    *     18,434,048   340,611,071   322,177,024   7 HPFS/NTFS
/dev/sda4         340,611,072   976,771,119   636,160,048   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Schijf /dev/sdb: 500.1 GB, 500107862016 bytes
255 koppen, 63 sectoren/spoor, 60801 cilinders, totaal 976773168 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Sectorgrootte (logischl/fysiek): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   362,368,054   362,367,992   7 HPFS/NTFS
/dev/sdb2         771,971,445   961,361,729   189,390,285  83 Linux
/dev/sdb3         961,361,730   976,768,064    15,406,335   f W95 Ext d (LBA)
/dev/sdb5         961,361,793   976,768,064    15,406,272  82 Linux swap / Solaris
/dev/sdb4         362,378,205   771,971,444   409,593,240  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        DE7C248F7C24648D                       ntfs       WinRE                         
/dev/sda2        7ED0263FD025FDD1                       ntfs       SYSTEM                        
/dev/sda4        1EBC287CBC285117                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FECC22FDCC22AFB7                       ntfs       000000                        
/dev/sdb2        47ffcc6d-21cd-4422-96aa-c9a14c42de6e   ext4                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb4        9c98f06b-8ad8-48c2-9ef0-f2bcb2e863fc   ext4       linux ext4                    
/dev/sdb5        14990c90-fc64-4c97-ad7a-da831b0fac6b   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=nico)


=========================== sdb2/boot/grub/grub.cfg: ===========================

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
menuentry 'Ubuntu, with Linux 2.6.32-31-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 47ffcc6d-21cd-4422-96aa-c9a14c42de6e
    linux    /boot/vmlinuz-2.6.32-31-generic-pae root=UUID=47ffcc6d-21cd-4422-96aa-c9a14c42de6e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 47ffcc6d-21cd-4422-96aa-c9a14c42de6e
    echo    'Loading Linux 2.6.32-31-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-31-generic-pae root=UUID=47ffcc6d-21cd-4422-96aa-c9a14c42de6e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 47ffcc6d-21cd-4422-96aa-c9a14c42de6e
    linux    /boot/vmlinuz-2.6.31-23-generic-pae root=UUID=47ffcc6d-21cd-4422-96aa-c9a14c42de6e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.31-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 47ffcc6d-21cd-4422-96aa-c9a14c42de6e
    echo    'Loading Linux 2.6.31-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.31-23-generic-pae root=UUID=47ffcc6d-21cd-4422-96aa-c9a14c42de6e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 47ffcc6d-21cd-4422-96aa-c9a14c42de6e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 47ffcc6d-21cd-4422-96aa-c9a14c42de6e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set de7c248f7c24648d
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 7ed0263fd025fdd1
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=47ffcc6d-21cd-4422-96aa-c9a14c42de6e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=14990c90-fc64-4c97-ad7a-da831b0fac6b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=121,devmode=664 0 0

=================== sdb2: Location of files loaded by Grub: ===================


 398.4GB: boot/grub/grub.cfg
 477.9GB: boot/initrd.img-2.6.31-23-generic-pae
 446.7GB: boot/initrd.img-2.6.32-31-generic-pae
 444.5GB: boot/vmlinuz-2.6.31-23-generic-pae
 446.5GB: boot/vmlinuz-2.6.32-31-generic-pae
 446.7GB: initrd.img
 477.9GB: initrd.img.old
 446.5GB: vmlinuz
 444.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
```

---

### Post by Dutch70 on 2011-04-25
```
=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=47ffcc6d-21cd-4422-96aa-c9a14c42de6e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=14990c90-fc64-4c97-ad7a-da831b0fac6b none            swap    sw              0       0
[COLOR="Red"]/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=121,devmode=664 0 0[/COLOR]
```

It looks like it is trying to mount the part in red. Did you use a cd to upgrade? This part is beyond my knowledge to be honest. I'm not sure whether to tell you to delete that, or comment it out by putting a "#" sign in front of /dev/scd0. I'll leave that up to you, unless someone else chimes in. 

If it was mine, I'd try commenting it out first. I don't know why you would ever need that in there, but you can always go back and remove the "#" symbol.

---

### Post by Dutch70 on 2011-04-25
BTW, to edit fstab, use...
```
gksudo gedit /etc/fstab
```

---

### Post by nicolaas3 on 2011-04-27
Thanks Dutch,  it works (commenting out the red lines)

---

### Post by Dutch70 on 2011-04-27
Glad it worked for you. 

Thanks for letting us know & marking the thread solved. :)

---

