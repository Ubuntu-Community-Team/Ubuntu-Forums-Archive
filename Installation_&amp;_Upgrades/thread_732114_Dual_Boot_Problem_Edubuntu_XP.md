---
title: "Dual Boot Problem Edubuntu XP"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by hmaia on 2008-03-22
Hi,

I just install Edubuntu in a machine with a XP already installed.
After Install i just cant boot to XP Anymore.

I already try with super grub and same errors occurs, error related to hal.dll.

Here is my info:

sudo fdisk -l
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15281527

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        6374    51191122+   f  W95 Ext'd (LBA)
/dev/sda2   *        6375       12043    45536242+   7  HPFS/NTFS
/dev/sda3           12044       13016     7815622+  83  Linux
/dev/sda4           13017       13052      289170   82  Linux swap / Solaris
/dev/sda5   *           2        6374    51191091    7  HPFS/NTFS

=====================================
My menu.lst

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
# kopt=root=UUID=00b08880-6dfb-41d4-8f72-e29c9d27dd94 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=00b08880-6dfb-41d4-8f72-e29c9d27dd94 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=00b08880-6dfb-41d4-8f72-e29c9d27dd94 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

======================================================
My boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


======================================================

Anyone Can Help me with this?

Thanks
Hugo

---

### Post by Kiri on 2008-03-22
Looks like sda2 and sda5 are both set to active boot partition?
I think you should have just sda2 as active.

---

### Post by dstew on 2008-03-22
> default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWSI think this should be```
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
```Same in the operating systems line. I think boot.ini counts partitions starting at 1, not zero, so /dev/sda2 might be partition number 2.

---

### Post by hmaia on 2008-03-22
Hi,

Thanks Kiri and dstew, but still dont work.

My conf files are like you can see :

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        6374    51191122+   f  W95 Ext'd (LBA)
/dev/sda2   *        6375       12043    45536242+   7  HPFS/NTFS
/dev/sda3           12044       13016     7815622+  83  Linux
/dev/sda4           13017       13052      289170   82  Linux swap / Solaris
/dev/sda5               2        6374    51191091    7  HPFS/NTFS


my menu.lst (Just the end of the file, the rest is like initial post)
## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=00b08880-6dfb-41d4-8f72-e29c9d27dd94 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=00b08880-6dfb-41d4-8f72-e29c9d27dd94 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1

=================================================
my boot.ini

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

=================================================

any help and opinions are very welcome, not only want to see this fixed, byt also understand why it happens, so i can advice others to try Edubuntu without loose is original OS.

---

### Post by Pumalite on 2008-03-22
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Post a screenshot. Use the camera icon at the bottom.

---

### Post by hmaia on 2008-03-22
Hi,

Pumalite, here it is the info you asking for.
Hope that can help you to help me.

Thanks.

---

### Post by dstew on 2008-03-22
Do you get the error after choosing the Windows item from the grub menu? Please post the exact error. It seems that the error is coming from within Windows, if it says something about hal.dll

---

### Post by hmaia on 2008-03-22
> **dstew said:**
> Do you get the error after choosing the Windows item from the grub menu? Please post the exact error. It seems that the error is coming from within Windows, if it says something about hal.dll

yes, it says something like hal.ddl missing or corrupted.

---

### Post by dstew on 2008-03-22
Files with the extension .dll are Windows files. Maybe check on a Windows forum for help with that, or google that particular error.

---

### Post by Pumalite on 2008-03-22
I think the Installation CD comes with the possibility to repair the systemfile; at least in XP.

---

### Post by hmaia on 2008-03-23
Hi,

Already solve the problem.

First of all i best thanks to Kiri, dstew and to Pumalite.
As you understand in my next lines, you dont give me the solution but you were part of the solution, because you help me order my brain in order to find the final solution.

Kiri you notice that i had two active partitions, that happens after i made some experiences and then , i didnt realise that while doing that experiments i put 2 partitions active.
How this happens:
If you use Grub to flag a parttition with Boot and then edit menu.lst and change the windows entry to another diferent then you will make both active.
So first of all we need to make sure that only 1 partition is active.

dstew, your comment was very important, because later help me to keep in mind that not always the reference number in ubuntu and in windows are the same.

Pumalite, your help, help me to collect more information to struct my aproach to the problem, i use gparted live cd to make sure that when pc boot everything was like i expect, and also use super grub were i get the info that in my pc sda2 is (hdo, 1) and not hd0,2 like i was thinking at the very beggining of the problem.

To those who can have this kind of problem here it his my experience and what i did to solved.


After the help that i related, and after i try to fix with windows recover console, with no results, in fact i even can't do a bootcfg /rebuild, because it give some error, i start to think that first of all i need to be sure that at ubuntu side everything was fine, so i make a list and start to edit grub menu.lst and change the partition values for windows entry, hd0,0 hd0,1, etc. everytime i reeboot , i kept the error. so i found what was the only possible entry , was the one were i get the hal.dll error, the other errors were related to ubuntu, so if i get the hal.dll error means that from ubuntu side the configuratuion is fine, and now i have to found the windows side problem.

then i make sure that i have the rigth boot flag in partition were boot.ini exists, doesnt have to be the same of were windows folders are, grub just have to know were boot.ini is, and the boot.ini says wich partition can windows folder be found.

OBS : I am a SCM and developer software, so i use my experience to understand that the hal.ddl error its not a particular error , but a generic one, what windows does is try to found the windows/system32/hal.dll, if a windows folder does not exists , like if you have wrong partition in boot.ini file windows allways says that hal.dll is missing or corrupted, the missing is true, because windows folder is not there, but this error can put us in worng direction, what windows should say is that a windows folder can not be found in partition .
In other words windows dont validate if all folders in path to hal.dll exists

So, after be sure that ubuntu side was fine, i start to edit the boot.ini file, and change the partition number (partition(0),partition(1),partition(3)), everytime i make a change i reboot the system, allways getting hal.dll, until i get to the spot, in my case was partition(4), my sda5 in ubuntu side.

Now i have dual boot, i still have XP without having to re-install the system, i can use edubuntu for me, and the mainly reason, i can put my boy using ubuntu at home, and i can sugest the ubuntu instalation at my sun school, were i have responsabilitys at the  parents associations board.

Best Regards
Hugo
:guitar:

---

### Post by Pumalite on 2008-03-23
Congrats! Great work.

---

### Post by Kiri on 2008-03-23
Good! And thanks for posting your information to help others too :)

---

### Post by dstew on 2008-03-23
Good job. You succeeded by being persistent and thoughtful.

---

