---
title: "tri-boot with ubuntu and grub 1.5"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by dbowlin17 on 2010-01-30
I have 3 partitions, one with ubuntu 9.10, another with xp pro and another with 7 ultimate. I want to be able to boot to the windows oses from grub. What do I do? when i hit escape at grub, i get ubuntu 9.10 2.6.31-17, 2.6.31-16, 2.6.31-15, 2.6.31-14 all with recovery mode as well, and then memtest, and none of my windows OSes. is there a way to have the computer just show me the oses instead of the brief window of time i can have? and then my final question, windows can't read the linux partitons, is there something i can do to share files between the two operating systems?

---

### Post by phillw on 2010-01-30
Hi,

firstly, lets see if grub can 'see' your Windows installations. If it is a new install of 9.10 (not an upgrade from 9.04 etc) then
```
sudo update-grub
```
will tell grub to go 'a hunting' and you should see it locate your Win areas.

Regards,

Phill.

---

### Post by dbowlin17 on 2010-01-30
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-17-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


That is what came out of terminal. Why do I have 4 different linux kernels? But also, it appears to have not found either of the Windows installs.

---

### Post by kansasnoob on 2010-01-30
While booted into Ubuntu post the output of these commands:

```
grub-install -v
```

```
ls /boot
```

```
ls /boot/grub
```

---

### Post by dbowlin17 on 2010-01-30
grub-install (GNU GRUB 0.97)

abi-2.6.31-14-generic         memtest86+.bin
abi-2.6.31-15-generic         System.map-2.6.31-14-generic
abi-2.6.31-16-generic         System.map-2.6.31-15-generic
abi-2.6.31-17-generic         System.map-2.6.31-16-generic
config-2.6.31-14-generic      System.map-2.6.31-17-generic
config-2.6.31-15-generic      vmcoreinfo-2.6.31-14-generic
config-2.6.31-16-generic      vmcoreinfo-2.6.31-15-generic
config-2.6.31-17-generic      vmcoreinfo-2.6.31-16-generic
grub                          vmcoreinfo-2.6.31-17-generic
initrd.img-2.6.31-14-generic  vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-15-generic  vmlinuz-2.6.31-15-generic
initrd.img-2.6.31-16-generic  vmlinuz-2.6.31-16-generic
initrd.img-2.6.31-17-generic  vmlinuz-2.6.31-17-generic


default        grubenv            menu.lst           stage1
device.map     installed-version  menu.lst~          stage2
e2fs_stage1_5  jfs_stage1_5       minix_stage1_5     xfs_stage1_5
fat_stage1_5   menu_backupp.lst   reiserfs_stage1_5





I will also say, I got the 7 partition to work. When I tried following similar steps for XP, it didn't work and when I try to boot to it, it appears as if it refreshes, the whole screen flashes and then is right where it was when i hit enter to boot.

---

### Post by kansasnoob on 2010-01-30
We better just see the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dbowlin17 on 2010-01-30
Here it is:

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004c6df

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   717,864,524   717,864,462  83 Linux
/dev/sda2    *    717,864,525   847,316,294   129,451,770   7 HPFS/NTFS
/dev/sda3         847,316,295   976,768,064   129,451,770   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        e1bb393e-c181-4968-acb6-85497c5b983c   ext3                                     
/dev/sda2        6716CEE22C3EA0F5                       ntfs                                     
/dev/sda3        43635F5256996886                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e1bb393e-c181-4968-acb6-85497c5b983c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=e1bb393e-c181-4968-acb6-85497c5b983c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 9.10, kernel 2.6.31-17-generic
uuid		e1bb393e-c181-4968-acb6-85497c5b983c
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=e1bb393e-c181-4968-acb6-85497c5b983c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-17-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid		e1bb393e-c181-4968-acb6-85497c5b983c
kernel		/boot/vmlinuz-2.6.31-17-generic root=UUID=e1bb393e-c181-4968-acb6-85497c5b983c ro  single
initrd		/boot/initrd.img-2.6.31-17-generic

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		e1bb393e-c181-4968-acb6-85497c5b983c
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e1bb393e-c181-4968-acb6-85497c5b983c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		e1bb393e-c181-4968-acb6-85497c5b983c
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=e1bb393e-c181-4968-acb6-85497c5b983c ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		e1bb393e-c181-4968-acb6-85497c5b983c
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=e1bb393e-c181-4968-acb6-85497c5b983c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-15-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid		e1bb393e-c181-4968-acb6-85497c5b983c
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=e1bb393e-c181-4968-acb6-85497c5b983c ro  single
initrd		/boot/initrd.img-2.6.31-15-generic

