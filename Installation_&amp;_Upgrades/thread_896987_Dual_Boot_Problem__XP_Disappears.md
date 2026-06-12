---
title: "Dual Boot Problem:  XP Disappears"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by strfish7 on 2008-08-21
Hello, 
I've posted once before on this issue, but didn't have time to follow up.  I've attempted to install Hardy as a dual boot with XP, but I believe the partitioning got messed up. XP shows as an operating system in the boot menu, but highlighting it and attempting to boot produces a blinking cursor.  Any Windows commands are met with 'invalid command.'  Hardy boots up fine.  My output to sudo fdisk -lu is as follows

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa7ca49d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   180217170   312576704    66179767+   7  HPFS/NTFS
/dev/sda2              63   180217169    90108553+   5  Extended
/dev/sda5             126     3903794     1951834+  82  Linux swap / Solaris
/dev/sda6         3903858    23968979    10032561   83  Linux
/dev/sda7        23969043   180217169    78124063+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 65 MB, 65534976 bytes
3 heads, 42 sectors/track, 1015 cylinders, total 127998 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x69737369

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  1869771365  2038460886    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(14839455, 0, 36)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(16178261, 0, 1)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?  1701519481  3571400945   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(13504122, 2, 26)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(28344451, 2, 36)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?        2573        2573           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(20, 1, 12)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(20, 1, 11)
Partition 3 does not end on cylinder boundary.
/dev/sdb4               0  3435113471  1717556736    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(27262805, 0, 42)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Needless to say, this doesn't look right, even to my newb eyes.  Any suggestions on how to put this right?  Thanks.

---

### Post by niyonk on 2008-08-21
You forgot to give the output of your /boot/grub/menu.lst that is where the Xp entry is loaded from.

I did notice you have cylinder boundary errors...I suggest you back-up your Linux files and wipe the partitions.
Then re-partition from Windows...that is how i got rid of the error the last time i got it.

Good Luck! :)

---

