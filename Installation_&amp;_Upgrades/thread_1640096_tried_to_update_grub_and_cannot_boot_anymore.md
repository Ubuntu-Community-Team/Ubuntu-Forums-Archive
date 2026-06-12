---
title: "tried to update grub and cannot boot anymore"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by joene1 on 2010-12-07
Hey guys
I have Windows 7 installed on my ASUS notebook. A little while ago I used the Wubi installer to install Ubuntu 10.10 as a dual-boot system next to Windows. Everything worked fine till now. 
Yesterday I was logged in my Ubuntu system and I installed everything the update manager advised me to, including something about grub (I don't really remember what it was, I just clicked ok...). It then told me to restart. I chose to restart later. When I decided to shut down my computer a little later, the shutdown never seemed to end. So I pressed the power bottom of my computer until the screen went black. Usually this is not a problem, the system will just boot again but this time (probably due to the unfinished changes to grub), it didn't work. 
Now every time I boot my computer, I cannot chose the operating system anymore. The only thing there is is the error message:-ae[INDENT]error: no such device: 06799143-7350-4157-81a4-2d28eo3c6a39
grub rescue>
[/INDENT]Following instructions of [this website]("http://bootinfoscript.sourceforge.net/") I have the output of the boot_info_script and don't really know what to do with it:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfb6b29d9

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,715,903    30,713,856  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     30,715,904   519,102,463   488,386,560   7 HPFS/NTFS
/dev/sda3         519,102,464   976,771,071   457,668,608   f W95 Ext d (LBA)
/dev/sda5         519,104,512   976,771,071   457,666,560   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4026 MB, 4026531840 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00049da6

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,389,899     7,389,837  83 Linux
/dev/sdb2           7,389,900     7,855,784       465,885   5 Extended
/dev/sdb5           7,389,963     7,855,784       465,822  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       06799143-7350-4157-81a4-2d28e03c6a39   ext4                                     
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        B6ECDE74ECDE2DFD                       ntfs       OS                            
/dev/sda5        FA2EE1802EE135F3                       ntfs       DATA                          
/dev/sdb1        cace153e-44e4-4013-87d8-b55f62067e6f   ext4                                     
/dev/sdb5        2cf4eda0-c6c9-4352-9f2c-0b97a7ba5941   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set cace153e-44e4-4013-87d8-b55f62067e6f
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
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set cace153e-44e4-4013-87d8-b55f62067e6f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=cace153e-44e4-4013-87d8-b55f62067e6f ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set cace153e-44e4-4013-87d8-b55f62067e6f
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=cace153e-44e4-4013-87d8-b55f62067e6f ro single 
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=cace153e-44e4-4013-87d8-b55f62067e6f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=2cf4eda0-c6c9-4352-9f2c-0b97a7ba5941 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.4GB: boot/grub/core.img
   2.4GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.31-14-generic
   2.4GB: boot/vmlinuz-2.6.31-14-generic
    .8GB: initrd.img
   2.4GB: vmlinuz
```Do you now if there's still hope for my system. 
I'm thinking about just installing everything new (windows and ubuntu).
Thanks so much for your help!
joene1

---

### Post by drs305 on 2010-12-07
joene1,

Welcome to the Ubuntu forums. No need to reinstall everything.

The results show you have a wubi install on sda and another Ubuntu install on sdb. We'll deal with the ability to boot Windows. Grub2 was installed on your Windows MBR, which overwrote the ability to boot Windows. To restore the Windows bootloader quickly, from the Ubuntu LiveCD, you can run this command. Don't worry about the messages about lilo as they only apply if you are fully installing lilo (which you aren't).

From the LiveCD, open a terminal (Applications, Accessories, Terminal):
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Reboot and you should be able to boot Windows. Then try booting Wubi and see if you can do that as well.

Forum member *Rubi1200* has just posted an excellent thread on Wubi problems which will help you if the above doesn't solve things.
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by oldfred on 2010-12-07
Certainly do everything drs305 recommends.

If you boot your sdb drive, the 4GB flash? drive does it boot? It looks like you have a full install in the 4GB drive. That is tight but will work if you do not install much and houseclean regularly. Running this may find your windows also, if it boots:

sudo update-grub

---

### Post by joene1 on 2010-12-07
Thanks guys, 
that sounds great. I'm now working on a usb stick which does have a full ubuntu installation. I suppose that's what you meant.
I gonna try your solution now...
lg

---

### Post by joene1 on 2010-12-07
Awesome!
I did exactly what you guys told me and it worked even better. When I boot now, I can choose the os just as I used to! No need to run Wubi again. As far as I see now, there is nothing different from what it used to be.
So thanks a lot
joene1

---

