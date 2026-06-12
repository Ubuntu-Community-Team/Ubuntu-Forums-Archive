---
title: "Ubuntu Grub2 problem"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by c.a on 2011-02-19
Hello and thank you in advance to anyone who takes the time to read and/or help.

I have a netbook Samsung N150.  Came loaded with Win7 Starter.  I loaded Ubuntu 10.10 on it and it worked fine until about a week ago when by mistake I guess I pressed F4 which starts the recovery software from Samsung.

I rebooted the machine and I got a black screen with a cursor blinking in the upper left hand side of the screen.

I followed the directions to re-install grub2 onto the HDD:

I used a USB live version of ubuntu and mounted the ubuntu hdd which happes to be SDA6
and went to the boot directory and found (confirmed) that I was going to recover grub2

I followed the directions in this link:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Everything works as noted in the document above but when I reboot the machine what I get is no longer the same blank screen.  It is slightly different, the cursor blinking on the upper left hand side happens to be twice as wide as before.

I tried holding the shift key while booting to see grub but for about a second is says:
Loading GRUB and then the black screen with the cursor blinking on the upper left hand side comes up.

I also used an external CDROM to erase the MBR with the fdisk command to see if that would bring back the win boot loader and then I would attempt to install grub again but the same result with the blank screen happened.

Any idea as to what I am doing wrong or if I missing something?
i installed GRUB to /dev/sda but my ubuntu install is /dev/sda6 and I got a warning not to do it to sda6 because it was an unreliable method.

Any help will be greatly appreciated.

---

### Post by Quackers on 2011-02-19
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by c.a on 2011-02-19
Here it is, thank you for replying so promptly.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

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
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    31,459,327    31,457,280  27 Hidden HPFS/NTFS
/dev/sda2    *     31,459,328    31,664,127       204,800   7 HPFS/NTFS
/dev/sda3          31,664,128   138,409,983   106,745,856   7 HPFS/NTFS
/dev/sda4         138,412,031   312,576,704   174,164,674   f W95 Ext d (LBA)
/dev/sda5         138,412,032   210,178,047    71,766,016   7 HPFS/NTFS
/dev/sda6         210,178,458   308,303,414    98,124,957  83 Linux
/dev/sda7         308,303,478   312,576,704     4,273,227  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1040 MB, 1040187392 bytes
32 heads, 62 sectors/track, 1024 cylinders, total 2031616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     2,031,615     2,031,554   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3ECEB5DDCEB58DA1                       ntfs       RECOVERY                      
/dev/sda2        766AB6F96AB6B4E9                       ntfs       SYSTEM                        
/dev/sda3        CC00B90700B8F992                       ntfs                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        CC9AD3A99AD38DF8                       ntfs       New Volume                    
/dev/sda6        137234cf-304a-4387-ae02-0da99d470147   ext4                                     
/dev/sda7        427337bd-49ab-4d6a-94de-e6d1f577f0a7   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        346E-B618                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=137234cf-304a-4387-ae02-0da99d470147 ro   quiet splash intel_idle.max_cstate=0
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=137234cf-304a-4387-ae02-0da99d470147 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=137234cf-304a-4387-ae02-0da99d470147 ro   quiet splash intel_idle.max_cstate=0
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=137234cf-304a-4387-ae02-0da99d470147 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=137234cf-304a-4387-ae02-0da99d470147 ro   quiet splash intel_idle.max_cstate=0
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=137234cf-304a-4387-ae02-0da99d470147 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=137234cf-304a-4387-ae02-0da99d470147 ro   quiet splash intel_idle.max_cstate=0
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=137234cf-304a-4387-ae02-0da99d470147 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=137234cf-304a-4387-ae02-0da99d470147 ro   quiet splash intel_idle.max_cstate=0
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=137234cf-304a-4387-ae02-0da99d470147 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=137234cf-304a-4387-ae02-0da99d470147 ro   quiet splash intel_idle.max_cstate=0
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    echo    'Loading Linux 2.6.31-22-generic ...'
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=137234cf-304a-4387-ae02-0da99d470147 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 137234cf-304a-4387-ae02-0da99d470147
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3eceb5ddceb58da1
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 766ab6f96ab6b4e9
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=137234cf-304a-4387-ae02-0da99d470147 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=427337bd-49ab-4d6a-94de-e6d1f577f0a7 none            swap    sw              0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 107.8GB: boot/grub/core.img
 114.5GB: boot/grub/grub.cfg
 126.1GB: boot/initrd.img-2.6.31-22-generic
 126.8GB: boot/initrd.img-2.6.32-25-generic
 116.9GB: boot/initrd.img-2.6.35-22-generic
 115.8GB: boot/initrd.img-2.6.35-23-generic
 117.6GB: boot/initrd.img-2.6.35-24-generic
 115.9GB: boot/initrd.img-2.6.35-25-generic
 109.7GB: boot/vmlinuz-2.6.31-22-generic
 120.8GB: boot/vmlinuz-2.6.32-25-generic
 118.3GB: boot/vmlinuz-2.6.35-22-generic
 108.9GB: boot/vmlinuz-2.6.35-23-generic
 108.8GB: boot/vmlinuz-2.6.35-24-generic
 108.8GB: boot/vmlinuz-2.6.35-25-generic
 115.9GB: initrd.img
 117.6GB: initrd.img.old
 108.8GB: vmlinuz
 108.8GB: vmlinuz.old
```

---

### Post by c.a on 2011-03-10
Hello.  Bump for me.  I was away for a bit so I was unable to follow up.  I posted the information I was asked to post.  Anyone have any idea what could be keeping me from booting?

Thanks in advanced.

---

