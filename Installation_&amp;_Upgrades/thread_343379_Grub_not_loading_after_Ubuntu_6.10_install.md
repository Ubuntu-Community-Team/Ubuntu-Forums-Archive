---
title: "Grub not loading after Ubuntu 6.10 install"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by montgoss on 2007-01-21
I've tried to install Ubuntu before on this machine,but had the same error with Dapper Drake. II thought I'd give it another shot with the latest Ubuntu, Edgy.

Essentially, everything goes fine during the install.  But on reboot, Grub doesn't show up on the screen and the machine boots straight to Windows.  My windows and Ubuntu partitions are on the same SATA drive.  If it matters, I believe Ubuntu and Grub see that SATA drive as the secondary hard drive.  In other words, there is a sba1 that has data, but Windows is on sdb1 and Ubuntu on sdb2.  I also have an extended partition(sdb3) that contains an NTFS data parition(sdb5) and the linux-swap partition(sdb6).  (I don't know where sdb4 went).

In the last step of the install is when Grub seems to be loaded.  If there is a way to install Grub without doing a full re-install of Ubuntu, deleting the Ubuntu partition and recopying the data down, that would really help in troubleshooting!  Anyways...  On the first install attempt, I accepted the default install location (hd0 I believe) for Grub.  The machine booted straight to Windows.  So, I tried again and told Grub to go to (sdb0).  This time the install gives an error:> Title: Unable to install GRUB in (sdb0)
Executing 'grub-install (sdb0)' failed.
This is a fatal error.

I then tried installing to sdb1.  That worked as far as the installer was concerned.  But then the machine wouldn't boot period.  Neither Windows nor Ubuntu attempted to boot.  The BIOS threw an error about non-system disk, I believe.  Reinstalling Ubuntu with GRUB going to the default location made it so Windows now automatically boots again.  But still no GRUB and no Ubuntu.

So, where/how do I get GRUB to load at startup and boot Ubuntu?


I'd appreciate any help ASAP.  I got my server setup with MythTV.  But I can't use the MythTV frontend in Windows XP on this machine.  Help me get Ubuntu working and I may just trash the Windows partition...

---

### Post by bernied on 2007-01-21
You can set up grub using the grub console. This usually works when grub-install fails. You can do this using the ubuntu live-cd.

So, get a terminal in the live-cd, and type:
```
sudo grub
```
You are now in the grub console.

It is very important to know where grub thinks everything is, because this is different to where linux thinks everything is. It is this confusion of locations that has probably caused the problem.

You only need two commands, but finding out what parameters to use for the first one might be challenging.

So the commands are:
root (hdx,y)   - it's the x and the y that you need to find out
and
setup (hd0)

So, to find out what x and y are, you need to find your linux install using grub. You can do this using tab-completion. I'm going to let Herman explain the rest because he's written a huge how-to on the topic - but you only need [this bit](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer)

Tell us how you get on.

---

### Post by bernied on 2007-01-21
To clarify, x is the hard drive where grub thinks your linux install is - this is probably 1 (in grub's terms, the second hard disk), but it might also be 0 (the first disk), y is the partition on that drive, this is much-more-probably 1 (the second partition on the drive).

I've just realised that grub may see the cd as hd0, in which case that second command should be 
```
setup (hd1)
```not (hd0)

How many disks do you have?

---

### Post by bulldog on 2007-01-21
You can do two things,boot from sda where GRUB should be now,or reinstall GRUB on sdb and boot from this hdd.
To reinstall GRUB to the correct hdd you'll have to find out how ubuntu see the boot order.
```
cat /boot/grub/device.map
``` will give you that info.

Give us the output of the cat command and we can tell you how to reinstall GRUB with the live cd.

---

### Post by montgoss on 2007-01-21
While waiting for a reply and browsing the forums, another post sparked an idea.  So, I did another reinstall and told GRUB to go to (hd1).  Now GRUB loads on startup!  But now neither Windows nor Ubuntu will boot!!  :confused: 

If I select the first option in the GRUB menu, Ubuntu, kernel 2.6.17-10-generic, I get:> Error 22: No such partition

If I select the Windows XP option in the GRUB menu, I get:> NTLDR is missing.
Press Ctrl + Alt + Del to restart

I press 'e' to edit the GRUB command for Ubuntu.  The first line was "root (hd1,1)"

I ran "sudo grub" and followed instructions from bernied's link.  I typed "find /vmlinuz" and it returns "(hd1,1)"

So, I ran your two commands:```
grub> root (hd1,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd1,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.
```
It thinks it worked.  I'll reboot right now and reply with the results.

> **bulldog said:**
> You can do two things,boot from sda where GRUB should be now,or reinstall GRUB on sdb and boot from this hdd.
To reinstall GRUB to the correct hdd you'll have to find out how ubuntu see the boot order.
```
cat /boot/grub/device.map
``` will give you that info.

Give us the output of the cat command and we can tell you how to reinstall GRUB with the live cd.The output of that command is: ```
cat: /boot/grub/device.map: No such file or directory
```

Reading more on bernied's link, I ran your command from the command line inside grub (ie, after running "sudo grub"):> grub> cat (hd1,1)/boot/grub/device.map 
(hd0)       /dev/sda
(hd1)       /dev/sdb

---

### Post by montgoss on 2007-01-21
Ok.  I rebooted after running the grub "setup (hd0)" thing.  Same errors as before when I try to boot Ubuntu or Windows.  While at the GRUB menu, I also opened a command line and tried "setup (hd1)".  That made no difference.

What should I do next?  ](*,)

