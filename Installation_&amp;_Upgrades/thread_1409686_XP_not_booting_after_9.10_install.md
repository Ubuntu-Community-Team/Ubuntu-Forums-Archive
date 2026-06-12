---
title: "XP not booting after 9.10 install"
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by ARhere on 2010-02-17
Yet another "dual XP+Ubuntu" boot problem for everyone.

My neighbor wanted to try out Linux as he did not want to pay for Windows 7, so I offered to install Ubuntu as a dual boot.  Ubuntu 9.10 boots and works fine, but now Windows XP will not boot.  It just sits in a blank screen with flashing cursor after selecting Windows in Grub.

So, it is a Dell, originally with two partitions, one large one with Windows XP and a small one with HP's recovery partition.  Here are my steps.
1.  Using a Ubuntu 9.10 64-bit CD, I booted into a Live Ubuntu session.
2.  Using GParted, I resized the Windows partition.
3.  Installed / on the free space, did updates.
4.  Delivered to neighbors house, showed them Ubuntu, and when I tried to restart into XP from Grub, I get a blank screen with flashing cursor.

I looked at the SuperGrubDisk and it seems to only work with Grub1, so I did not want to try as at least one OS boots and I did not want to risk messing up Ubuntu as well.

Thoughts?  Easy fix?
-AR

---

### Post by wojox on 2010-02-17
From gnome-terminal run:

```
sudo update-grub2
```

---

### Post by ARhere on 2010-02-17
> **wojox said:**
> From gnome-terminal run:

```
sudo update-grub2
```

Thanks for the quick reply, no change though.

-AR

---

### Post by kansasnoob on 2010-02-17
In order to see what's going on we really need to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by ARhere on 2010-02-17
Done.  Here is the results...
```
                Boot Info Script 0.55    dated February 15th, 2010                    

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
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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
Disk identifier: 0xcab10bee

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   194,611,409   194,611,347   7 HPFS/NTFS
/dev/sda2         295,928,640   312,575,759    16,647,120   c W95 FAT32 (LBA)
/dev/sda3         194,611,410   295,917,299   101,305,890   5 Extended
/dev/sda5         194,611,473   291,692,204    97,080,732  83 Linux
/dev/sda6         291,692,268   295,917,299     4,225,032  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        29DC8DA8477E9254                       ntfs       HP_PAVILION                   
/dev/sda2        4B6E-6BC0                              vfat       HP_RECOVERY                   
/dev/sda5        0efac013-cc5c-4194-af7f-26f5f50a0838   ext4                                     
/dev/sda6        c1e77bde-a098-4a76-9dfd-61333746d7e1   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=wince)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

================================ sda2/boot.ini: ================================

[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons

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
search --no-floppy --fs-uuid --set 0efac013-cc5c-4194-af7f-26f5f50a0838
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
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0efac013-cc5c-4194-af7f-26f5f50a0838
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0efac013-cc5c-4194-af7f-26f5f50a0838 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0efac013-cc5c-4194-af7f-26f5f50a0838
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=0efac013-cc5c-4194-af7f-26f5f50a0838 ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0efac013-cc5c-4194-af7f-26f5f50a0838
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0efac013-cc5c-4194-af7f-26f5f50a0838 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0efac013-cc5c-4194-af7f-26f5f50a0838
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=0efac013-cc5c-4194-af7f-26f5f50a0838 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0efac013-cc5c-4194-af7f-26f5f50a0838
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=0efac013-cc5c-4194-af7f-26f5f50a0838 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 0efac013-cc5c-4194-af7f-26f5f50a0838
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=0efac013-cc5c-4194-af7f-26f5f50a0838 ro single 
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
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 29dc8da8477e9254
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" {
	insmod fat
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 4b6e-6bc0
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
UUID=0efac013-cc5c-4194-af7f-26f5f50a0838 /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda1 during installation
UUID=29DC8DA8477E9254 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=c1e77bde-a098-4a76-9dfd-61333746d7e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/windows/Documents\040and\040Settings/HP_Owner/My\040Documents/My\040Pictures  /home/wince/Pictures auto bind
/windows/Documents\040and\040Settings/HP_Owner/My\040Documents/Downloads  /home/wince/Downloads auto bind
/windows/Documents\040and\040Settings/HP_Owner/My\040Documents/My\040Music  /home/wince/Music auto bind
/windows/Documents\040and\040Settings/HP_Owner/My\040Documents/My\040Videos  /home/wince/Videos auto bind
/windows/Documents\040and\040Settings/HP_Owner/My\040Documents/My\040Files  /home/wince/Documents auto bind

=================== sda5: Location of files loaded by Grub: ===================


 103.0GB: boot/grub/core.img
 104.8GB: boot/grub/grub.cfg
 100.2GB: boot/initrd.img-2.6.31-14-generic
 100.9GB: boot/initrd.img-2.6.31-17-generic
 103.9GB: boot/initrd.img-2.6.31-19-generic
 100.2GB: boot/vmlinuz-2.6.31-14-generic
 100.6GB: boot/vmlinuz-2.6.31-17-generic
 103.7GB: boot/vmlinuz-2.6.31-19-generic
 103.9GB: initrd.img
 100.9GB: initrd.img.old
 103.7GB: vmlinuz
 100.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

I have to admit that I do not like the new Grub I was unhappy when Ubuntu 9.10 loaded it by default.

-AR

---

### Post by kansasnoob on 2010-02-18
I think it might be worthwhile to try upgrading to the newest grub2 (Lucid packages) which is very simple. You'd need to know whether you have 32bit or 64bit Ubuntu, so run:

```
uname -m
```

(64 bit = x86_64, and 32 bit = i686)

Then just:

```
sudo apt-get remove grub-pc grub-common
```

And then Download grub-common and grub-pc here:

[http://packages.ubuntu.com/lucid/grub-common](http://packages.ubuntu.com/lucid/grub-common)

[http://packages.ubuntu.com/lucid/admin/grub-pc](http://packages.ubuntu.com/lucid/admin/grub-pc)

Just save them to the Desktop (or Downloads folder, wherever you wish) then just double-click the package and gdebi will install it. **(Note: grub-common must be installed first and grub-pc second)**

Then just run:

```
sudo update-grub
```

And to be on the safe side:

```
sudo grub-install /dev/sda
```

That should be it, but if it doesn't work or if you just want to revert to legacy grub that's why I wrote this:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Specifically in your case:

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get --purge remove startupmanager
```