### Post by caljohnsmith on 2008-08-21
So do you know what drive is "sdb"? fdisk shows it is only 65 MB. Anyway, as long as you can boot into Hardy, please post the following:
```
cat /boot/grub/menu.lst
```
Also, can you mount your Windows partition successfully in Hardy? If it isn't all ready being mounted on startup, try doing:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
```

---

### Post by strfish7 on 2008-08-21
Oops, sdb is just a thumb drive I accidentally left in one of the usb ports.

Here's the output for cat/grub/menu.1st:
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
# kopt=root=UUID=4790eeb6-0a2a-4f44-b134-ae0d347cd371 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4790eeb6-0a2a-4f44-b134-ae0d347cd371 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=4790eeb6-0a2a-4f44-b134-ae0d347cd371 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4790eeb6-0a2a-4f44-b134-ae0d347cd371 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=4790eeb6-0a2a-4f44-b134-ae0d347cd371 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4790eeb6-0a2a-4f44-b134-ae0d347cd371 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=4790eeb6-0a2a-4f44-b134-ae0d347cd371 ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4790eeb6-0a2a-4f44-b134-ae0d347cd371 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4790eeb6-0a2a-4f44-b134-ae0d347cd371 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Here's the output from the second command:


carl@Helios:~$ sudo mount /dev/sda1 /mnt
fuse: mount failed: Device or resource busy
carl@Helios:~$ ls -l /mnt
total 1671271
drwxrwx--- 1 root plugdev          0 2007-06-14 08:30 3199e86af0bedfb2a86a
drwxrwx--- 1 root plugdev          0 2005-05-03 16:39 adaptec
-rwxrwx--- 1 root plugdev          0 2003-08-13 07:43 AUTOEXEC.BAT
-rwxrwx--- 1 root plugdev        212 2007-04-04 08:13 boot.ini
-rwxrwx--- 2 root plugdev        211 2006-03-31 17:13 boot.ini.comodofirewall
drwxrwx--- 1 root plugdev       4096 2008-05-09 13:31 Config.Msi
-rwxrwx--- 1 root plugdev          0 2003-08-13 07:43 CONFIG.SYS
drwxrwx--- 1 root plugdev          0 2005-09-15 08:38 d3temp(2)
drwxrwx--- 1 root plugdev       4096 2007-09-21 17:04 DiabloSpawn
drwxrwx--- 1 root plugdev       4096 2007-08-29 13:48 Documents and Settings
-rwxrwx--- 2 root plugdev         99 2005-07-15 17:08 DownloadLog.txt
drwxrwx--- 1 root plugdev          0 2003-08-13 08:42 Drivers
-rwxrwx--- 1 root plugdev 1006161920 2008-05-21 15:30 hiberfil.sys
-rwxrwx--- 1 root plugdev          0 2003-08-13 07:43 IO.SYS
-rwxrwx--- 1 root plugdev       2024 2007-06-08 16:43 IPH.PH
-rwxrwx--- 1 root plugdev        355 2002-12-31 23:12 mmcInst.log
drwxrwx--- 1 root plugdev       4096 2007-10-08 10:44 Movies
-rwxrwx--- 1 root plugdev       1782 2004-12-12 15:19 Mp3FE.m3u
-rwxrwx--- 1 root plugdev          0 2003-08-13 07:43 MSDOS.SYS
drwxrwx--- 1 root plugdev          0 2006-06-07 08:26 MSOCache
drwxrwx--- 1 root plugdev          0 2005-07-15 17:08 My Download Files
drwxrwx--- 1 root plugdev          0 2005-07-15 17:08 My Games
drwxrwx--- 1 root plugdev       4096 2007-06-15 13:36 My Music
drwxrwx--- 1 root plugdev      28672 2007-09-17 10:46 My Shared Folder
-rwxrwx--- 1 root plugdev      47564 2004-10-10 18:31 NTDETECT.COM
-rwxrwx--- 1 root plugdev     250032 2004-10-10 18:31 ntldr
-rwxrwx--- 1 root plugdev  704643072 2008-05-21 15:30 pagefile.sys
drwxrwx--- 1 root plugdev      28672 2008-06-18 14:15 Program Files
drwxrwx--- 1 root plugdev       4096 2004-10-10 18:41 System Volume Information
drwxrwx--- 1 root plugdev          0 2007-09-21 16:38 TEMP
drwxrwx--- 1 root plugdev     180224 2008-05-20 15:43 WINDOWS
-rwxrwx--- 1 root plugdev        146 2007-01-02 18:04 YServer.txt
carl@Helios:~$

---

### Post by niyonk on 2008-08-21
well, from what i can see...your partition was already mounted and menu.lst seems fine with me..

Well, grub should not remove XP's bootloader. Are you sure you were still able to log into XP before you installed Ubuntu??

Maybe something in your boot.ini can tell us where u are going wrong.

---

### Post by caljohnsmith on 2008-08-21
Your Windows entry in menu.lst appears to be correct based on the information you have provided so far. That would make sense since Grub did not return an error when you tried booting Windows, so it is a high probability that the problem is with Windows. In case you haven't done all ready, be sure to back up any of your important Windows files from Ubuntu.

If you have the Windows Install CD, I would recommend booting that, going into the recovery console, and running "chkdsk" on your Windows partition. Also, run "fixboot" to make sure the boot sector of your Windows partition is OK. But whatever you do, don't run "fixmbr" since that will replace your Grub with the Windows boot loader. Let me know if you need any more details.

---

### Post by strfish7 on 2008-08-21
Thanks for the suggestions...I'll try the Windows startup disk and let you know what happens.

(later)  Well, running chkdsk and fixboot, apparently, did not cause any change.  Still can't boot into XP, nor does any partition show in Hardy. Any other thoughts, guys?

---

### Post by niyonk on 2008-08-21
Well, the last thing you could try is fixmbr.
After that, you can restore grub using the Live CD.
Knowing that the XP bootloader works is what you need to know. 
Grub just calls it...

---

### Post by caljohnsmith on 2008-08-21
> **strfish7 said:**
> Thanks for the suggestions...I'll try the Windows startup disk and let you know what happens.

(later)  Well, running chkdsk and fixboot, apparently, did not cause any change.  Still can't boot into XP, nor does any partition show in Hardy. Any other thoughts, guys?
Do you mean if you run "sudo fdisk -l" you don't see sda1? That should be your Windows partition. It is probably all ready set up to mount on startup in your /etc/fstab. Try the following though:
```
sudo umount /dev/sda1
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Does that list the files and folders in your root Windows directory?

