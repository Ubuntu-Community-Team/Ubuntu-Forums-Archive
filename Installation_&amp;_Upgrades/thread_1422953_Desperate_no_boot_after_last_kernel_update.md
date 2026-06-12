---
title: "Desperate: no boot after last kernel update"
date: 2010-03-06
forum: Installation &amp; Upgrades
---

### Post by WDYSUN on 2010-03-06
Dear Friends

I am desperate! I updated the system and I think there was a kernel update because know in grub I see linux-2.6.31-20-generic. The computer is unable to boot. After I select which kernel to use the boot starts but then at some point it stops and I don't have access to keybords, mouse or whatever, it just does not respond. I also tried to boot from previus kernel both generic and recovery mode, no way to boot the system.

Can somebody tell me what I should do? I need my PC for my job. 

I hope somebody can help.

Best Wishes

Pietro

---

### Post by TitanusEramius on 2010-03-06
When you boot your computer, what else do you see in GRUB?

Unless you have removed them, there should be the old kernel you used to boot, just to rows down, and it should be named something like "linux-2.6.29-20-generic". Have you tried to select that one and press enter?

If this works, it's possible to remove the new kernel (top two lines in GRUB) so you don't have to click two down each time you boot, but please post the result here when you tries this.

---

### Post by WDYSUN on 2010-03-06
Hello TitanusEramius,

I also tried to boot from previous kernel versions, but the results were the same.

Then I tried a couple of times again. Now I can boot but it takes a lot of time before Ubuntu prompt to the login window.

I tried to go in Aministrator > Log file viewer 

When window open the windows has an allert on top, please see the attached picture. What log shoud I sumbit to see what's the problem?

The ohter question is: is there any possibility to get the startup process in verbose mode so I can understand where the system takes so much time to boot? In my university lab I was used to debian lenny and I could see the whole process appearing on the screen up to login, is that possible in ubuntu?

I would appreciate any help you can provide.

Best Wishes
Pietro   






> **TitanusEramius said:**
> When you boot your computer, what else do you see in GRUB?

Unless you have removed them, there should be the old kernel you used to boot, just to rows down, and it should be named something like "linux-2.6.29-20-generic". Have you tried to select that one and press enter?

If this works, it's possible to remove the new kernel (top two lines in GRUB) so you don't have to click two down each time you boot, but please post the result here when you tries this.

---

### Post by presence1960 on 2010-03-06
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by WDYSUN on 2010-03-06
Hello presence1960,

here the content of the RESULTS.txt file you were asking for

Thanks
Pietro 

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

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

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1       1,839,860,190 1,840,020,839       160,650  de Dell Utility
/dev/sda2    *  1,840,020,840 1,859,154,254    19,133,415   7 HPFS/NTFS
/dev/sda3       1,859,154,255 1,953,520,064    94,365,810   7 HPFS/NTFS
/dev/sda4                  63 1,839,860,189 1,839,860,127   5 Extended
/dev/sda5                 126 1,816,100,054 1,816,099,929  83 Linux
/dev/sda6       1,816,100,118 1,839,860,189    23,760,072  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07DA-0114                              vfat                                     
/dev/sda2        5A64E17664E15573                       ntfs       RECOVERY                      
/dev/sda3        6656E47656E447FF                       ntfs       SEVEN                         
/dev/sda5        1e2405d2-d183-4723-9e92-650d1d597c11   ext4                                     
/dev/sda6        d4805e44-d5f6-4a77-9214-310dad6f6495   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set 1e2405d2-d183-4723-9e92-650d1d597c11
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
	search --no-floppy --fs-uuid --set 1e2405d2-d183-4723-9e92-650d1d597c11
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=1e2405d2-d183-4723-9e92-650d1d597c11 ro   splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1e2405d2-d183-4723-9e92-650d1d597c11
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=1e2405d2-d183-4723-9e92-650d1d597c11 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1e2405d2-d183-4723-9e92-650d1d597c11
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=1e2405d2-d183-4723-9e92-650d1d597c11 ro   splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1e2405d2-d183-4723-9e92-650d1d597c11
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=1e2405d2-d183-4723-9e92-650d1d597c11 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1e2405d2-d183-4723-9e92-650d1d597c11
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1e2405d2-d183-4723-9e92-650d1d597c11 ro   splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 1e2405d2-d183-4723-9e92-650d1d597c11
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=1e2405d2-d183-4723-9e92-650d1d597c11 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 5a64e17664e15573
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
UUID=1e2405d2-d183-4723-9e92-650d1d597c11 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d4805e44-d5f6-4a77-9214-310dad6f6495 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


   4.5GB: boot/grub/core.img
   2.0GB: boot/grub/grub.cfg
    .3GB: boot/initrd.img-2.6.31-14-generic
    .9GB: boot/initrd.img-2.6.31-19-generic
   2.0GB: boot/initrd.img-2.6.31-20-generic
    .2GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-19-generic
   2.1GB: boot/vmlinuz-2.6.31-20-generic
   2.0GB: initrd.img
    .9GB: initrd.img.old
   2.1GB: vmlinuz
    .6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 


