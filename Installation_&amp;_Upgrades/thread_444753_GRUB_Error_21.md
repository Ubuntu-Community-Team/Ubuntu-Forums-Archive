---
title: "GRUB Error 21"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by alfredlau on 2007-05-15
So I decided to move over to Linux, from Windows Vista.

I decided to start dual-booting them. I followed the instructions, and now I get this GRUB ERROR 21 whenever I start my computer.

I'm using the Live CD now. I've googled for a solution for about 2 hours, and couldn't find a thing which helped. Can anyone here help me?

I have two harddisks. I installed Vista on one, and Linux on the other.

---

### Post by bulldog on 2007-05-15
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

Can you post the outcome of ```
 sudo fdisk -l
``` lower case L not a one.
Can you tell which hdd is your master boot device,the one with windows or with ubuntu?
On which hdd did you install GRUB,at the end of the install?

---

### Post by alfredlau on 2007-05-15
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30443   244526080    7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        4998    19663560    f  W95 Ext'd (LBA)
/dev/sdb5            2551        3850    10442218+   7  HPFS/NTFS
-----
I don't know about which hdd being the master boot device... I'm not very good with hardware. >_<
I just followed through the installation, so I supposed GRUB was installed to wherever Ubuntu was installed?

Oh... and I formatted the Ubuntu I previously installed, and installed it on the same hard disk as Vista (in a partition I made using Vista's disk management before I started installing). But sadly, GRUB gave the same error.

---

### Post by bulldog on 2007-05-15
As I understand correctly,ubuntu and Vista are on the same hdd.
As I look to the fdisk outcome,you haven't any ubuntu installed.
I see two bootable NTFS partitions,one on sda and one on sdb.

---

### Post by alfredlau on 2007-05-15
uhh. Sorry. I finished installing, and did the fdisk -l again. But it didn't register the new installation yet. :S

-----
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30443   244526080    7  HPFS/NTFS
/dev/sda2           30444       38913    68035275   83  Linux

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        4998    19663560    f  W95 Ext'd (LBA)
/dev/sdb5            2551        3850    10442218+   7  HPFS/NTFS

---

### Post by bulldog on 2007-05-15
Yeah you've got a linux on sda2,but no swap file?
To run ubuntu you need at least two partitions,a / for the system files and a swap which is similar as the windows page file.

You can make more partitions,like /home or /data but that's optional.
Your swap should be twice the amount of installed RAM,but if you have 1GB of Ramor more,you can make the swap partition 1GB as well.

---

### Post by alfredlau on 2007-05-15
What swap file? :S

---

### Post by pavelchjen on 2007-05-15
what Vendor and version of your PC's BIOS ?
[http://ubuntuforums.org/showthread.php?t=444935](http://ubuntuforums.org/showthread.php?t=444935)

---

### Post by bulldog on 2007-05-15
> **alfredlau said:**
> What swap file? :S

See my previous post.:)

---

### Post by alfredlau on 2007-05-15
Well, I reformatted the disk, and then installed Ubuntu again, this time with the swap disk.

Nope. Still has that stupid Error 21. If I were to use Vista's installation disc and repair the MBR, I can use Vista's bootloader, and do dual booting, right?

---

### Post by alfredlau on 2007-05-16
Can someone help me with this?

---

### Post by bulldog on 2007-05-16
```
fdisk -l
``` please............

---

### Post by alfredlau on 2007-05-16
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30443   244526080    7  HPFS/NTFS
/dev/sda2           30444       38709    66396645   83  Linux
/dev/sda3           38710       38913     1638630    5  Extended
/dev/sda5           38710       38913     1638598+  82  Linux swap / Solaris

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        4998    19663560    f  W95 Ext'd (LBA)
/dev/sdb5            2551        4998    19663528+   7  HPFS/NTFS

------
One thing I've noticed, in my boot/grub/device.map... its content is this:
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb

Is that supposed to be like that? :s

---

### Post by confused57 on 2007-05-16
> **alfredlau said:**
> Can someone help me with this?
You might also want to check your hard drive controllers in bios, make sure both hard drives are identified correctly and enabled(or set to "auto").

---

### Post by alfredlau on 2007-05-16
That I have. They -are- both identified, and set to auto.

---

### Post by bulldog on 2007-05-16
I suppose you installed GRUB on the sda hdd (hd0) and this is you master boot disk as well.
Can you boot the live cd so we can mount your ubuntu to have a look at the menu.lst?
If you get to the desktop open a terminal and copy and paste the next commands.

```
sudo mkdir /mnt/rescue
sudo mount /dev/sda2 /mnt/rescue
sudo cp /mnt/rescue/boot/grub/menu.lst /mnt/rescue/boot/grub/menu.lst_backup
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```

Can you post the output of the last command to the forum?

---

### Post by alfredlau on 2007-05-16
[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=295ac1f0-e18b-44c2-9ea1-0ea200683130 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=295ac1f0-e18b-44c2-9ea1-0ea200683130 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=295ac1f0-e18b-44c2-9ea1-0ea200683130 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/PHP]

I'm guessing this line: 
[php]root		(hd0,1)[/php]
should be changed to:
[php]root		(hd0,2)[/php]
?

---

### Post by bulldog on 2007-05-16
No there's nothing wrong with the menu.lst,it should be hd0,1 because grub starts counting with zero for the first partition.
If you're absolutely sure you boot from the sda hdd,I have no idea why it not would boot.
Both hdd are recognized by ubuntu [fdisk] your menu.lst points to the right partition and you'll get error 21.
It looks like a BIOS error,because the live cd has no problems with your hdd's.

Did you noticed this posting from pavelchjen?
```
what Vendor and version of your PC's BIOS ?
http://ubuntuforums.org/showthread.php?t=444935
```

---

### Post by alfredlau on 2007-05-16
I'm not sure what BIOS I use, but I'm pretty sure it isn't Phoenix. Bleh. :(

---

### Post by bulldog on 2007-05-16
It's not an external hdd by any chance?
Because grub can't find your hdd,but when you boot the live cd it can.
Does the motherboard has native Sata ports,or do you use any PCI card to emulate Sata?
Pretty strange :(

---

### Post by alfredlau on 2007-05-16
I Just re-booted.

And the damn BIOS was actually Phoenix. ARGH. Is there anything else I can do, other than get OpenBIOS? But I got this computer like.. 5 months ago. And it isn't a lappy. =S

---

### Post by bulldog on 2007-05-16
I don't say it's your BIOS but it could be.
Everything what is necessary to boot is correct,you can get an error but we can try to solve it.
But if it's not finding the hdd,well..............what can I say,I can't force grub to look any better:) 

I should repair the Vista boot and make free space on the second hdd for ubuntu.
Then install ubuntu on the second hdd **and install grub there as well**
Make the second hdd your master boot device to see if it will be found.

Yes,I know,a lot of work,but if this is not working either,you can be pretty sure your BIOS is involved.

---