P.S. I wouldn't recommend running fixmbr, because it will replace Grub with the Windows boot loader. That's not too big deal since you can reinstall Grub, but since Grub is not returning any errors when booting Windows (and you have your menu.lst set correctly), I think Windows is the problem and not Grub. And the Windows boot loader does essentially the same thing as Grub--it "chainloads" your Windows partition.

---

### Post by DavidTangye on 2008-08-21
> **caljohnsmith said:**
>  Try the following though:
```
sudo umount /dev/sda1
sudo mount -t ntfs /dev/sda1 /mnt
ls -l /mnt
```This would be better
```
sudo mkdir /mnt/sda1 # In case its not already there
sudo umount /mnt/sda1 # In case it IS there and is mounted already
sudo mount -t ntfs /dev/sda1 /mnt/sda1
ls -l /mnt/sda1
```If other words, never mount to /mnt directly in case other mounts are mounted to /mnt/(other subdirectories). Instead always mount to subdirectories. In the first example in an earlier message above the mount probably failed for this reason.

If you ```
cat /etc/fstab
``` you should find mention of sda1, and the line that follows it will show exactly where it would normally be mounted, eg something like this line > UUID=a592808b-65b3-42e5-8a68-b600e6edaefc /mnt/sda1       ntfs    ro,users,suid,dev,noexec,async,noauto 0       0Make sure it says 'ntfs', meaning that by default the system will try to mount it as an ntfs filesystem, not a linux(ie ext3)  one.

---

### Post by strfish7 on 2008-08-21
sudo fdisk -1 yields

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7ca49d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       11219       19457    66179767+   7  HPFS/NTFS
/dev/sda2               1       11218    90108553+   5  Extended
/dev/sda5               1         243     1951834+  82  Linux swap / Solaris
/dev/sda6             244        1492    10032561   83  Linux
/dev/sda7            1493       11218    78124063+  83  Linux

udo umount /mnt/sda1 yields

carl@Helios:~$ sudo umount /mnt/sda1
umount: /mnt/sda1: not mounted

and this

