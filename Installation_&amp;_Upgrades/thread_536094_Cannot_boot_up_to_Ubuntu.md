---
title: "Cannot boot up to Ubuntu"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by mgybran on 2007-08-27
Hi 

I have recently reinstalled Feisty Faun (several times in fact) and am now not able to boot up.  I get the GRUB menu but when I select to boot up I get the following error:

Starting up...
invalid compressed format (error=1)
-- System halted

I can't find a lot on the Net about this error but I think it could have something to do with either GRUB or the MBR master boot record.  I have reinstalled GRUB to the root.  No errors, but the above error remains.

I would like to draw a line in the sand and start from scratch by reinstalling Windows and Linux, but this seems easier said than done.  After several formatting of the Windows/Linux partitions and installs I can't get past this error above.  Windows always reinstalls perfectly, and I can  access this fine.

How can I start off fresh with the MBR?  It always seems to remember my previous Linux installation

Thanks

---

### Post by louieb on 2007-08-28
If you get to the GRUB menu then you are done with the MBR. The code in the MBR is just a pointer to some program on the hard drive. stage2 in the case of GRUB or ntldr if it boots to windows. The problem could be with the Linux partition.  Are you trying to use LVM?  What file system are you trying to use?  

If you don't know the answers to these questions then please describe the selections you are making during the install process. I'll try and give you some help. Some good dual boot stuff  is in the **Dual Boot** and **psychocats** links in signature.

---

### Post by mgybran on 2007-08-29
> **louieb said:**
>  Are you trying to use LVM?  What file system are you trying to use?  



I just did a quick search for LVM in Wikipedia.  The answer is no, I have not used the logical volume manager.  I tried three different ways, partitioned with the live CD Gparted, WindowsXP install and Partition Magic.  (cannot remember the sequence).
I have tried ntfs (windows) and ext3 and also set all partitios to ntfs with Gparted and then started the install.
I played around with GParted a long time and I have probably tried at least ten installs.

As per your suggestion, I have referred to PsychoCats website and have reviewed the guide on partitioning. I am now in the process of reinstalling Windows.  I have completely removed all partitions in the installation and created four partitions. Intend to setup the following
C ntfs for Windows
D ext3 for /home 
E ext3 for /
F Swap

UPDATE
During the Windows XP install I completely removed all partitions. One was left. From this I created the above partitions and installed Windows XP on the C partition.
After the install I formatted drives D,E and F to ntfs from Windows.  I then started the Live CD. Opened GPartEd and changed  my /home to ext3 and / to ext3.  I then started the installation. Selected the home, / and swap.  Formatted the / and the installation finished successfully.  I rebooted, got the grub menu and .... the errorthat I reported is back.  

What to do?  Point to note.. I previously installed Ubuntu easily in May and it had run without any problems for four months.  I can boot to Windows without any problems.

---

### Post by louieb on 2007-08-29
your using the live CD I take it. Boot to the CD open **applications>accessories>terminal**    I want you to list your partition table to do that key in```
 **sudo fdisk -l** 
``` 
Post the output here. 

Another output I want is content of **/boot/grub/menu.lst** You can use the Text editor in the accessories menu to cut and paste. 

