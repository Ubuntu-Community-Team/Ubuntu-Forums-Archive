---
title: "&quot;Error: no such partition&quot;"
date: 2010-12-05
forum: Installation &amp; Upgrades
---

### Post by danielpj1 on 2010-12-05
Hello -

I installed UNR on my Asus eeePC 1001P. This is my first Ubuntu/Linux install (read: I am new to all of this). I had two partitions one with Windows 7 starter and another one with UNR (dual boot set up). I decided to uninstall UNR and try to redo the partitions by reinstalling UNR. I deleted the UNR partition. When the computer rebooted it posted the error:

Error: no such partition
grub rescue>

I searched the internet and attempted this:
grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
grub> boot

This was not succesfull (getting "unknown command" for all lines above). I tried:
set root=(hd0,0)

This prompted "grub>" but all subsequent commands above returned the "unkown command"

With no CD drive in this computer I tried reinstalling UNR, but the USB is not recognized (boot priority in BIOS is set to USB then HDD). I tried installing a copy of repair disk in a bootable USB and this did not work either.

I can still access the Asus "Express Gate" interface and it recognizes the USB drives (files cannot be executed), but since this interface is pretty limited I cannot run anything from the "Express Gate". Since the USB is not recognized I am guessing a USB CD drive would be useless (I do not have one and have not tested this). I have run out of options, short of opening this computer, taking the hard drive out, formatting and installing a fresh copy of Windows/Ubuntu on it.

Can anyone help me out? Thanks in advance for any attempts to help me!

---

### Post by Quackers on 2010-12-05
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by danielpj1 on 2010-12-05
Thanks for your reply. SOrry about the code tags...

My problem lies in that I can't boot from a USB drive, so I cant reinstall or try Ubuntu... my BIOS setting are correct (boot order is set to start with USB then HDD), not sure where to go from here.

---

### Post by Quackers on 2010-12-05
How did you install Ubuntu?

---

### Post by danielpj1 on 2010-12-05
Through a USB as explained in the UNR homepage. That is what is so frustrating about this, for some reason my USB drives don't seem to be working.

The curious thing is if I load the Asus Express interface (it is a very simple OS that I can boot to using a different power button on the netbook), the contents of the USB thumb drive are visible.

---

### Post by Quackers on 2010-12-05
I know you said your boot priority is set to usb first - but usb what? It could be usb hdd, but you need usb flash or similar to be first boot device. It's worth checking that first.

---

### Post by danielpj1 on 2010-12-05
Unfortunately not that simple ;) ... There are only 3 boot priorities  available in the BIOS (HDD, USB, and CD. I placed HDD dead last). The USB option is for the USB drives since I had to change it to install Ubuntu the first time.

BTW, thank for taking some time to try to help me

---

### Post by Quackers on 2010-12-05
So usb is set as first boot device and you are trying to boot from the same usb stick that you installed Ubuntu with and it won't boot? 
There will be a setting in the bios to return all settings to default. Try that first. Then go back in and see what device is set to boot first.

---

### Post by danielpj1 on 2010-12-05
Well finally found the problem with the boot sequence. After reseting to defaults and setting USB as first boot device another menu is available to set USB devices as a priority (again under a seperate heading)... So I guess it has to be done twice. 

I loaded the recovery disk and followed the command prompt instructions to restore the bootloader.

Thanks Quackers, you defenetely guided me in the right direction!

---

### Post by Quackers on 2010-12-05
Excellent! :-)  Enjoy!
You're welcome.

Please mark the thread as solved using Thread Tools near the top of the page. Thanks.

---