carl@Helios:~$ sudo mount -t ntfs /dev/sda1 /mnt/sda1
carl@Helios:~$ ls -l /mnt/sda1
total 983147
drwxrwx--- 1 root plugdev          0 2007-06-14 08:30 3199e86af0bedfb2a86a
drwxrwx--- 1 root plugdev          0 2005-05-03 16:39 adaptec
-rwxrwx--- 1 root plugdev          0 2003-08-13 07:43 AUTOEXEC.BAT
-rwxrwx--- 1 root plugdev       2788 2008-08-21 12:44 bootex.log
-rwxrwx--- 1 root plugdev        212 2007-04-04 08:13 boot.ini
-rwxrwx--- 2 root plugdev        211 2006-03-31 17:13 boot.ini.comodofirewall
drwxrwx--- 1 root plugdev       4096 2008-05-09 13:31 Config.Msi
-rwxrwx--- 1 root plugdev          0 2003-08-13 07:43 CONFIG.SYS
drwxrwx--- 1 root plugdev          0 2005-09-15 08:38 d3temp(2)
drwxrwx--- 1 root plugdev       4096 2007-09-21 17:04 DiabloSpawn
drwxrwx--- 1 root plugdev       4096 2007-08-29 13:48 Documents and Settings
-rwxrwx--- 2 root plugdev         99 2005-07-15 17:08 DownloadLog.txt
drwxrwx--- 1 root plugdev          0 2003-08-13 08:42 Drivers
-rwxrwx--- 1 root plugdev 1006161920 2008-05-21 15:30 hiberfil.sys
-rwxrwx--- 1 root plugdev          0 2003-08-13 07:43 IO.SYS
-rwxrwx--- 1 root plugdev       2024 2007-06-08 16:43 IPH.PH
-rwxrwx--- 1 root plugdev        355 2002-12-31 23:12 mmcInst.log
drwxrwx--- 1 root plugdev       4096 2007-10-08 10:44 Movies
-rwxrwx--- 1 root plugdev       1782 2004-12-12 15:19 Mp3FE.m3u
-rwxrwx--- 1 root plugdev          0 2003-08-13 07:43 MSDOS.SYS
drwxrwx--- 1 root plugdev          0 2006-06-07 08:26 MSOCache
drwxrwx--- 1 root plugdev          0 2005-07-15 17:08 My Download Files
drwxrwx--- 1 root plugdev          0 2005-07-15 17:08 My Games
drwxrwx--- 1 root plugdev       4096 2007-06-15 13:36 My Music
drwxrwx--- 1 root plugdev      28672 2007-09-17 10:46 My Shared Folder
-rwxrwx--- 1 root plugdev      47564 2004-10-10 18:31 NTDETECT.COM
-rwxrwx--- 1 root plugdev     250032 2004-10-10 18:31 ntldr
drwxrwx--- 1 root plugdev      28672 2008-06-18 14:15 Program Files
drwxrwx--- 1 root plugdev       4096 2004-10-10 18:41 System Volume Information
drwxrwx--- 1 root plugdev          0 2007-09-21 16:38 TEMP
drwxrwx--- 1 root plugdev     180224 2008-05-20 15:43 WINDOWS
-rwxrwx--- 1 root plugdev        146 2007-01-02 18:04 YServer.txt


Finally

carl@Helios:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=4790eeb6-0a2a-4f44-b134-ae0d347cd371 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=1a504d16-a009-469c-82bd-88666b259ca1 /home           ext2    relatime        0       2
# /dev/sda1
UUID=C4C8DC74C8DC65E8 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=79575f54-04a2-4f3c-9cd9-2dbf313ea223 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 

Please understand, I've no idea what I'm looking at here.  Thank you for the help.

---

### Post by caljohnsmith on 2008-08-21
So it looks like you can access your Windows partition just fine. I would recommend you make a backup of any important Windows files at this point. 

So when you try and boot into Windows, is it still the same thing--you get a blinking cursor? Or do you get any errors? How soon after you boot Windows from Grub does it hang--immediately or does it try and load some stuff? Any other details you can provide about booting Windows would be helpful.

While you have Windows mounted on /mnt/sda1, please post the output of the following:
```
cat /mnt/sda1/boot.ini 
```

---

### Post by DavidTangye on 2008-08-21
> **strfish7 said:**
> Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       11219       19457    66179767+   7  HPFS/NTFS
/dev/sda2               1       11218    90108553+   5  Extended
/dev/sda5               1         243     1951834+  82  Linux swap / Solaris
/dev/sda6             244        1492    10032561   83  Linux
/dev/sda7            1493       11218    78124063+  83  LinuxShow your partitions and start and end locations, notably:

[LIST]
[*] /dev/sda1 is ntfs format
[*] /dev/sda2 is an 'extended partition' marker, ie the following partitions are within it.
[*] /dev/sda3 is type 82, ie your swap partition
[*] /dev/sda6 and 7 are type 83, ie linux ext3 partitions. At least one will be for /, ie root
[/LIST]
 
> **strfish7 said:**
> sudo umount /mnt/sda1 yields

carl@Helios:~$ sudo umount /mnt/sda1
umount: /mnt/sda1: not mountedNo problem - the partition was not yet already mounted at this mount-point, as we expected because we had just defined the mount-point, with teh mkdir (make directory) command (ie an empty subdirectory is the usual location for a mount-point for partitions).