Don't see any reason why it does  not work. May need the content of  **/etc/fstab**   and IF your trying to install edgy or  feisty the output of```
** ls -l /dev/disk/by-uuid/   **
``` 

I know thats a lot of stuff but the answer to why it won't boot Ubuntu is in there somewhere.

---

### Post by mgybran on 2007-08-29
Update 2
as per your third link on reinstalling GRUB I followed the instructions.
The first commands succeeded but did not resolve the problem.
The second commands also succeeded but
Output was:
stage1 exists =yes
stage2 exists=yes
stage1_5 exists=yes
17 sectors embedded succeeded
Running install /boot/grub/stage1 and stage2 succeeded

My hard drive is also a SATA sda6

Result.... same error and the system is halted.

---

### Post by mgybran on 2007-08-29
Information requested below

**Output from fdisk -l**
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       24791   158175990    f  W95 Ext'd (LBA)
/dev/sda5            5100       20397   122881153+  83  Linux
/dev/sda6           20398       24527    33174193+  83  Linux
/dev/sda7           24528       24791     2120548+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

***********************************************
**Content of /boot/grub/menu.lst**
# menu.lst - See: grub( 8 ), info grub, update-grub( 8 )
#            grub-install( 8 ), grub-floppy( 8 ),
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=704aa21a-3148-4a06-b584-5d742ec9c670 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic
root=UUID=704aa21a-3148-4a06-b584-5d742ec9c670 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.20-15-generic
root=UUID=704aa21a-3148-4a06-b584-5d742ec9c670 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,5)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

******************************************
**Content of /etc/fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=704aa21a-3148-4a06-b584-5d742ec9c670 /               ext3
defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=827cc1ce-7cc8-4a10-b932-b36bd99944f3 /home           ext3
defaults        0       2
# /dev/sda1
UUID=6010230E1022EAAC /media/sda1     ntfs
defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=b63be320-704b-4b0b-8b2d-341146952d78 none            swap    sw
          0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0

*********************************************
**Output of ls -l /dev/disk/by-uuid/**
ubuntu@ubuntu:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2007-08-30 01:53 6010230E1022EAAC -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-08-30 01:53
704aa21a-3148-4a06-b584-5d742ec9c670 -> ../../sda6
lrwxrwxrwx 1 root root 10 2007-08-30 01:53
827cc1ce-7cc8-4a10-b932-b36bd99944f3 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-08-30 01:53
b63be320-704b-4b0b-8b2d-341146952d78 -> ../../sda7
ubuntu@ubuntu:~$

---

### Post by louieb on 2007-08-29
Well I was wrong. I can't find anything that would stop it from booting. The invalid compression message make me think its the **          /boot/initrd.img-2.6.20-15-generic** that file is compressed. But I would not know how to fix it. One thing you might try is boot to memtest just to see if that comes up OK. 

Since you have had Ubuntu up and running on that PC before My wild as guess is the Install CD has a few twisted bits in the wrong place. I would be inclined to burn it again. Or even try the alternate install CD. 
Can't ever figure out the size of a partition from the fdisk output. How big is sda6 your  / partition?
```
704aa21a-3148-4a06-b584-5d742ec9c670 fstab /
704aa21a-3148-4a06-b584-5d742ec9c670 uuid 
704aa21a-3148-4a06-b584-5d742ec9c670 menu 


Device Boot Start End Blocks Id System
/dev/sda1 *     1  5099   40957686 7 HPFS/NTFS
/dev/sda2  5100 24791 158175990 f W95 Ext'd (LBA)
/dev/sda5  5100 20397 122881153+ 83 Linux
/dev/sda6 20398 24527  33174193+ 83 Linux
/dev/sda7 24528 24791   2120548+ 82 Linux swap / Solaris  
```

---

### Post by logos34 on 2007-08-29
Louieb is right--it's not a Grub issue because you're past that stage. It's trying to load the initial ramdisk image but can't...something's corrupted in one or both of the these files:

[B]initrd.img-2.6.20-15-generic
vmlinuz-2.6.20-15-generic[/B]

That's my guess.

Are you suing a factory-pressed Ubuntu install CD or did you download?  If the latter, could be a bad burn/faulty media/corrupted iso download. You should have followed the proceedure detailed in the [burningsiohowto.]("https://wiki.ubuntu.com/BurningIsoHowto")

---

### Post by logos34 on 2007-08-29
sorry louieb--as usual I was typing just as you posted.  i get lazy with the refresh button

---

### Post by logos34 on 2007-08-29
> **louieb said:**
> 
Can't ever figure out the size of a partition from the fdisk output. How big is sda6 your  / partition?


around ~30 GB ?? (4129 cylinders)

---

### Post by mgybran on 2007-08-30
> **logos34 said:**
> around ~30 GB ?? (4129 cylinders)

Yep.  That is pretty much the size.

---

### Post by mgybran on 2007-08-30
I did an integrity check on the CD. Turns out there are 3 corrupt files on it.  It does say which files these are though.  Thanks for pointing me to the CD guys.
I will need to buy some more CDs for a new burn.I checked the md5 checksum this time.  At least I know this time that at least the md5 checksum is correct.
I will let you know how I get on.

---

### Post by mgybran on 2007-08-31
I reburned a new CD. Checked for integrity. No errors this time.  Fixed my mbr, deleted and formatted the Linux partition.   Reinstalled. Worked fine this time.  Thanks for your help guys.

---