---

### Post by bernied on 2007-01-21
Right, so there are a couple of things going funny with your install. Even when grub started ok you still couldn't boot - this will be because the grub configuration file, which is called menu.lst, is not written properly. This file is custom-made for your PC during the installation process. There is something a bit different about your machine which the installer is not handling properly. But we can fix it manually.

You didn't answer my question about how many disks you have - are there two? Could you please show the output from 
```
sudo fdisk -l
```
this is a list of all your disks and partitions.

This is a bit of a guess, but I think you should try this.
First, from a grub console (terminal on the Live CD, then 'sudo grub'):
```
root (hd1,1)
setup (hd1)
```
this should enable grub to start on bootup. Try rebooting.
If grub doesn't start then you can't do the next bit.

If grub does start, then select the first ubuntu option, but don't hit enter, instead hit the 'e' key (for edit). The first line will probably be:
```
root (hd0,1)
```
but should probably be:
```
root (hd1,1)
```
while you are here, please write down (the old-fashioned way) everything in that entry, starting with the 'root' line, but including the 'kernel' and 'initrd' lines as well.

Once you have changed the hd0 to hd1, hit 'b' to boot. This may not work, but don't panic. Does the kernel start? Do you get a load of messages? It may end with a 'kernel panic' line, when you will have to a cold reboot. This will be because the 'kernel' options are also wrong, specifically the 'root=' option.

This may be 'root=sda2' but should probably be 'root=sdb2'. If you got a kernel panic, go back and repeat the above, this time changing both lines, the 'root' line and the 'kernel' line.

Write down the options that work, you will need to change these in your menu.lst file.

If you get this far, the file is at /boot/grub/menu.lst (but only when you have your installed ubuntu running, not when running the live-cd) and you can edit it with nano. Only do this once you have your installed ubuntu running, not from live cd:
```
sudo nano /boot/grub/menu.lst
```

---

### Post by bernied on 2007-01-21
When I asked you to write that stuff down, it was because it would be useful to see it - so please post it here, along with the output from the fdisk -l command.

---

### Post by montgoss on 2007-01-21
> **bernied said:**
> Right, so there are a couple of things going funny with your install. Even when grub started ok you still couldn't boot - this will be because the grub configuration file, which is called menu.lst, is not written properly.

**/boot/grub/menu.lst**
```
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=53bfd851-761a-49df-bddb-e624acba7b97 ro
# kopt_2_6=root=/dev/sdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
#title		Microsoft Windows XP Professional
#root		(hd1,0)
#savedefault
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1

title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd0,0)
savedefault
makeactive
chainloader	+1
``` *Note: There are two entries for WinXP because I tried something another post suggested.  It still wouldn't allow WinXP to boot.*

Other people have asked for **/etc/fstab** too.  Here it is just in case it helps:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=53bfd851-761a-49df-bddb-e624acba7b97 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=1CF468E4F468C21E /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb1
UUID=6A8C6A338C69FA49 /media/sdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb5
UUID=D490BAC790BAAEFC /media/sdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sdb6
UUID=7cdd9ff6-e351-46af-8e31-1270382aafe1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


> **bernied said:**
> You didn't answer my question about how many disks you have - are there two? Could you please show the output from 
```
sudo fdisk -l
```
this is a list of all your disks and partitions.

There are two SATA drives.  Here's the output of **fdisk -l**
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14023   112639716    7  HPFS/NTFS
/dev/sdb2           14024       16637    20996955   83  Linux
/dev/sdb3           16638       38913   178931970    f  W95 Ext'd (LBA)
/dev/sdb5           16638       38651   176827423+   7  HPFS/NTFS
/dev/sdb6           38652       38913     2104483+  82  Linux swap / Solaris
```


> **bernied said:**
> This is a bit of a guess, but I think you should try this.
First, from a grub console (terminal on the Live CD, then 'sudo grub'):
```
root (hd1,1)
setup (hd1)
```
this should enable grub to start on bootup. Try rebooting.
If grub doesn't start then you can't do the next bit.I tried this before.  My last reply was about what happened.  GRUB loads, but neither Ubuntu nor Windows XP will boot.

> **bernied said:**
> If grub does start, then select the first ubuntu option, but don't hit enter, instead hit the 'e' key (for edit). The first line will probably be:
```
root (hd0,1)
```
but should probably be:
```
root (hd1,1)
```
while you are here, please write down (the old-fashioned way) everything in that entry, starting with the 'root' line, but including the 'kernel' and 'initrd' lines as well.The lines there match the above posting of menu.lst.  As you can see, the root line is already (hd1,1).  I changed it to (hd0,1) out of curiosity, and it actually booted into Ubuntu!  WTF?  But, Ubuntu seems to work!!

I'm going to try changing the equivalent line for Windows XP and see if it will boot that too.

BTW, I was able to get the menu.lst file from the LiveCD.  I mounted the linux partition:```
mkdir ./sdb2
sudo mount /dev/sdb2/ ./sdb2/
sudo gedit ./sdb2/boot/grub/menu.lst
```

OK, I removed the ```
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
```from the Windows XP boot settings and Windows booted too.

I think everything works!   :biggrin:

---