```



> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by presence1960 on 2010-03-06
```
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1       1,839,860,190 1,840,020,839       160,650  de Dell Utility
/dev/sda2    *  1,840,020,840 1,859,154,254    19,133,415   7 HPFS/NTFS
/dev/sda3       1,859,154,255 1,953,520,064    94,365,810   7 HPFS/NTFS
[COLOR="Red"]/dev/sda4                  63 1,839,860,189 1,839,860,127   5 Extended
/dev/sda5                 126 1,816,100,054 1,816,099,929  83 Linux
/dev/sda6       1,816,100,118 1,839,860,189    23,760,072  82 Linux swap / Solaris[/COLOR]
```
Everything except the above looks OK. Your sda4 is an extended partition but is at the beginning of the disk before sda1. sda4 starts at 63 which is where sda1 usually starts. I am not sure if that has anything to do with the slow boot but you can boot into ubuntu and run in terminal ```
sudo fdisk /dev/sda
x
f
w
```

This will fix partition table order. Then see what happens when you boot.

---

### Post by WDYSUN on 2010-03-06
Sorry I want to be sure I got it right. 

boot in ubuntu then open terminal and run 

```

sudo fdisk /dev/sda
x
f
w

```



There is also something else strange. The USB devices have problems, for instance my HP printer doesn't work after the long boot, and to get it working I need to switch it OFF and then ON.

I am getting crazy now! 

Thanks 
Pietro 

> **presence1960 said:**
> 
...snip...
you  can boot into ubuntu and run in terminal 

```

sudo fdisk /dev/sda
x
f
w

```

This will fix partition table order. Then see what happens when you boot.


---

### Post by presence1960 on 2010-03-06
> **WDYSUN said:**
> Sorry I want to be sure I got it right. 

boot in ubuntu then open terminal and run 

```

sudo fdisk /dev/sda
x
f
w

