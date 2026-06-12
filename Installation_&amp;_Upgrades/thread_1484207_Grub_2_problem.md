---
title: "Grub 2 problem"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by Virgil51 on 2010-05-15
Hey there,
Relatively new user of ubuntu here.
I tried installing Lucid on a separate hard drive to my Win 7 x64 installation remembering that same process working with jaunty however even though the installation went fine, my computer stopped after it was done listing my pci devices(at the point where it would normally load grub) and just sat there with the white underscore flashing. Presumably because something was wrong with my grub install and my windows loader had been removed. 
I tried booting from my windows cd and running startup repair to no avail.
I then tried booting off a live Lucid CD and manually installing grub 2 with the advice from the tips and tricks section to no avail.

Eventually i formatted all my drives with my windows 7 disk and all is well again.So thinking that it was my lucid cd that was wrong i then install karmic side by side with my windows on the same hd(installation goes over with no errors). However now it ignores my karmic installation and boots into windows without grub again.
Leaving me with the only conclusion that my installation of grub 2 is to blame. Any help would be appreciated.
Thx

---

### Post by kio_http on 2010-05-15
Your installation of lucid 10.04 was good. Its just that you have a copy of the initial "final" release. A bug concerning this was detected and he iso recreated. To fix this just use the 10.04 cd. If its not detected after, Open terminal

Applications Menu > Accessories > Terminal

Type and then press enter

```
sudo update-grub2
```

---

### Post by Virgil51 on 2010-05-15
Thanks for the quick reply, I'll try this.

---

### Post by dino99 on 2010-05-15
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Virgil51 on 2010-05-15
> **kio_http said:**
> Your installation of lucid 10.04 was good. Its just that you have a copy of the initial "final" release. A bug concerning this was detected and he iso recreated. To fix this just use the 10.04 cd. If its not detected after, Open terminal

Applications Menu > Accessories > Terminal

Type and then press enter

```
sudo update-grub2
```

Hey, newbie at large again but when i try to run that it gives me a "grub probe error cannot find a device for /"
I'm assuming this is because I'm leaving out something from the command such as the partition or hd to be updated?

---

### Post by oldfred on 2010-05-15
Lets see where you currently have everything:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by Virgil51 on 2010-05-15
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr /ntldr

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xac3aac3a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,359,034,739 1,359,032,692   7 HPFS/NTFS
/dev/sda2       1,359,034,740 1,465,144,064   106,109,325   5 Extended
/dev/sda5       1,359,034,803 1,460,710,124   101,675,322  83 Linux
/dev/sda6       1,460,710,188 1,465,144,064     4,433,877  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8341ccaf

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
164 heads, 19 sectors/track, 50160 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000658f7

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8074484F74484A5C                       ntfs                                     
/dev/sda5        0061f749-a2ab-472a-8bff-8cf2e7b0607b   ext4                                     
/dev/sda6        5f44a843-9c2f-4c17-848d-5b9a3f608273   swap                                     
/dev/sdb1        1A4EECAD75B40B41                       ntfs                                     
/dev/sdc1        F66A45546A4512B3                       ntfs       System Reserved               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


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
search --no-floppy --fs-uuid --set 0061f749-a2ab-472a-8bff-8cf2e7b0607b
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
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0061f749-a2ab-472a-8bff-8cf2e7b0607b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0061f749-a2ab-472a-8bff-8cf2e7b0607b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 0061f749-a2ab-472a-8bff-8cf2e7b0607b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=0061f749-a2ab-472a-8bff-8cf2e7b0607b ro single 
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
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 1a4eecad75b40b41
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set f66a45546a4512b3
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
UUID=0061f749-a2ab-472a-8bff-8cf2e7b0607b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5f44a843-9c2f-4c17-848d-5b9a3f608273 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 699.2GB: boot/grub/core.img
 699.5GB: boot/grub/grub.cfg
 696.3GB: boot/initrd.img-2.6.31-14-generic
 696.3GB: boot/vmlinuz-2.6.31-14-generic
 696.3GB: initrd.img
 696.3GB: vmlinuz
```
thats it there.
Thanks again for any help.

---

### Post by kansasnoob on 2010-05-15
Is the 750GB drive set to boot first in BIOS?

---

### Post by Virgil51 on 2010-05-15
My boot prioty lists simply "hard drive" as the first to boot however the 750 gig one is listed as master 0 in the standard cmos section.

---

### Post by oldfred on 2010-05-15
In my system primary master is the boot drive, so I would think master 0 is yours unless grub sees the drives in a different order?
If you are directly booting windows then sdc has to be the drive booting. You have a win7 boot partition of 100MB in sdc but your install is in sda which is unusual.

Try changing boot drives in BIOS, sda the 750 should give you grub2  and boot, sdb the 500 is a grub that now does nothing so is should crash, and sdc is windows.

---

### Post by darkod on 2010-05-15
> **Virgil51 said:**
> My boot prioty lists simply "hard drive" as the first to boot however the 750 gig one is listed as master 0 in the standard cmos section.

I know it sounds like stupid question, but try taking a better look in the BIOS. Most newer boards (and that's years ago) started having separate setting to list hdds in preferred order.
Because with multiple hdds having HDD first in device priority is not enough information. You should be able to select in which orders you want your hdds to be checked for bootloader.
Otherwise, the assumption that Master 0 would be first is logical, but who knows.

PS. You could try installing grub2 to all disks, most importantly to /dev/sdb, the 500GB disk. Because that disk has some old grub1 on it, with no config files to continue loading. Exactly that would show you a cursor and stop because it has nothing to load. If I'm not mistaken...

---

### Post by Virgil51 on 2010-05-16
> **darkod said:**
> 

PS. You could try installing grub2 to all disks, most importantly to /dev/sdb, the 500GB disk. Because that disk has some old grub1 on it, with no config files to continue loading. Exactly that would show you a cursor and stop because it has nothing to load. If I'm not mistaken...
Would you mind explaining to me how that can be done?
Thx.

---

### Post by drs305 on 2010-05-16
> **Virgil51 said:**
> Would you mind explaining to me how that can be done?
Thx.

One way is with the command:
```
sudo dpkg-reconfigure grub-pc
```

You would probably want to accept the default entries for the command lines by tabbing to "OK" and then pressing ENTER. When you get to the partition section, use the UP/DN keys to move to *sdb*, use the SPACE bar to select the drive, then tab to "OK" and press ENTER.

Note it is generally not recommended to select specific parittions.

---

### Post by Virgil51 on 2010-05-16
> **oldfred said:**
> 

Try changing boot drives in BIOS, sda the 750 should give you grub2  and boot, sdb the 500 is a grub that now does nothing so is should crash, and sdc is windows.
After a bit more rummaging around in my bios i found the option to change the booting order of my drives and i changed it to the one with lucid on it.It now loads grub 2 fine and loads win7 through grub fine aswell.
Thanks to everyone for the help.

---

