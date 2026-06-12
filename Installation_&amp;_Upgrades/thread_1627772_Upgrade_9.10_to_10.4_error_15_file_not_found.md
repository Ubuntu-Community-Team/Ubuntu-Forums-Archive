---
title: "Upgrade 9.10 to 10.4: error 15 file not found"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by DawgMan on 2010-11-21
Fairly new to ubuntu. Dell Laptop D830.  Dual boot XP and Ubuntu.

Upgrading from update manager to 10.04 LTS.  Upgrade went fine, but, asked me which menu.lst to use.  The default was Keep the current menu.lst. When hovering over it said modifications were made to my version.  The other choice was the developer copy.  I took the default.

When rebooting, my old menu.lst came up as it listed 9.10.

So I added a section about 10.04 LTS using /boot/vmlinuz-2.6.32-25-generic assuming that is the new 10.04 kernel.

When I boot to 10.04 LTS I get:

Error 15: File not found

Press any key to continue...

When I boot to 9.10 I get:

Mount: mounting none on /dev failed: No such device61f7538854
Starting up ...

I eventually boots up.



```


dan@dan-ubuntu:~$ ls -l /boot
total 42196
-rw-r--r-- 1 root root  524784 2009-10-20 17:27 abi-2.6.28-16-generic
-rw-r--r-- 1 root root  624277 2010-03-12 01:45 abi-2.6.31-20-generic
-rw-r--r-- 1 root root  646144 2010-10-16 16:37 abi-2.6.32-25-generic
-rw-r--r-- 1 root root   90655 2009-10-20 17:27 config-2.6.28-16-generic
-rw-r--r-- 1 root root  105779 2010-03-12 01:45 config-2.6.31-20-generic
-rw-r--r-- 1 root root  110600 2010-10-16 16:37 config-2.6.32-25-generic
drwxr-xr-x 2 root root    4096 2010-11-21 19:18 grub
-rw-r--r-- 1 root root 7064316 2010-11-21 01:39 initrd.img-2.6.28-16-generic
-rw-r--r-- 1 root root 7739792 2010-11-21 09:51 initrd.img-2.6.31-20-generic
-rw-r--r-- 1 root root 8338819 2010-11-21 10:09 initrd.img-2.6.32-25-generic
-rw-r--r-- 1 root root  160280 2010-03-23 05:40 memtest86+.bin
-rw-r--r-- 1 root root 1864822 2009-10-20 17:27 System.map-2.6.28-16-generic
-rw-r--r-- 1 root root 2133277 2010-03-12 01:45 System.map-2.6.31-20-generic
-rw-r--r-- 1 root root 2155696 2010-10-16 16:37 System.map-2.6.32-25-generic
-rw-r--r-- 1 root root    1170 2009-10-20 17:32 vmcoreinfo-2.6.28-16-generic
-rw-r--r-- 1 root root    1336 2010-03-12 01:52 vmcoreinfo-2.6.31-20-generic
-rw-r--r-- 1 root root    1336 2010-10-16 16:38 vmcoreinfo-2.6.32-25-generic
-rw-r--r-- 1 root root 3513536 2009-10-20 17:27 vmlinuz-2.6.28-16-generic
-rw-r--r-- 1 root root 3947008 2010-03-12 01:45 vmlinuz-2.6.31-20-generic
-rw-r--r-- 1 root root 4050592 2010-10-16 16:37 vmlinuz-2.6.32-25-generic
dan@dan-ubuntu:~$ 


```

my menu.lst

```


## ## End Default Options ##

title		Ubuntu 10.04 LTS, kernel 2.6.32-25-generic
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854	
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic


```

fstab:

```


dan@dan-ubuntu:~$ sudo fdisk -lu
[sudo] password for dan: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf9b45fa1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   204796619   102398278+   7  HPFS/NTFS
/dev/sda2       204796620   976768064   385985722+   5  Extended
/dev/sda5       204796683   964847834   380025576   83  Linux
/dev/sda6       964847898   976768064     5960083+  82  Linux swap / Solaris
dan@dan-ubuntu:~$ 


```

Not sure where to go from here.

---

### Post by sikander3786 on 2010-11-23
You can follow this link in order to install Grub2.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Or post the output of bootinfoscript as per instructions here to let us figure it out for you.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Post the complete text from Results.txt.

Thanks.

---

