---
title: "Post-Installation Problems"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by Sinuse on 2010-02-27
So, I ordered the Ubuntu 9.10 Desktop Edition in the mail. I got it, and  tried to install it side-by-side with Windows XP. There wasn't enough  space, so I decided to erase everything on a hard drive that I barely  ever used and install it on there. When that was finished, I restarted  my computer...And instead of giving me an option to dual-boot, it just  went straight to Windows. I can't access the hard drive anymore. I'm new  to Linux, so I just don't know what to do at this point to be able to  use Ubuntu :redface: I  put the disc back in and tried to re-install it, but it just freezes up.  Help much appreciated!

---

### Post by presence1960 on 2010-02-27
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

### Post by Sinuse on 2010-02-27
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

Thanks for being interested in my problem!
I attempted to try ubuntu without any changes, but when it was loading, the screen just went into a blinking underscore at the top left.

---

### Post by presence1960 on 2010-02-28
> **Sinuse said:**
> Thanks for being interested in my problem!
I attempted to try ubuntu without any changes, but when it was loading, the screen just went into a blinking underscore at the top left.

At the window where you choose "try ubuntu without any changes" hit F4 before selecting that and choose safe graphics mode. Then choose "try ubuntu..."

See [here]("https://help.ubuntu.com/community/BootOptions") for more info on this and other boot options from the Live CD

---

### Post by Sinuse on 2010-03-02
> **presence1960 said:**
> At the window where you choose "try ubuntu without any changes" hit F4 before selecting that and choose safe graphics mode. Then choose "try ubuntu..."

See [here]("https://help.ubuntu.com/community/BootOptions") for more info on this and other boot options from the Live CD

It still wouldn't work :/ Is there any way to get the harddrive that I installed it on to appear again instead? This is kind of a lot of trouble.

---

### Post by darkod on 2010-03-02
> **Sinuse said:**
> It still wouldn't work :/ Is there any way to get the harddrive that I installed it on to appear again instead? This is kind of a lot of trouble.

If the hard disk is working properly, it didn't go anywhere. Windows doesn't recognize linux partitions so you won't be able to see them in My Computer.
But if you open Disk Management, your hdd is still there, at least it should be.

But if you installed ubuntu on another hdd, you need to get that working. Go into BIOS and set it to boot from your other disk. It seems you are still booting from the XP disk as first option so it just loads XP directly. Windows bootloader can't boot linux.

Switch the hdd boot order to get grub2 from the other hdd.

---

### Post by Sinuse on 2010-03-02
> **darkod said:**
> If the hard disk is working properly, it didn't go anywhere. Windows doesn't recognize linux partitions so you won't be able to see them in My Computer.
But if you open Disk Management, your hdd is still there, at least it should be.

But if you installed ubuntu on another hdd, you need to get that working. Go into BIOS and set it to boot from your other disk. It seems you are still booting from the XP disk as first option so it just loads XP directly. Windows bootloader can't boot linux.

Switch the hdd boot order to get grub2 from the other hdd.

Thank you for explaining that to me :) I feel much more at ease.

I did as you instructed, switched the other hdd to first priority and rebooted my computer. It was loading fine, and then that dang blinking underscore appeared ):

---

### Post by darkod on 2010-03-02
> **Sinuse said:**
> Thank you for explaining that to me :) I feel much more at ease.

I did as you instructed, switched the other hdd to first priority and rebooted my computer. It was loading fine, and then that dang blinking underscore appeared ):

What model of video card do you have?

---

### Post by Sinuse on 2010-03-02
> **darkod said:**
> What model of video card do you have?

NVIDIA Geforce 6800 XT.

(By the way, I had got it to boot in the demo version by going into safe graphics mode before installation.)

---

### Post by darkod on 2010-03-02
When you boot your computer, you get a grub boot menu, right? Don't boot the default ubuntu normal mode entry, boot the recovery mode. In the next menu select something like "netroot with networking". That will load command prompt.

Write this down, because you will have only text command prompt.

If that loads successfully, install the EnvyNG package with:

sudo apt-get install envyng-core envyng-qt

