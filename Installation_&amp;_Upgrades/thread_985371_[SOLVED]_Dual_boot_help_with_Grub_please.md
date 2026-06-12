---
title: "[SOLVED] Dual boot help with Grub please"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by mrdak on 2008-11-17
Hi,

Xp is on one drive, and Ubuntu on another.
While trying to get the impossible x-fi driver that just came out installed, I restarted, and ubuntu wouldn't reboot. I reinstalled 8.10, and didn't install grub to the right partition. Then neither OS would boot.
So, I used SGD and could not repair grub, but it did repair XP. 
Then I used the live CD and did a repair on Grub. 
Now, I can boot into both OS's, but only if I switch the boot order in bios. When I try from the Ubuntu hd, grub loads and will not boot the xp on the list.Only Ubuntu. 

Here is my fdisk -l

danh@Dans-PhenomBox:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0747b04c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9030    72533443+   7  HPFS/NTFS
/dev/sda2            9031        9039       72292+   7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x555f555f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4844    38909398+   7  HPFS/NTFS
/dev/sdb2            4845       24320   156440970    f  W95 Ext'd (LBA)
/dev/sdb5            4845        9688    38909398+   7  HPFS/NTFS
/dev/sdb6            9689       14532    38909398+   7  HPFS/NTFS
/dev/sdb7           14533       19376    38909398+   7  HPFS/NTFS
/dev/sdb8           19377       24320    39712648+   7  HPFS/NTFS

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
16 heads, 63 sectors/track, 144073 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x05c00fa0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       71740    36156928+   7  HPFS/NTFS
/dev/sdc2           71741      144073    36455832    f  W95 Ext'd (LBA)
/dev/sdc5           71741      144073    36455800+   7  HPFS/NTFS

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f548106

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        2231    17920476   83  Linux
/dev/sdd2            2554        9729    57641220    f  W95 Ext'd (LBA)
/dev/sdd3   *        2232        2553     2586465   82  Linux swap / Solaris
/dev/sdd5            2554        9729    57641188+   7  HPFS/NTFS

Partition table entries are not in disk order
danh@Dans-PhenomBox:~$ 

------------------------------------

And here is my menu.lst 

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
# kopt=root=UUID=87d876e6-62dc-4224-9925-e5207ae5de55 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=87d876e6-62dc-4224-9925-e5207ae5de55

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		87d876e6-62dc-4224-9925-e5207ae5de55
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=87d876e6-62dc-4224-9925-e5207ae5de55 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		87d876e6-62dc-4224-9925-e5207ae5de55
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=87d876e6-62dc-4224-9925-e5207ae5de55 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		87d876e6-62dc-4224-9925-e5207ae5de55
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
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb5
title		Microsoft Windows XP Home Edition
root		(hd1,4)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


How can I edit menu.lst to put XP in the right place, or order.
I would like to keep the Ubuntu hd as the first hd, and make XP boot from grub also. It's on the second hd. 
I am confused about the disk order........ I understand how it works, but I just can't get it to work  :(
Thanks in advance........... really!

---

### Post by caljohnsmith on 2008-11-17
OK, how about opening your menu.lst first:
```
gksudo gedit /boot/grub/menu.lst
```
And then replace your Windows entries with:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   Windows XP (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
If your Windows partition is the first partition on the drive, one of those entries above should work. If not, please let me know exactly what happens when you try each of them from the Grub menu, and we can work from there. Otherwise let me know how it goes. :)

---

### Post by zwygart on 2008-11-17
To edit menu.lst type 
```
sudo gedit /boot/grub/menu.lst
```

Where is your GRUB intstalled? I mean stage 1. Is it on the MBR of sda or at sdd1 or other?.

GRUB give the letter 0 to the drive where he is on. So you may try map on the first XP by copying the 
map (hd0) (hd1)
map (hd1) (hd0)
to the first XP. It will look like this :
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

The second XP, I suggest to change the 1 for 2

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb5
title Microsoft Windows XP Home Edition
root (hd1,4)
savedefault
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

I usually have trouble by booting XP from GRUB. But I never tried by using map. Please post back.

On my home computer I arranged it that the BIOS boot the second HD first. When I choose XP, boot from GRUB will fail with a error. I just have to press enter and the BIOS boot on the first HD (XP). This way I have to press enter two times, but it works. I should try change it.
I hope this help and post back.

P.S.:Don't be afraid off trying letters on your XP boot section. It not breakes your system. Only XP would not boot, but it does not anyway.

---

### Post by mrdak on 2008-11-17
My bios lists 

hda5 - sda5  hd0,4  as where XP is installed... ok...
and
hda1 - sda1  hd0,0  as where ext2-3\ Linux is.

Right now in my boot order, I have the hda1 1st, and the hda5 second

Does that help? Just thought I'd mention it.




zwygart  I tried both of your suggestions in menu.lst and no joy.


caljohnsmith,  I'll try your suggestions, and will post back in about an hour..........  thanks

Thanks to both of you. I'll be back in a bit  ;)

mrdak


edit ......  Look closely at my fdisk -l.....  I don't have xp installed on that 200gb drive where the * is.
I have XP on the 74GB hd and Linux is on the 80GB hd.
BrB

---

### Post by mrdak on 2008-11-17
> **caljohnsmith said:**
> OK, how about opening your menu.lst first:
```
gksudo gedit /boot/grub/menu.lst
```
And then replace your Windows entries with:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   Windows XP (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1
```
If your Windows partition is the first partition on the drive, one of those entries above should work. If not, please let me know exactly what happens when you try each of them from the Grub menu, and we can work from there. Otherwise let me know how it goes. :)

Well sir, :)
Your first suggested entry using hd1 fixed my problem. I tried it just a little while ago, and it didn't work, but had a feeling I typed it in backwards or something, so I tried it again, bamm.......... happy happy joy joy
When I tried hd2 and hd3, I got missing ntldr, and I just knew the xp boot.ini had not been touched. So I went back and retyped hd1, and it's all good.
Thank you so very much, and I hope you have a great Thanksgiving ;)
You too zwygart!!     



mrdak

---

### Post by caljohnsmith on 2008-11-17
> **mrdak said:**
> Well sir, :)
Your first suggested entry using hd1 fixed my problem. I tried it just a little while ago, and it didn't work, but had a feeling I typed it in backwards or something, so I tried it again, bamm.......... happy happy joy joy
When I tried hd2 and hd3, I got missing ntldr, and I just knew the xp boot.ini had not been touched. So I went back and retyped hd1, and it's all good.
Thank you so very much, and I hope you have a great Thanksgiving ;)
You too zwygart!!     

mrdak
That's great news, I'm glad it worked; have a happy Thanksgiving too. :)

---

### Post by zwygart on 2008-11-18
Perfect

I'm happy. Some times it's difficult to found out wich letter means what. But it's perfect that you found out yours. This helps everybody (me too). I retain that map works. I missed that your grub is not installed on the first HD (sda). This causes that all letters are shifted in GRUB. (This is what I learned thanks you too).

---

