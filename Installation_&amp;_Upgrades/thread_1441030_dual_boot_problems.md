---
title: "dual boot problems"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by TXbirder on 2010-03-28
I have a Toshiba netbook.  It came with WinXP Home installed and worked just fine.  I installed UNR, letting the installer automatically repartition the hard drive, allocating about 50% each to XP and UNR.  

When I start the computer I get the GRUB screen.  When I select XP, it tries to start- I get a Microsoft start screen for about 10 seconds, then a quick flash of what might be a Blue Screen of Death and the computer returns to GRUB.

When I select Ubuntu, UNR opens, but sometimes* very slowly*( "Waking up.  Please wait.." for at least a two or three minutes), and works.  UNR startup is unpredictable-  sometimes fast- sometimes slow. 

So I have no access to WinXP now- can't even open it in Safe mode.

John

---

### Post by oldfred on 2010-03-28
So we can be sure of what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by TXbirder on 2010-03-29
I can't get the download to open.  I tried to open it in Desktop and Documents but failed each time.

John

---

### Post by presence1960 on 2010-03-29
> **TXbirder said:**
> I can't get the download to open.  I tried to open it in Desktop and Documents but failed each time.

John

you don't open the downloaded script. You move it to desktop. Then open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

Here are easy full instructions from beginning to end:

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

### Post by TXbirder on 2010-03-29
Sorry this is taking so long-  I can't figure out how to move the info script to Desktop.  When I right-click the boot_info_script icon I get a menu which seems not to offer a means to move the info script to Desktop.

John

---

### Post by presence1960 on 2010-03-29
right click the file & choose copy. Now go to desktop & right click and choose paste.

---

### Post by TXbirder on 2010-03-29
At last.

John


```

```
[B]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9e779e77

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   155,027,249   155,027,187   7 HPFS/NTFS
/dev/sda2         296,849,070   312,576,704    15,727,635  1c Hidden W95 FAT32 (LBA)
/dev/sda3         155,027,250   296,849,069   141,821,820   5 Extended
/dev/sda5         155,027,313   290,969,279   135,941,967  83 Linux
/dev/sda6         290,969,343   296,849,069     5,879,727  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        54D0DC47D0DC30CA                       ntfs       TI100277P0G                   
/dev/sda2        0401-0163                              vfat       HDDRECOVERY                   
/dev/sda5        b818ec2c-f499-4337-a5da-39b898a09db4   ext4                                     
/dev/sda6        69915c67-430f-4735-b093-3016581837e0   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set b818ec2c-f499-4337-a5da-39b898a09db4
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
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set b818ec2c-f499-4337-a5da-39b898a09db4
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=b818ec2c-f499-4337-a5da-39b898a09db4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set b818ec2c-f499-4337-a5da-39b898a09db4
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=b818ec2c-f499-4337-a5da-39b898a09db4 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set b818ec2c-f499-4337-a5da-39b898a09db4
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b818ec2c-f499-4337-a5da-39b898a09db4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set b818ec2c-f499-4337-a5da-39b898a09db4
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b818ec2c-f499-4337-a5da-39b898a09db4 ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 54d0dc47d0dc30ca
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
    insmod fat
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 0401-0163
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
UUID=b818ec2c-f499-4337-a5da-39b898a09db4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=69915c67-430f-4735-b093-3016581837e0 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  83.2GB: boot/grub/core.img
  83.2GB: boot/grub/grub.cfg
  79.9GB: boot/initrd.img-2.6.31-14-generic
  80.3GB: boot/initrd.img-2.6.31-20-generic
  79.8GB: boot/vmlinuz-2.6.31-14-generic
  80.1GB: boot/vmlinuz-2.6.31-20-generic
  80.3GB: initrd.img
  79.9GB: initrd.img.old
  80.1GB: vmlinuz
  79.8GB: vmlinuz.old[/B]

---

### Post by presence1960 on 2010-03-29
Sorry for the delay. Your boot info results look OK. You definitely have a windows problem, it is not a GRUB problem.

---

### Post by oldfred on 2010-03-29
I would reinstall the windows boot loader, repair windows or make sure it works, then reinstall grub. Besure to follow the directions for grub2.

Instructions for both are here:

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by wilee-nilee on 2010-03-30
In case you need a full install ISO.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
It is a straight slipstream no corporate extras.

---

### Post by TXbirder on 2010-03-30
Well,  my netbook came with WinXP installed and no CD.  The instructions for this download imply that this is good only for Acer Aspires.   I could probably install it but my product key is for a Toshiba and might not work with this download.

John

---

### Post by TXbirder on 2010-03-30
WAIT A MINUTE!  I just discovered that I can get a recovery CD for XP from Toshiba.  I have ordered one, so the re-installation of XP is on hold until the CD arrives.

I'll just have to work XP-less for a week.

John

---

### Post by wilee-nilee on 2010-03-30
> **TXbirder said:**
> Well,  my netbook came with WinXP installed and no CD.  The instructions for this download imply that this is good only for Acer Aspires.   I could probably install it but my product key is for a Toshiba and might not work with this download.

John

The down load as I tried to explain is not for a acer computer although it looks that way, it is a XP ISO with sp3 slipstreamed any key for XP home will work.

---

### Post by TXbirder on 2010-03-30
Thanks

---