Run it in text mode with:

envyng -t

Select to install nvidia driver. If there are more options, select 190 or 190.53, that one covers 6800 XT. Lets hope it's in the list.

Just follow the messages. After it's installed, it will ask to reboot. Try the normal mode entry and see if it helped.

---

### Post by Sinuse on 2010-03-02
> **darkod said:**
> When you boot your computer, you get a grub boot menu, right? Don't boot the default ubuntu normal mode entry, boot the recovery mode. In the next menu select something like "netroot with networking". That will load command prompt.

Write this down, because you will have only text command prompt.

If that loads successfully, install the EnvyNG package with:

sudo apt-get install envyng-core envyng-qt

Run it in text mode with:

envyng -t

Select to install nvidia driver. If there are more options, select 190 or 190.53, that one covers 6800 XT. Lets hope it's in the list.

Just follow the messages. After it's installed, it will ask to reboot. Try the normal mode entry and see if it helped.

If you're talking about booting with the hard drive that ubuntu is installed on, then no. I don't get a menu. Just underscore. But when I use the disk, I get a menu. Do I use that?

---

### Post by darkod on 2010-03-02
> **Sinuse said:**
> If you're talking about booting with the hard drive that ubuntu is installed on, then no. I don't get a menu. Just underscore. But when I use the disk, I get a menu. Do I use that?

You should get a menu with the hdd too because you also have windows on the computer right? If you have two OSs then you should get a menu.
Something is not right. I was trying to avoid it, but if you can use the cd and boot into live desktop (at least in safe graphics mode), run the script that presence suggested earlier and post the results as per the instructions. It will show more info.
It's quite late over here and I really gotta go to bed, but maybe presence can continue after seeing your results. Run the script.

---

### Post by Ozymandias_117 on 2010-03-02
To get to the grub menu, you have to hold shift while your computer boots, it no longer displays by default.

---

### Post by Sinuse on 2010-03-02
I finally got in! I went to the menu and clicked the down button and all of a sudden it started to load.
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=debd320b-9177-4b68-8fa8-2dc3dbcd31c9)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf929f929

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    39,086,144    39,086,082   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5c15ac3

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000ca9dd

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   482,383,754   482,383,692  83 Linux
/dev/sdc2         482,383,755   488,392,064     6,008,310   5 Extended
/dev/sdc5         482,383,818   488,392,064     6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B0E47FA9E47F7088                       ntfs                                     
/dev/sdb1        3AC4439BC44357F1                       ntfs                                     
/dev/sdc1        debd320b-9177-4b68-8fa8-2dc3dbcd31c9   ext4                                     
/dev/sdc5        26680ede-7a18-4c41-9547-0c9ab5d9e222   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=candice)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root=(hd2,1)
search --no-floppy --fs-uuid --set debd320b-9177-4b68-8fa8-2dc3dbcd31c9
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
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set debd320b-9177-4b68-8fa8-2dc3dbcd31c9
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=debd320b-9177-4b68-8fa8-2dc3dbcd31c9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set debd320b-9177-4b68-8fa8-2dc3dbcd31c9
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=debd320b-9177-4b68-8fa8-2dc3dbcd31c9 ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 3ac4439bc44357f1
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=debd320b-9177-4b68-8fa8-2dc3dbcd31c9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=26680ede-7a18-4c41-9547-0c9ab5d9e222 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  40.7GB: boot/grub/core.img
  40.7GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-14-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .5GB: initrd.img
    .5GB: vmlinuz
```

---

### Post by cnntdygrhm on 2010-03-02
Please help ive tried three post now and no luck here is my problem I'm having a similar problem. I'm trying to upgrade my netbook (sylvania meso g) from ubuntu 8.04 to ubuntu 9.10 i downloaded the ISO downloaded the usb creator so that i could put it on my thumb drive, create the ISO and reboot with my freshely made ISO thumbdrive. When i reboot i get to the install screen select install and my netbook reboots and starts the process all over again without 9.10 ever being installed. When i select help i get the install screen but if at the very tipy top of my screen you see a 1/2in section that i cant read because it so small for help screen.

---

