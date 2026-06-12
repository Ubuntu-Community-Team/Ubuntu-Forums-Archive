---
title: "Problems with Vista &amp; Ubuntu"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by rjg2bucks on 2010-03-14
Hi
I would really appreciate some help in resolving the situation, I have created. I recently installed ubuntu onto a pc running MS vista. Then I somehow managed to install a second instance of ubuntu. Both of these were on the (drive e:)
Then because of HDD problems, I had to reformat my original drive with MS Vista (drive C). Because of installation problems with ms vista - I ended up installing it onto the drive e: also. But now I can no longer load ubuntu because the "GRUB" loader is missing.
So my questions are:
1: How can I restore the "GRUB" loader? So I can access ubuntu again
2: How can I remove/uninstall the second ubuntu installation?
3: Is it possible to have a triple boot system with ms vista / ubuntu 32-bit / ubuntu 64-bit?
Sorry for any technically incorrect usage, but I'm a newbiw with ubuntu.
Thanks in advance

---

### Post by stilling on 2010-03-14
i amnot an expert but why don`t you format your hard drive install vista again clean install on drive c: and install Virtual Box and install ubuntu 32 `64 and other system that you whant and even use all 3 of them in the same time a little help for Virtual box you can find on the website
[http://www.virtualbox.org](http://www.virtualbox.org)

---

### Post by presence1960 on 2010-03-14
You can multiple boot. You probably don't have to reinstall anything. Need more info.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by rjg2bucks on 2010-03-14
Thanks for your help. I did as you requested and the the contents of RESULTS.Txt are:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=d6ccf972-664f-4537-9873-3b13e79a8887)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: _________________________________________________________________________

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c39bccd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   268,412,927   268,410,880   7 HPFS/NTFS
/dev/sda2         268,414,020   488,392,064   219,978,045   f W95 Ext d (LBA)
/dev/sda5         268,414,083   488,392,064   219,977,982   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x06cefe95

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,152,358,514 1,152,358,452   7 HPFS/NTFS
/dev/sdb2       1,152,358,515 1,160,166,104     7,807,590  82 Linux swap / Solaris
/dev/sdb3       1,160,166,105 1,250,258,624    90,092,520   5 Extended
/dev/sdb5       1,160,166,168 1,179,701,144    19,534,977  83 Linux
/dev/sdb6       1,179,701,208 1,218,642,704    38,941,497  83 Linux
/dev/sdb7       1,218,642,768 1,248,844,904    30,202,137  83 Linux
/dev/sdb8       1,248,844,968 1,250,258,624     1,413,657  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        502C47C12C47A0B8                       ntfs                                     
/dev/sda5        F86066F46066B8D0                       ntfs       Disk_2                        
/dev/sdb1        6C18596818593276                       ntfs       Big Disk_3                    
/dev/sdb2        9945a530-1c25-4fde-bc1b-ebe49d82721b   swap                                     
/dev/sdb5        d6ccf972-664f-4537-9873-3b13e79a8887   ext4                                     
/dev/sdb6        50e180ea-0d47-415c-9ed2-d2c4466f44fb   ext4                                     
/dev/sdb7        a2604d88-a26f-448d-a5c5-fb574ec0754f   ext4                                     
/dev/sdb8        b0f79ada-1d95-4c93-b5cf-cf0c44dd9913   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
search --no-floppy --fs-uuid --set d6ccf972-664f-4537-9873-3b13e79a8887
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
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set d6ccf972-664f-4537-9873-3b13e79a8887
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=d6ccf972-664f-4537-9873-3b13e79a8887 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set d6ccf972-664f-4537-9873-3b13e79a8887
    linux    /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=d6ccf972-664f-4537-9873-3b13e79a8887 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set d6ccf972-664f-4537-9873-3b13e79a8887
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=d6ccf972-664f-4537-9873-3b13e79a8887 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set d6ccf972-664f-4537-9873-3b13e79a8887
    linux    /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=d6ccf972-664f-4537-9873-3b13e79a8887 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic-pae
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3250af8b50af547f
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
UUID=d6ccf972-664f-4537-9873-3b13e79a8887 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=50e180ea-0d47-415c-9ed2-d2c4466f44fb /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=9945a530-1c25-4fde-bc1b-ebe49d82721b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 597.2GB: boot/grub/core.img
 599.3GB: boot/grub/grub.cfg
 597.2GB: boot/initrd.img-2.6.31-19-generic-pae
 598.3GB: boot/initrd.img-2.6.31-20-generic-pae
 596.6GB: boot/vmlinuz-2.6.31-19-generic-pae
 598.2GB: boot/vmlinuz-2.6.31-20-generic-pae
 598.3GB: initrd.img
 597.2GB: initrd.img.old
 598.2GB: vmlinuz
 596.6GB: vmlinuz.old

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set a2604d88-a26f-448d-a5c5-fb574ec0754f
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
    search --no-floppy --fs-uuid --set a2604d88-a26f-448d-a5c5-fb574ec0754f
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=a2604d88-a26f-448d-a5c5-fb574ec0754f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2604d88-a26f-448d-a5c5-fb574ec0754f
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=a2604d88-a26f-448d-a5c5-fb574ec0754f ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2604d88-a26f-448d-a5c5-fb574ec0754f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a2604d88-a26f-448d-a5c5-fb574ec0754f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2604d88-a26f-448d-a5c5-fb574ec0754f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=a2604d88-a26f-448d-a5c5-fb574ec0754f ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (on /dev/sdb5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d6ccf972-664f-4537-9873-3b13e79a8887
    linux /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=d6ccf972-664f-4537-9873-3b13e79a8887 ro quiet splash
    initrd /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-20-generic-pae (recovery mode) (on /dev/sdb5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d6ccf972-664f-4537-9873-3b13e79a8887
    linux /boot/vmlinuz-2.6.31-20-generic-pae root=UUID=d6ccf972-664f-4537-9873-3b13e79a8887 ro single
    initrd /boot/initrd.img-2.6.31-20-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (on /dev/sdb5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d6ccf972-664f-4537-9873-3b13e79a8887
    linux /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=d6ccf972-664f-4537-9873-3b13e79a8887 ro quiet splash
    initrd /boot/initrd.img-2.6.31-19-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-19-generic-pae (recovery mode) (on /dev/sdb5)" {
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set d6ccf972-664f-4537-9873-3b13e79a8887
    linux /boot/vmlinuz-2.6.31-19-generic-pae root=UUID=d6ccf972-664f-4537-9873-3b13e79a8887 ro single
    initrd /boot/initrd.img-2.6.31-19-generic-pae
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb7 during installation
UUID=a2604d88-a26f-448d-a5c5-fb574ec0754f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=b0f79ada-1d95-4c93-b5cf-cf0c44dd9913 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb7: Location of files loaded by Grub: ===================


 627.3GB: boot/grub/core.img
 627.3GB: boot/grub/grub.cfg
 624.7GB: boot/initrd.img-2.6.31-14-generic
 627.4GB: boot/initrd.img-2.6.31-20-generic
 626.0GB: boot/vmlinuz-2.6.31-14-generic
 626.9GB: boot/vmlinuz-2.6.31-20-generic
 627.4GB: initrd.img
 624.7GB: initrd.img.old
 626.9GB: vmlinuz
 626.0GB: vmlinuz.old

---

### Post by presence1960 on 2010-03-14
Boot the ubuntu Live CD & choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
sudo mount /dev/sdb7 /mnt
```This will mount your 64 bit ubuntu / partition. next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

When completed reboot without the Live CD & go into BIOS. make sure the sdb (640 GB) disk is set to first in the hard disk boot order. Save changes to CMOS and continue booting into ubuntu. When the desktop loads open a terminal and run ```
sudo dpkg-reconfigure grub-pc
```Just hit enter on each window until you get to the window where you can choose where to put GRUB sda or sdb. Use the arrow keys to navigate and the space bar to select/deselect. Deselect sda and select sdb. Use Tab to highlight Ok and hit Enter. This will insure all grub-pc (GRUB 2) updates go to MBR of sdb.

One more thing: run in terminal ```
sudo update-grub
```All your OSs should now be in the GRUB menu when you boot.

---

### Post by rjg2bucks on 2010-03-15
> **presence1960 said:**
> Boot the ubuntu Live CD & choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
sudo mount /dev/sdb7 /mnt
```This will mount your 64 bit ubuntu / partition. next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```When completed reboot without the Live CD & go into BIOS. make sure the sdb (640 GB) disk is set to first in the hard disk boot order. Save changes to CMOS and continue booting into ubuntu. When the desktop loads open a terminal and run ```
sudo dpkg-reconfigure grub-pc
```Just hit enter on each window until you get to the window where you can choose where to put GRUB sda or sdb. Use the arrow keys to navigate and the space bar to select/deselect. Deselect sda and select sdb. Use Tab to highlight Ok and hit Enter. This will insure all grub-pc (GRUB 2) updates go to MBR of sdb.

[I]One more thing: run in terminal ```
sudo update-grub
```All your OSs should now be in the GRUB menu when you boot.

Thanks for your help. I have not yet installed Ubuntu 64-bit on the pc. I have 2 copies of Ubuntu 32-bit installed on the same HDD. I would like to remove the newer of the two installations (installed by mistake) and then install Ubuntu 64 bit.[/I]

---

