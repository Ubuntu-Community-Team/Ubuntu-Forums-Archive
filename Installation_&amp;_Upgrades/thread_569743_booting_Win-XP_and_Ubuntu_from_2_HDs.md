---
title: "booting Win-XP and Ubuntu from 2 HDs"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by sudharma99 on 2007-10-07
I have installed UBUNTU 7.04 on my IDE drive 1 and Win-XP on my SATA drive 2. I can boot from the respective Hard Drives if I select them as 1st boot drive in the BIOS setup.  

I modified the grub as advised. I get the boot menu but the XP option won't load. ERROR 23 - something to do with parsing.

Any help to solve this problem is much appreciated.

sudo fdisk -lu gave the below given data:-

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   153677789    76838863+  83  Linux
/dev/hda2       153677790   156296384     1309297+   5  Extended
/dev/hda5       153677853   156296384     1309266   82  Linux swap / Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    25350569    12675253+   7  HPFS/NTFS
/dev/sda2        25350570    40965749     7807590    7  HPFS/NTFS
/dev/sda3        40965750   156280319    57657285    f  W95 Ext'd (LBA)
/dev/sda5        40965813    72212174    15623181    7  HPFS/NTFS
/dev/sda6   *    72212238   101032784    14410273+  83  Linux
/dev/sda7       101032848   102398309      682731   82  Linux swap / Solaris
/dev/sda8       102398373   156280319    26940973+   7  HPFS/NTFS





The grub data given below:-

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
timeout		3 

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
# kopt=root=UUID=274d8a04-43bf-497f-82ee-bb6379c42031 ro 

## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 

## default grub root device 
## e.g. groot=(hd0,0) 
# groot=(hd0,0) 

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

title		Ubuntu, kernel 2.6.20-16-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=274d8a04-43bf-497f-82ee-bb6379c42031 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-16-generic 
quiet 
savedefault 

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=274d8a04-43bf-497f-82ee-bb6379c42031 ro single 
initrd		/boot/initrd.img-2.6.20-16-generic 

title		Ubuntu, kernel 2.6.20-15-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=274d8a04-43bf-497f-82ee-bb6379c42031 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic 
quiet 
savedefault 

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=274d8a04-43bf-497f-82ee-bb6379c42031 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic 

title		Ubuntu, memtest86+ 
root		(hd0x 
,hd1) 
kernel		/boot/memtest86+.bin 
quiet 

title		Windows XP Professional 
root		(hd1,0) 
savedefault 
makeactive 
chainloader	+1 
map (hd0) (sd1) 
map (sd1) (hd0) 


### END DEBIAN AUTOMAGIC KERNELS LIST



I wish to select and boot any one of the OS from a common menu.
Thanks in advance

Sathish

---

### Post by ajgreeny on 2007-10-07
I'm not sure but I think this may be something to do with windows wanting to be on the first disk in a system.  It may be possible if you reset your disks with the ide as drive2 and windows as drive1, though you will then need to change the partitions in menu.lst.  The other thing I wonder about is the entry for windows in menu.lst

title		Windows XP Professional 
root		(hd1,0) 
savedefault 
makeactive 
chainloader	+1 
[B] map (hd0) (sd1) 
map (sd1) (hd0) [/B]

Do you need the bits at the bottom where you map to the drives?

If that is not the reason, then I can't help, I'm afraid, but I'm certain others will be able to help you.

---

### Post by Steve1961 on 2007-10-07
title Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0) 

I think the entry needs to look like the above - grub doesn't distinguish between hd0 and sd0 AFAIK

---

### Post by insomniux on 2007-10-07
I'm not sure if it makes any difference. In my menu.lst both the map commands came before the makeactive command. You may be able to find out which map-devices you need to change by running "find /boot.ini" in the grub shell. It'll tell you on which device XP is installed. I guess this will be sd0,0.

---