> **strfish7 said:**
> carl@Helios:~$ sudo mount -t ntfs /dev/sda1 /mnt/sda1
carl@Helios:~$ ls -l /mnt/sda1
total 983147
drwxrwx--- 1 root plugdev          0 2007-06-14 08:30 3199e86af0bedfb2a86a
drwxrwx--- 1 root plugdev          0 2005-05-03 16:39 adaptec
-rwxrwx--- 1 root plugdev          0 2003-08-13 07:43 AUTOEXEC.BAT
-rwxrwx--- 1 root plugdev       2788 2008-08-21 12:44 bootex.log
-rwxrwx--- 1 root plugdev        212 2007-04-04 08:13 boot.ini
-rwxrwx--- 2 root plugdev        211 2006-03-31 17:13 boot.ini.comodofirewall
....Shows that the mount command worked, and ls -l is a 'long format' listing of the windows partition's root directory now mounted at that mount-point.

> **strfish7 said:**
> carl@Helios:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# /dev/sda6
UUID=4790eeb6-0a2a-4f44-b134-ae0d347cd371 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=1a504d16-a009-469c-82bd-88666b259ca1 /home           ext2    relatime        0       2
# /dev/sda1
UUID=C4C8DC74C8DC65E8 /windows        ntfs    defaults,umask=007,gid=46 0       1Are the interesting bits of your filesystem table 'fstab'. It defines where and how the above partitions are mounted. 

Note that the Windows partition should be already mounted at /windows, so you now have it mounted twice. If you like, you can now do this
```
sudo umount /dev/sda1
```because we do not need this second mount point,. We can just use the original one that Ubuntu provided at install time, ie the /windows one, and we can for instance```
cat /windows/boot.ini
``` instead of ```
cat /mnt/sda1/boot.ini
``` to read the windows boot.ini file.

ps Instead of looking at /etc/fstab the command 'mount' shows what is actually mounted at this time. Try it. You will see that the information is formatted much like in the /etc/fstab. Also, if you run ```
mount|grep sda
``` you will get the output of the mount command filtered to just lines with sda, so cutting out the uninteresting stuff.

---

### Post by mike_f on 2008-08-21
As an alternative to repartitioning from Windows, get the free [System Rescue CD]("http://www.sysresccd.org/") and boot with it (after backing up all important data, of course). Type 'startx' to get the graphical desktop and click the gparted icon to run the graphical partitioner. It may offer to fix the partition table which may or may not destroy working partitions. 
You can also resize existing partitions and add new ones to make backup and data sharing more convenient. 

Yes, blowing away all partitions will definitely fix the 'out of order' warnings. :(

Did we say 'always backup first'? :)

---

### Post by DavidTangye on 2008-08-21
> **mike_f said:**
>  					Originally Posted by **niyonk** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5638542#post5638542") 				
 				[I]I did notice you have cylinder boundary errors...I suggest you back-up your Linux files and wipe the partitions.
Then re-partition from Windows...that is how i got rid of the error the last time i got it.[/I]
As an alternative to repartitioning from Windows, get the free [System Rescue CD]("http://www.sysresccd.org/") and boot with it (after backing up all important data, of course). Type 'startx' to get the graphical desktop and click the gparted icon to run the graphical partitioner. It may offer to fix the partition table which may or may not destroy working partitions. You can also resize existing partitions which sometimes cleans up these errors.Weren't the cylinder boundary errors on the usbstick? So in this case none of this needs to be considered.

---

### Post by strfish7 on 2008-08-21
"So when you try and boot into Windows, is it still the same thing--you get a blinking cursor?"
Exactly so.  No XP. 

cat /windows/boot.ini yields

carl@Helios:~$ cat /windows/boot.ini
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptOut

And this

carl@Helios:~$ mount|grep sda
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sda7 on /home type ext2 (rw,relatime)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)

---

### Post by mike_f on 2008-08-21
@DavidTangye: OOPS, my bad. You're right, I'll edit the post to correct it. It still is useful to have the SysRescue CD around.

BTW I just noticed that a possibly critical line is missing from grub's menu.lst. It is possible that somehow the WinXP partition might have been marked hidden, so add the 'unhide' line in the WinXP entry. It can't hurt!

