---
title: "[SOLVED] Grub Error in dual-boot XP/Ubuntu system"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by Aesir on 2008-08-28
I've been installing different OS on an available drive over the past couple of days and on the last install (this time, Ubuntu 8.04.1) I think I have a syntax and/or mapping error in my menu.lst and I can't boot to XP anymore.  From within linux I can see the data on the XP drive so I'm hoping that it's not toasted and that I just have to edit something in menu.lst to sort things out like they were.

BIOS has four drives in order of priority as:
80gb primary master (Ubuntu 8.04.1 i386)
80gb slave (unused)
250 primary on SATA 3 (XP Pro operating system, program and data partitions)
250 primary on SATA 5 (unused)

BIOS has boot priority set to CD drive, then the 80gb master, then floppy.

On power on, GRUB menu selection for XP results in a reboot of the system back into the grub menu.  Editing the relevant line to experimentally change the HD2,0 value to any other values (hd0,0 to hd2,1 were tested) results in no such partition error except for hd2,0 which gives the aforementioned reboot then back to the menu cycle.

Here are the files I think are relevant to the issue, starting with fdisk -l output:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97899789

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1533    12313791    7  HPFS/NTFS
/dev/sda2            1534       30400   231874177+   f  W95 Ext'd (LBA)
/dev/sda5            1534       14281   102398278+   7  HPFS/NTFS
/dev/sda6           14282       20655    51199123+   7  HPFS/NTFS
/dev/sda7           20656       21166     4104576    7  HPFS/NTFS
/dev/sda8           21167       21548     3068383+   7  HPFS/NTFS
/dev/sda9           21549       29579    64508976    7  HPFS/NTFS
/dev/sda10          29580       30400     6594651    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9745e817

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x65c4263a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4fbc4fbb
```

menu.lst, which I've tried editing by hand with little success, though with each edit something did change (indicating I was editing the correct file).
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
# kopt=root=UUID=f16d4727-d66f-4a01-968d-7106a8fe257d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f16d4727-d66f-4a01-968d-7106a8fe257d ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f16d4727-d66f-4a01-968d-7106a8fe257d ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
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
root		(hd2,0)
savedefault
makeactive
chainloader	+1
```

Finally, XP's boot.ini. I have not edited this since installing an AMD CPU a few years ago:
```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=OPTIN /fastdetect /usepmtimer
```

As best I can tell, I've not managed to blow up the XP MBR or partition, but I really can't confirm without booting into the OS.  So I tried to disable all drives in BIOS except for the XP drive.  Grub puked a little bit on that with grub error 22 (iirc).  It never tried to boot XP that time, it just gave out the error and I had to reboot, and undo the changes in the BIOS to get a proper boot menu for linux again.

TIA for any help/guidance.

P.S. The end-goal is that I have a fully operational XP drive for my day to day stuff, along with 1 to 3 different other operating systems to experiment with.  (short list so far is OpenSolaris if I can sort out a sound driver issue, one flavor of Ubuntu, and one nasty test drive for things that are beyond my skill in setting up ... like Gentoo).  But for now, I'd like to get back to one Ubuntu and one XP drive like I've had for the past few months.

P.P.S. I should add that the non-hand edited menu.list originally had ubuntu, ubuntu recovery, and memtest pointed at hd2,0 - and XP on hd0,0.  The problem there was that not one of the operating systems or memtest would load.  When I changed those three ubuntu related entries to hd0,0, they worked, but XP still won't try to boot.

---

### Post by falcon61102 on 2008-08-28
Are you able to boot into Ubuntu?

Also, based on the results of your fdisk -l readout, Ubuntu is reading your XP drive as the primary drive.  This may be causing you some issues with the menu.lst.

Try adding the map command to your GRUB for starting up XP.  When you start your computer and get to the GRUB, select the XP line and hit "e" to edit.  Enter in the following lines and then press "b" for boot.  This allows you to temporarily test boot settings but will not save them.  Use the following commands:
```
map (hd0) (hd2)
map (hd2) (hd0)
```

---

### Post by caljohnsmith on 2008-08-28
+1 for what falcon61102 said; any time you try and boot Windows on a HDD different from the HDD that's booted on start up, you have to use the "mapping" technique that falcon61102 talks about. It's reasonable to assume your Windows is on the first partition because of your fdisk output, so the only thing you need to determine is which HDD Grub thinks Windows is on. Try adding the following two entries to your menu.lst, reboot, and see if either works:
```
title   Windows (hd1)
root    (hd1,0)
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title   Windows (hd2)
root    (hd2,0)
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
If neither of those work, then I think what you said here is significant:
> **Aesir said:**
> 
On power on, GRUB menu selection for XP results in a reboot of the system back into the grub menu.
This can happen if Grub accidentally gets written to the boot sector of the Windows partition. That's probably not likely in your case, but if you have your Windows Install CD, you can make sure your Windows boot sector is OK by running "fixboot" in the recovery console after booting up the Win Install CD. 

Let me know how it goes. :)

---

### Post by Aesir on 2008-08-28
In searching out this issue, I found it's fairly common, and I did run into many topics mentioning Grub's MAP statement.  I am ignorant about whether or not Grub has the potential to destroy boot records or partition tables or any other irrevocable things, so I played it safe and kicked off this topic.

Problem solved.

The first set of kudos goes to falcon61102 - for providing the tip on mappings.  The second thanks goes to caljohnsmith for making it infinitely easier to test the solutions out through a quick copy/paste of a pair of testable menu.lst entries.  Between those two tips, I was in XP (where I write this post) within a matter of seconds.  The correct map for me was:

```
map        (hd0) (hd2)
map        (hd2) (hd0)
```

Thanks folks.  I'm now going to leave 8.04 and XP alone... but I'm about to install freespire on one of the remaining two drives... and will revisit OpenSolaris for the last unused drive if I can find a solution to the mystery of the missing AC'97 audio driver+codec under that OS.  Wish me luck!

---

### Post by falcon61102 on 2008-08-28
Glad it worked out for you.

---