```



There is also something else strange. The USB devices have problems, for instance my HP printer doesn't work after the long boot, and to get it working I need to switch it OFF and then ON.

I am getting crazy now! 

Thanks 
Pietro

Correct. In this order:
sudo fdisk /dev/sda (will ask for password)
then x
then f
then w

Then reboot.

---

### Post by howlingmadhowie on 2010-03-06
i had this problem. i'm using the ati graphics driver (fglrx).  i solved the problem by booting into rescue mode and renaming /etc/X11/xorg.conf /etc/X11/xorg.conf.old, then rebooting. the kernel will now use the in-built graphics driver. then i could run the ati setup utility again and restart.

---

### Post by WDYSUN on 2010-03-06
Presence1960

thanks o lot! God bless you!!!!! Your suggestions saved me from the hell!!!!

Anyway the printer also works correctly. When I launched your commands  the outputs were saying that the kernel update was causing wrong partition... etc, and in fact I did an update yesterday.   

Thanks a lot again!
Pietro
Ps: I see you are from Philly. I spent years in Philly while I was doing my phd in  UPenn Econ/Wharton School... mmh! The pilly steak was great! 


> **presence1960 said:**
> Correct. In this order:
sudo fdisk /dev/sda (will ask for password)
then x
then f
then w

Then reboot.

---

### Post by Sarnix on 2010-03-19
Hi,

I hope you can help me too, Presence1960 or anyone else. I did a kernel update and they seem to give me trouble all the time, because I messed up when installing the os-es on this computer.

Right now during the booting process it starts doing filesystem checks and after the checks it reboots. Then I booted to recovery mode and ran the boot info script and here's the RESULT.TXT
It doesn't tell me anything but it must the messed up hdd partitioning.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2b289e06

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,812,684   204,812,622   7 HPFS/NTFS
/dev/sda2         204,812,685   400,114,889   195,302,205  83 Linux
/dev/sda3         400,114,890   603,240,749   203,125,860   5 Extended
/dev/sda5         400,114,953   407,922,479     7,807,527  82 Linux swap / Solaris
/dev/sda6         407,922,543   603,240,749   195,318,207  83 Linux
/dev/sda4         603,240,750 2,930,272,064 2,327,031,315  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F64C4DF54C4DB0E3                       ntfs                                     
/dev/sda2        cd17428d-6e42-4856-b028-13c1dd9313e2   ext4                                     
/dev/sda4        7222a2fa-9972-459b-94bc-8d0719adb0c5   ext2                                     
/dev/sda5        170f6949-a5a1-4dd3-b8fe-81ff5d941c93   swap                                     
/dev/sda6        8122ee8b-8ece-4f07-afc4-6c7f00d42925   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)
/dev/sda4        /mnt/files               ext2       (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set cd17428d-6e42-4856-b028-13c1dd9313e2
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
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set cd17428d-6e42-4856-b028-13c1dd9313e2
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=cd17428d-6e42-4856-b028-13c1dd9313e2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set cd17428d-6e42-4856-b028-13c1dd9313e2
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=cd17428d-6e42-4856-b028-13c1dd9313e2 ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set cd17428d-6e42-4856-b028-13c1dd9313e2
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=cd17428d-6e42-4856-b028-13c1dd9313e2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set cd17428d-6e42-4856-b028-13c1dd9313e2
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=cd17428d-6e42-4856-b028-13c1dd9313e2 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set cd17428d-6e42-4856-b028-13c1dd9313e2
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=cd17428d-6e42-4856-b028-13c1dd9313e2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set cd17428d-6e42-4856-b028-13c1dd9313e2
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=cd17428d-6e42-4856-b028-13c1dd9313e2 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set cd17428d-6e42-4856-b028-13c1dd9313e2
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=cd17428d-6e42-4856-b028-13c1dd9313e2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set cd17428d-6e42-4856-b028-13c1dd9313e2
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=cd17428d-6e42-4856-b028-13c1dd9313e2 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f64c4df54c4db0e3
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=cd17428d-6e42-4856-b028-13c1dd9313e2 /               ext4    errors=remount-ro 0       1
# /docs was on /dev/sda4 during installation
UUID=7222a2fa-9972-459b-94bc-8d0719adb0c5 /mnt/files           ext2    defaults        0       2
# /files was on /dev/sdb1 during installation
#UUID=27dcdb0e-bbcd-4ff5-8eb8-43582e66fb2a /mnt/disk2          ext2    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=8122ee8b-8ece-4f07-afc4-6c7f00d42925 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=170f6949-a5a1-4dd3-b8fe-81ff5d941c93 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


 108.5GB: boot/grub/core.img
 108.0GB: boot/grub/grub.cfg
 107.8GB: boot/initrd.img-2.6.31-14-generic
 105.4GB: boot/initrd.img-2.6.31-17-generic
 109.6GB: boot/initrd.img-2.6.31-19-generic
 110.6GB: boot/initrd.img-2.6.31-20-generic
 107.4GB: boot/vmlinuz-2.6.31-14-generic
 105.0GB: boot/vmlinuz-2.6.31-17-generic
 108.1GB: boot/vmlinuz-2.6.31-19-generic
 107.0GB: boot/vmlinuz-2.6.31-20-generic
 110.6GB: initrd.img
 109.6GB: initrd.img.old
 107.0GB: vmlinuz
 108.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

TIA for any help,
Marnix

---

### Post by presence1960 on 2010-03-19
```
=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=cd17428d-6e42-4856-b028-13c1dd9313e2 /               ext4    errors=remount-ro 0       1
# /docs was on /dev/sda4 during installation
UUID=7222a2fa-9972-459b-94bc-8d0719adb0c5 /mnt/files           ext2    defaults        0       2
[COLOR="Red"]# /files was on /dev/sdb1 during installation
#UUID=27dcdb0e-bbcd-4ff5-8eb8-43582e66fb2a /mnt/disk2          ext2    defaults        0       2[/COLOR]
# /home was on /dev/sda6 during installation
UUID=8122ee8b-8ece-4f07-afc4-6c7f00d42925 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=170f6949-a5a1-4dd3-b8fe-81ff5d941c93 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Note the red in your fstab file, at boot your Os is looking to mount a non-existant partition on a non-existant disk.

You can fix this by editing the fstab file. Boot the Live CD and choose "try ubuntu without any changes". When the desktop loads go Places > Computer. Highlight your ubuntu (sda2) root partition on the left pane of the file browser. Do not highlight Filesystem as that is the Live CD's root. When you highlight the correct one you will see directories such as bin, boot, dev, etc, home etc. Your ubuntu / partition is now mounted.

Now open a terminal and run ```
gksu nautilus
```Again highlight your ubuntu root (/) partition in the file browser you just opened from terminal. Open the etc directory and then open the fstab file. Remove the line I highlighted in red. Be careful to only remove that as you now have root priviledge. When removed click Save on top toolbar. Close file. Close both browsers and reboot without the Live CD.

---

### Post by Sarnix on 2010-03-20
Hi,

the lines in red are commented out and I removed that disk from the computer. So as far as I know that disk doesn't exist for the OS.
I can get into a shell with root privileges and I can get into a regular shell if I comment out sda4 and mount it afterwards.
I think the whole problem is the unconventional partitioning I did when I installed ubuntu and xp. In /var/log/messages it keeps complaining about unproperly shutdown or unmounted filesystems. That's why it performs the filesystem checks and reboots after the checks are finished. It can't get past that for some reason.

---