# on /dev/sda1
title Microsoft Windows XP Home Edition
**unhide (hd0,0)**
root (hd0,0)
savedefault
makeactive
chainloader +1

To edit this file, type 'sudo gedit /boot/grub/menu.lst' in a terminal window.

---

### Post by strfish7 on 2008-08-21
Thanks, Mikef, but adding that line to my grub menu didn't do the trick. Same behavior.

---

### Post by caljohnsmith on 2008-08-22
I think at this point you should consider doing a Windows "repair" with your Windows Install CD, strfish7. It basically rebuilds all the Windows system files, yet does not touch your personal data or programs you've installed, so it's not as drastic as completely reinstalling Windows where you lose everything and start from scratch. But it will set you back to Service Pack 1 (depending on your CD), so once you are able to boot into Windows again, you'll have lots of security updates to download.

If you decide to do a Windows repair, then before you do that and just to prove that Windows is indeed the problem and not Grub, I would go ahead and run the "fixmbr" program from your Windows Install CD; if you still aren't able to boot into Windows after that, then that rules out a problem with Grub, and I think a Windows repair is justified. 

If you do use fixmbr, you can always recover Grub afterwards by booting a Live CD and doing:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub> quit
```
That's all you should need to do.

---

### Post by strfish7 on 2008-08-22
Thanks for the help. I'll try the fxmbr and Windows repair.

---

### Post by strfish7 on 2008-08-23
Ok, I guess this is kind of an intractable problem.  I've done a fixmbr to no effect, restored grub menu, and performed a Windows repair. I still cannot boot into XP from the grub menu...the blinking cursor. Any new suggestions, please?

---

### Post by niyonk on 2008-08-23
Were you able to boot into XP after you repaired the MBR?
If so then there is something wrong somewhere in grub.

Please, also provide more details :)

---

### Post by caljohnsmith on 2008-08-23
Just to make sure you don't have some sort of HDD problem, I would run some HDD diagnostic tools on your HDD to check its health. Do you have a diagnostic tools CD that came with your HDD? If not you can download the [Ultimate Boot CD]("http://www.ultimatebootcd.com") and use that; it has lots of HDD test you can run.

If those tests show your HDD is fine, then you might have to resort to reinstalling Windows.

---

### Post by strfish7 on 2008-08-23
> **niyonk said:**
> Were you able to boot into XP after you repaired the MBR?
If so then there is something wrong somewhere in grub.

Please, also provide more details :)

No, I've never been able to boot into XP, not once. I see the XP in the grub menu, but highlighting it produces nothing but the blinking cursor.

@cljohnsmith,

I suppose doing the Hardy installation may have corrupted my HD somehow, so I'll try using the Ultimate Boot CD suggestion to scan it.  I think you may be right, it might be easier just to reinstall XP...I'm using Hardy for most of my work, and have very limited needs for XP anymore.  In fact, it's kind of annoying to go back to it sometimes (I'm referring to another computer which does have a functional dual boot...)
  
Thank you both for the suggestions. Will report back.

---

### Post by niyonk on 2008-08-23
What i meant was....were you able to boot into XP using it's own bootloader.
You know fixmbr removes Grub, right?

---

### Post by jiminoregon on 2008-08-23
I'm another newbie with a similar problem, but with a twist. I dual installed Ubuntu on my laptop with WinXP, and it worked great.  Then somehow I screwed it up and couldn't boot up into either OS. After some online searching I found a program called Super Grub Disk which repairs grubs.  I downloaded, burned to disk, and used this program to fix the mbr and can now boot into WinXP, but still have not been able to repair the grub to reboot into Linux.  I probably didn't read the directions carefully enough before using the problem. If you care to check it out, it's at 

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Hope this helps.

---

### Post by strfish7 on 2008-08-24
> **niyonk said:**
> What i meant was....were you able to boot into XP using it's own bootloader.
You know fixmbr removes Grub, right?

Yes, after the fixmbr I tried booting into XP, but no go. I then reinstalled grub and was able to boot back into Hardy.  I've about given up on ever seeing XP without a complete reinstall.

---