title		Ubuntu 9.10, kernel 2.6.31-14-generic
uuid		e1bb393e-c181-4968-acb6-85497c5b983c
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=e1bb393e-c181-4968-acb6-85497c5b983c ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid		e1bb393e-c181-4968-acb6-85497c5b983c
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=e1bb393e-c181-4968-acb6-85497c5b983c ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
uuid		e1bb393e-c181-4968-acb6-85497c5b983c
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows 7
root (hd0,2)
savedefault
makeactive
chainloader +1

title Windows XP
root (hd0,1)
savedefault
makeactive
chainloader+1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e1bb393e-c181-4968-acb6-85497c5b983c /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ecd49d1a-e68d-4e08-b7a6-a550f4c0b0a4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================ sda2/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

---

### Post by kansasnoob on 2010-01-31
Sorry to take so long, I'm just now looking this over.

---

### Post by kansasnoob on 2010-01-31
Well I don't really see anything wrong there. What I think is happening is that with 4 kernels, each with it's boot and recovery options, and a memtest that totals 9 entries and it's pushing the Windows entries off the bottom of the boot menu.

The easiest fix is to install Startup Manager:

```
sudo apt-get install startupmanager
```

It will then show up in System > Administration:

[http://www.psychocats.net/ubuntu/images/sum09.png](http://www.psychocats.net/ubuntu/images/sum09.png)

You can see under the Boot Options tab that you can change the timeout value, if you remove the tick from "Use timeout in boot menu" it will always sit and wait infinitely until you make a choice. You'll notice you can also change the default boot, whether or not to show the menu, etc.

Now if you click on the Advanced tab you'll also see the option to limit the number of kernels to show. I recommend 2 because occasionally a new kernel will have problems and it's a good idea to have the last known working kernel just in case.

You can also choose whether or not to display the Recovery and MemTest options. I recommend keeping the Recovery options because they can come in very handy occasionally, but how often is MemTest used?

I hope this gets things sorted.

---

### Post by dbowlin17 on 2010-01-31
I really appreciate the time you have been putting towards helping solve my issues. I got that startup manager, but the thing is, I don't see how to do as you said. I have attatched a screen shot of the window. I am using grub2. It detected 7 and XP.

---

### Post by louieb on 2010-01-31
You have Grub legacy v0.97 not GRUB2. 

Widows has a weird way of multi booting - just wondering when you boot win 7 do you get if you get a menu that allows you to choose XP or win 7?

But having said that it looks like both should be able to boot from grub. 

Try selecting XP then start pressing F8 and see if you can get the XP boot menu and select safe mode. Then run chkdsk.

---

### Post by dbowlin17 on 2010-01-31
I am about to test the xp boot. I actually just upgraded to grub2, since i ran that boot info script.

---

### Post by kansasnoob on 2010-01-31
> **dbowlin17 said:**
> I really appreciate the time you have been putting towards helping solve my issues. I got that startup manager, but the thing is, I don't see how to do as you said. I have attatched a screen shot of the window. I am using grub2. It detected 7 and XP.

You were using legacy grub when you ran the Boot Info Script :P

---

### Post by dbowlin17 on 2010-01-31
right, I said that i upgraded since running the script. so now i can boot to all 3 operating systems. yay! although, with my monitor, when going between windows and linux there is about 1/2 a centimeter that the display is off by. is there a way to adjust the linux one so i don't have to keep hitting the auto adjust on my monitor each time?

---

### Post by kansasnoob on 2010-01-31
> **dbowlin17 said:**
> I am about to test the xp boot. I actually just upgraded to grub2, since i ran that boot info script.

What method did you use to upgrade to grub2?

If you have mixed legacy grub and grub2 files in /boot/grub you're going to end up with lots of problems.

To look run:

```
ls /boot/grub
```

Everything is in alphabetical order. If you see both a "grub.cfg" and a "menu.lst" you'll have problems at some point.

---

### Post by dbowlin17 on 2010-01-31
i have the grub.cfg and then the following 3: menu.lst menu.lst~ and menu.lst_backup_by_grub2_postinst

i used terminal to get grub2. should i be removing those three files? grub legacy is gone.

---

### Post by kansasnoob on 2010-01-31
> **dbowlin17 said:**
> i have the grub.cfg and then the following 3: menu.lst menu.lst~ and menu.lst_backup_by_grub2_postinst

i used terminal to get grub2. should i be removing those three files? grub legacy is gone.

```
sudo mv /boot/grub /boot/grub_backup
```

```
sudo mkdir /boot/grub
```

```
sudo apt-get install --reinstall grub-common grub-pc
```

```
sudo update-grub
```

Wait for it to say done.

That should be it.

---

### Post by dbowlin17 on 2010-01-31
all those menu things are gone. great. is there a way for me to adjust my screen settings so i don't have to hit my auto adjust button on my monitor when going between windows and linux

---

### Post by kansasnoob on 2010-02-01
That's an Xorg thing and I'm woefully ignorant when it comes to that.

---

