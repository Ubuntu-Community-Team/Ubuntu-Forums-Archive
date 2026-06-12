---
title: "Dual Boot - No GRUB"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by jor_el on 2007-08-19
I recently installed Ubuntu on my machine wanting to dual boot with XP. XP is on the primary drive, and I chose to install Ubuntu on the secondary drive. I realy new at this, but from what I read the installer would detect XP and configure grub automaticaly. That didnt happen, on reboot I just jump right back into XP. I dont know if I missed something durring the install, or if I will have to install and configure GRUB manualy.

Some of what I have read talks about modifying the boot.ini file. Is there anything I can do to get this configured correctly from the XP side, or will I have to reinstall Ubuntu? Is there a guide for setting GRUB up from scratch, or an easier way to make this work?

Thanks for your help.

---

### Post by confused57 on 2007-08-19
You could try booting first to your drive with Ubuntu...it's possible grub's IPL installed to the secondary drive's mbr.

---

### Post by jor_el on 2007-08-19
Thanks for the advise, but the machine is kind of a pain to get into. That and there is another partition behind the Ubuntu one wich would become drive C if I booted to that first (at least thats how I think it works). If I boot to the install cd is there a way to look into that and maybe setup the prinmary drive to dual boot?

---

### Post by confused57 on 2007-08-19
> **jor_el said:**
> Thanks for the advise, but the machine is kind of a pain to get into. That and there is another partition behind the Ubuntu one wich would become drive C if I booted to that first (at least thats how I think it works). If I boot to the install cd is there a way to look into that and maybe setup the prinmary drive to dual boot?
Yes, you can mount your root partition, by booting the Ubuntu live cd...then you can access your /boot/grub/menu.lst, which you might want to post the results:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

You probably just need to post the boot entries, which will show how Ubuntu recognizes the order of your hard drives...also, open a terminal(Applications---Accessories---Terminal) and post the output of:
```
sudo fdisk -l
```
-l is a small "L"

---

### Post by jor_el on 2007-08-19
Ok, did that and here is what I am looking at. The menu.lst file on the Ubuntu disk is like so:
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
# kopt=root=UUID=983a0803-2278-4c56-b462-625141d618ed ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=983a0803-2278-4c56-b462-625141d618ed ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=983a0803-2278-4c56-b462-625141d618ed ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title		Microsoft Windows XP Professional
root		(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1

```

And the fdisk shows my layout as so:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4863    39062016   83  Linux
/dev/sdb2            4864       19457   117226305    b  W95 FAT32

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       14946   120053713+   7  HPFS/NTFS

Disk /dev/sdd: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         892     7164958+   7  HPFS/NTFS
/dev/sdd2             893        1743     6835657+  82  Linux swap / Solaris

```

---

### Post by confused57 on 2007-08-19
It looks like grub recognizes your /dev/sdb as (hd0) and your /dev/sda drive with Windows as (hd3)...you say there isn't any way to set your bios to boot first to /dev/sdb, which would be the best solution.

Before you do anything else, download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
See if you can boot your Ubuntu with SGD, which is also capable of booting Windows...or restoring the IPL of Windows or Ubuntu to the mbr.

See the "Grub Section" on this website for a guide to how grub works:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by jor_el on 2007-08-20
If I try to boot to the drive I get this:
```
No bootable device -- insert boot disk and press any key
```

I really dont want to start messing with the MBR of the main drive because I know whats going to happen - I'll lose access to windows. I'm just a little too new at this to feel comfortable doing that. I'll look around a bit more but for now I guess I'm done :(

To confirm what you were seeing, when I run the installer it lists the Ubuntu drive as sda and the xp drive as sdb (which is weird because XP is a sata drive, the rest are ide). fdisk's layout makes more sense, and I think the issue may be because the installer configures grub as if the ubuntu drive were sda, but when it tries to boot it sees it as sdb. At least thats my random guess.

Ah well, hopefuly I can stumble on something to figure it out. Thanks for all your help.

---

### Post by maybeway36 on 2007-08-20
I think if you break the MBR, you can always run "fdisk /mbr" on a DOS floppy and it will give you back windows.

---

### Post by Om1977 on 2007-08-20
Or if you have trouble with a DOS floppy .. you can always use the windows 98 installation disk .. to run the command i.e. "fdisk /mbr" you will know that the mbr has been repaired if it returns a blank message

---

### Post by jor_el on 2007-08-20
Ok, this is really strange (in a good way I guess). I went back and wiped the swap, ext3, and shared fat32 partitions and started the install all over again. Before I started it I ran fdisk and noticed it was seeing the drives correctly, so I ran the install and tada - got GRUB all setup up on the main drive. So I am up and runnin here, thanks everyone for your help.

Now about this 8600GTS .....
8-)

---

### Post by confused57 on 2007-08-20
> **jor_el said:**
> Ok, this is really strange (in a good way I guess). I went back and wiped the swap, ext3, and shared fat32 partitions and started the install all over again. Before I started it I ran fdisk and noticed it was seeing the drives correctly, so I ran the install and tada - got GRUB all setup up on the main drive. So I am up and runnin here, thanks everyone for your help.

Now about this 8600GTS .....
8-)

Glad you were able to get your dual boot working.  You might have to use the latest Nvidia driver from the Nvidia website for your video card...try doing a forum search for your card, specifying search titles, I'm sure many people have been able to get this card working OK.

---