### Post by bdraughon on 2010-12-06
@quackers-
looks like you were about to finish but didn't have to. i'm having the same (similar) problem. here it is from the start..
i put linux on my thinkpad with windows 7 everything is awesome!! so i wanted to do the same with my old desktop pc bc XP is sooo messed up with crap it slows down my internet for the whole house when its connected to network (other problem for another forum). so in an attempt to allow me to access the extra harddrives on the XPsystem i wanted to put ubuntu on dual boot eventually to get rid of xp all together..
i first installed the server edition (to do something little different) everything worked correctly but didn't realize it was only cmd line interface i wanted the gui from the desktop edition. so i ran live cd deleted the server partition and installed the desktop. i'm not sure if i selected the correct settings for boot location... after reboot i got the 
error: no such partion
grub rescue> 
so here's the txt file you asked for from danielpj1

thanks!!
............................................

```
       Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,555,327   163,555,265   7 HPFS/NTFS
/dev/sda2         172,994,558   312,576,704   139,582,147   f W95 Ext d (LBA)
/dev/sda5         268,414,083   312,576,704    44,162,622   7 HPFS/NTFS
/dev/sda6         172,994,560   268,412,927    95,418,368  83 Linux
/dev/sda3         163,555,328   172,992,511     9,437,184  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B6C08C35C08BF9BF                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        1d44e3ab-4274-4dd2-8c6c-621c80bec1e8   swap                                     
/dev/sda5        32B4A9E7B4A9AE33                       ntfs       Zeroid                        
/dev/sda6        355ec381-ffe3-4fa0-a026-f9b681242704   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9CB098C5B098A774                       ntfs       Vault                         
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        3A8C782A8C77DF37                       ntfs       The Man                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[Boot Loader]
Timeout=5
Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 355ec381-ffe3-4fa0-a026-f9b681242704
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set 355ec381-ffe3-4fa0-a026-f9b681242704
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 355ec381-ffe3-4fa0-a026-f9b681242704
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=355ec381-ffe3-4fa0-a026-f9b681242704 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 355ec381-ffe3-4fa0-a026-f9b681242704
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=355ec381-ffe3-4fa0-a026-f9b681242704 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 355ec381-ffe3-4fa0-a026-f9b681242704
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos6)'
    search --no-floppy --fs-uuid --set 355ec381-ffe3-4fa0-a026-f9b681242704
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b6c08c35c08bf9bf
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=355ec381-ffe3-4fa0-a026-f9b681242704 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb3 during installation
UUID=1d44e3ab-4274-4dd2-8c6c-621c80bec1e8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 105.8GB: boot/grub/core.img
 103.7GB: boot/grub/grub.cfg
  89.1GB: boot/initrd.img-2.6.35-22-generic
 105.8GB: boot/vmlinuz-2.6.35-22-generic
  89.1GB: initrd.img
 105.8GB: vmlinuz

```

---

### Post by Quackers on 2010-12-06
Well here's a clue :-)
```
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.
```

You don't have a partition #4 - that may have something to do with it :-)
I am guessing that you've deleted a partition maybe?

I suggest you boot from the Ubuntu Live cd and select "try ubuntu" and when the desktop loads and after you have connected to the internet re-install grub with the following commands. 
Open up a terminal (Applications > accessories > terminal) and then 

```
sudo mkdir /mnt
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Please note! No partition number in the last command.
It will be easier if you copy/paste the commands into the terminal one at a time pressing enter after each line.

---

### Post by bdraughon on 2010-12-06
update, i used /sdb instead of /sda

```

ubuntu@ubuntu:~$ sudo mkdir /mnt
mkdir: cannot create directory `/mnt': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /mnt
ubuntu@ubuntu:~$ sudo grub-intall --root-directory=/mnt /dev/sdb
sudo: grub-intall: command not found
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sdb
/usr/sbin/grub-setup:  warn: Sector 32 is already in use by FlexNet; avoiding it.  This  software may cause boot or other problems in future.  Please ask its  authors not to store data in the boot track..
Installation finished. No error reported.
ubuntu@ubuntu:~$ 

```

rebooting....
WAMBAMMBO!! IT'S FLIPPIN WORKING!!!

thanks for you time and help!!

WIPE OUT!

---