```
sudo apt-get --purge remove grub-pc grub-common
```

```
sudo apt-get install grub
```

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

```
sudo grub
```

```
root (hd0,4)
```

```
setup (hd0)
```

```
quit
```

```
sudo apt-get install startupmanager
```

Then you'll have to add Windows:

```
gksudo gedit /boot/grub/menu.lst
```

And at the very bottom, below this:

### END DEBIAN AUTOMAGIC KERNELS LIST

Add this:

```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

Be sure to click on Save, then File > Quit.

Now go to System > Administration > Startup Manager and under the Boot options tab change the timeout to something more appropriate like 10 seconds or more, and also make sure the "Show bootloader menu" box is checked.

You can also click on the Advanced tab and limit how many kernels to show (I always like to show 2 in case the newest kernel gets hosed), and you can also deselect the Memtest option (I do like to leave the Recovery options).

---

### Post by ARhere on 2010-02-18
Wow... Thank you for the elaborate reply.

I will ssh into my neighbor's box and try this during lunch.  I will report later on the outcome.

-AR

---

### Post by kansasnoob on 2010-02-18
If you're going to do that thru an SSH and **if you choose to try the newer Lucid grub2 packages** you may need to use wget and dpkg.

Just for example:

```
wget http://mirrors.kernel.org/ubuntu/pool/main/g/grub2/grub-common_1.98~20100128-1ubuntu3_i386.deb
```

And by using the "ls" command I can see it's in /home/<username>

```
lance@lance-desktop:~$ wget http://mirrors.kernel.org/ubuntu/pool/main/g/grub2/grub-common_1.98~20100128-1ubuntu3_i386.deb
--2010-02-18 11:13:23--  http://mirrors.kernel.org/ubuntu/pool/main/g/grub2/grub-common_1.98~20100128-1ubuntu3_i386.deb
Resolving mirrors.kernel.org... 204.152.191.39, 149.20.20.135
Connecting to mirrors.kernel.org|204.152.191.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1492596 (1.4M) [text/plain]
Saving to: `grub-common_1.98~20100128-1ubuntu3_i386.deb'

100%[======================================>] 1,492,596    572K/s   in 2.5s    

2010-02-18 11:13:26 (572 KB/s) - `grub-common_1.98~20100128-1ubuntu3_i386.deb' saved [1492596/1492596]

lance@lance-desktop:~$ ls /home/lance
Central National Bank  Public
Desktop                Screenshot-messages - System Log Viewer.png
Documents              Templates
Downloads              Unsaved Document 1
Music                  Videos
Pictures               **grub-common_1.98~20100128-1ubuntu3_i386.deb**
Projects

```

So then I would install using dpkg like:

```
dpkg -i '/home/lance/grub-common_1.98~20100128-1ubuntu3_i386.deb'
```

I doubt sudo would be needed in your SSH environment.

---

### Post by ARhere on 2010-02-24
Ok, time for an update.

Thank you kansasnoob for you replies.  I went a slightly different route as the Windows OS on the machine needed a fresh install anyways.  I also thought it would be simple then to recover Grub2 afterwords ... **Boy was I wrong!**

1. I installed a fresh copy of XP on sda1
2. Used the "super Grub 2 CD" to boot Ubuntu on sda5 and ran
```
sudo update-grub2
``` and rebooted.  No Grub2
3. Reused the SG2D to boot into Ubuntu again and ran
```
sudo grub-install /dev/sda1
``` and rebooted.
Now I get the Grub menu and it boots into Ubuntu fine, but when I select Windows XP in the grub menu, it reloads the Grub menu. ... an infinite loop?

WTF?  Ideas?
-Andrew

---

### Post by ARhere on 2010-02-24
UPDATE:  I just used the SG2D to try and boot into WinXP, and same thing... grub2 menu reloads.

I really hope I do not have to reinstall Windows XP again, as that would be very frustrating.

Please help, as this is my neighbor interested in trying Ubuntu Linux as he heard about it from a friend.  I am worried the PC down time is creating a bad first impression.

-AR

---

### Post by oldfred on 2010-02-24
If your really did this then you removed part of windows.
sudo grub-install /dev/sda1

The difference is sda where the MBR or Master Boot Record is and the PBR or partition boot record. (Windows may call it something else). See this site while mostly Vista it helps to understand how windows works:
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You need to run the XP repairs.

You can do it with windows repair disk or testdisk:
Restore PBR boot sector for windows from linux using testdisk
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)
This is all the commands - you should only have to run fixboot, If you run fixMBR you will have to reinstall grub to sda.

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

---

### Post by ARhere on 2010-02-24
That was a **_VERY_** informational post and I really appreciate it as my problem is solved.

I know we may not always have time to educate rather then say, "Do this" so I give you a gold start.

Thank you,
-AR

---