### Post by DawgMan on 2010-11-23
Here is the results.txt

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

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

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   976,768,064   771,971,445   5 Extended
/dev/sda5         204,796,683   964,847,834   760,051,152  83 Linux
/dev/sda6         964,847,898   976,768,064    11,920,167  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        266C51FD6C51C867                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cd0c7441-38d1-4e1f-a206-b161f7538854   ext3                                     
/dev/sda6        6e553533-d163-46f3-b633-deb66deb8210   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

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
timeout		5

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
# kopt=root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cd0c7441-38d1-4e1f-a206-b161f7538854

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-25-generic
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854	
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, memtest86+
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=6e553533-d163-46f3-b633-deb66deb8210 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sda1 /media/Disk2 ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 362.9GB: boot/grub/menu.lst
 362.8GB: boot/grub/stage2
 366.9GB: boot/initrd.img-2.6.28-16-generic
 367.4GB: boot/initrd.img-2.6.31-20-generic
 367.4GB: boot/initrd.img-2.6.32-25-generic
 362.8GB: boot/vmlinuz-2.6.28-16-generic
 374.7GB: boot/vmlinuz-2.6.31-20-generic
 362.9GB: boot/vmlinuz-2.6.32-25-generic
 367.4GB: initrd.img
 362.9GB: vmlinuz

```

Any help would be great.

---

### Post by oldfred on 2010-11-24
I have not followed what the latest old grub legacy would create in a menu.lst. Did you copy the current entries? Usually you have a root or rootnoverify entry, not the UUID line.

Try this

title    Most Current Ubuntu on sda5
root    (hd0,4)
linux   /vmlinuz root=/dev/sda5 ro quiet splash
initrd  /initrd.img


Or change UUID line:

title        Ubuntu 10.04 LTS, kernel 2.6.32-25-generic
[COLOR=Red]root        (hd0,4) [/COLOR]   
kernel        /boot/vmlinuz-2.6.32-25-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic
quiet

---

### Post by DawgMan on 2010-11-26
Thanks, oldfred.  I tried that, it didn't work.

tried to reinstall grub via:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

but now I just boot to the grub> prompt.

I haven't tried method 3 from the above link because now I'm not sure I'm going in the right direction.

Boot now shows:

GNU GRUB version 1.98-1ubuntu7.

---

### Post by sikander3786 on 2010-11-26
Boot from a Live CD and do these commands.

```
sudo mount /dev/sda5 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Note, for the second one it is just sda and not sda5.

Reboot and see if you can boot Ubuntu successfully.

If still no joy, please once again post the output of bootinfoscript in order to see what is wrong there.

---

### Post by oldfred on 2010-11-26
Now you have grub2. Grub & grub2 often do not get along and it is better just to uninstall both and reinstall grub2.

chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by DawgMan on 2010-11-26
OK, grub-install finished. No errors reported. Still boots to grub>

here is RESULTS.txt

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

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620   976,768,064   771,971,445   5 Extended
/dev/sda5         204,796,683   964,847,834   760,051,152  83 Linux
/dev/sda6         964,847,898   976,768,064    11,920,167  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        266C51FD6C51C867                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        cd0c7441-38d1-4e1f-a206-b161f7538854   ext3                                     
/dev/sda6        6e553533-d163-46f3-b633-deb66deb8210   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /mnt                     ext3       (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

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
timeout		5

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
# kopt=root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cd0c7441-38d1-4e1f-a206-b161f7538854

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-25-generic
# root		(hd0,4)
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854	
kernel		/boot/vmlinuz-2.6.32-25-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet 
# kernel		/boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 ro quiet
splash 
initrd		/boot/initrd.img-2.6.32-25-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, memtest86+
uuid		cd0c7441-38d1-4e1f-a206-b161f7538854
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=cd0c7441-38d1-4e1f-a206-b161f7538854 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=6e553533-d163-46f3-b633-deb66deb8210 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sda1 /media/Disk2 ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda5: Location of files loaded by Grub: ===================


 362.9GB: boot/grub/core.img
 362.9GB: boot/grub/menu.lst
 362.8GB: boot/grub/stage2
 366.9GB: boot/initrd.img-2.6.28-16-generic
 367.4GB: boot/initrd.img-2.6.31-20-generic
 367.4GB: boot/initrd.img-2.6.32-25-generic
 362.8GB: boot/vmlinuz-2.6.28-16-generic
 374.7GB: boot/vmlinuz-2.6.31-20-generic
 362.9GB: boot/vmlinuz-2.6.32-25-generic
 367.4GB: initrd.img
 362.9GB: vmlinuz

```

Going to try Purge and Reinstall Grub 2 from the Live CD

---

### Post by DawgMan on 2010-11-26
Purged and reinstalled grub 2

thanks

---

