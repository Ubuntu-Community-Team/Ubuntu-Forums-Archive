---
title: "Dual boot Suse / Ubuntu on two Hd"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by Ronfleur on 2008-03-16
Hi, 

I've got Suse 9.3 installed on HDA and would like to install Ubuntu on HDB. 

Grub is installed on HDA.

Here's an extract from dmesg of the 2 HDD:

HDA (6.44 gigs)

Kernel command line: root=/dev/hda1 vga=0x317 selinux=0  splash=silent resume=/dev/hda2
ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
hda: SAMSUNG SV0644A, ATA DISK drive
hda: max request size: 128KiB
hda: 12504240 sectors (6402 MB) w/490KiB Cache, CHS=13232/15/63, UDMA(33)
hda: cache flushes not supported
 hda: hda1 hda2
EXT3 FS on hda1, internal journal
JBD: barrier-based sync failed on hda1 - disabling barriers
Adding 586364k swap on /dev/hda2.  Priority:42 extents:1
JBD: barrier-based sync failed on hda1 - disabling barriers

HDB (80 gigs)

ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
hdb: WDC WD800JB-00JJC0, ATA DISK drive
hdb: max request size: 128KiB
hdb: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(33)
hdb: cache flushes supported
 hdb: hdb1 < hdb5 hdb6 hdb7 hdb8 >
EXT3 FS on hdb6, internal journal
EXT3 FS on hdb7, internal journal
EXT3 FS on hdb8, internal journal
EXT3 FS on hdb5, internal journal

I've read on GRUB but am now suffering of info overload...:(

Also, can I install from an ISO image on a CD?:confused:


Thanks!:)

---

### Post by Pumalite on 2008-03-16
Download an iso from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on iso, burn at 4x or less, as 'image' and not 'data'
Install Ubuntu. Choose 2nd drive, Guided, Use Entire Disk. You'll have a new Grub that will pick up your Suse.

---

### Post by Herman on 2008-03-16
You are unlikely to have any problems with GRUB, since you have two IDE hard drives, as long as you have them plugged in and jumpered normally.
Ubuntu will detect the presence of Open SuSe, and Ubuntu will install its boot loader to MBR in the first hard drive and automatically give you an entry in Ubuntu's GRUB menu for booting Open SuSe.

In the computer I'm typing from now, I have Ubuntu Hardy Heron, Ubuntu Gutsy Gibbon, Ubuntu Feisty Fawn, Debian and Open SuSe.

Here is a copy of the bottom portion of my /boot/grub/menu.lst file,
```
## ## End Default Options ##

title        Ubuntu Gutsy, kernel 2.6.22-14-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e7e39ee8-2022-46bc-af71-a48ab3bd4f61 ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

title        Ubuntu Gutsy, kernel 2.6.22-14-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=e7e39ee8-2022-46bc-af71-a48ab3bd4f61 ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu Gutsy, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title        Ubuntu Feisty Fawn amdxz, (Configfile boot on /dev/hda2)
configfile    (hd0,1)/boot/grub/menu.lst
# kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=9e9e5184-127f-45d2-bf4a-e6f0a112f180 ro quiet splash 
# initrd        /boot/initrd.img-2.6.20-16-generic
# savedefault
# boot

# This entry was added by herman for a new
# linux installation on /dev/hda3.
title           Open SuSe-10.3-GM, (Chainloader boot on /dev/hda3)
root            (hd0,3)
chainloader +1

# This entry added by herman for a new
# linux installation on /dev/hda6.
title           Debian-40r0-1386, (Configfile boot on /dev/hda6)
configfile      (hd0,5)/boot/grub/menu.lst



# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 8.04 Hardy Heron Experimental System
configfile      (hd3,0)/boot/grub/menu.lst

``` As you can see, Ubuntu Gutsy Gibbon is my main operating system at the moment, and that's the one whose GRUB menu is installed in my first hard drive, and so comes up when I boot normally.
Ubuntu Gutsy Gibbon owns this menu.lst file, so I let it boot with GRUB's 'kernel' commands. When we have a kernel update in Ubuntu Gutsy Gibbon, the menu.lst file will be automatically updated to boot the new kernel in Ubuntu.

For the other operating systems, you will notice that I have modified my menu.lst file. They used to have kernel commands too, but I changed my menu.lst file to make the other operating systems boot by configfile or chainloader commands.

The reason why I did that, (don't worry, it's optional), is because that way each of the other operating systems will be booting by their own configuration files, so when each of the others has a kernel update, they will be able to automatically configure themselves to boot the latest kernel.

The configfile commands mean my Gutsy Gibbon's GRUB will open the other operating system's /boot/grub/menu.lst file, and Gutsy Gibbon's GRUB wuill boot the other operating system according to the information in that operating system's own configuration file.

The chainloader commands point Gutsy's GRUB to the other operating system's boot sector, and hand over control to the other operating system's boot loader. You can boot an operating system with LiLo or Windows NTLDR or some other foreign boot loader with the chainloader command. The other boot loader must be installed to the first sector of the operating system's partition for that to work.
That means I'm booting Open SuSe with it's own GRUB, since Open SuSe's GRUB is a little different to Ubuntu's GRUB.

Here's my Open SuSe's /boot/grub/menu.lst
```
# Modified by YaST2. Last modification on Fri Nov 23 22:37:15 UTC 2007
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,3)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 10.3
    root (hd0,3)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/scsi-SATA_WDC_WD1600JB-00_WD-WMANM7217041-part4    resume=/dev/sda5 splash=silent showopts
    initrd /boot/initrd-2.6.22.5-31-default

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 7.10, kernel 2.6.22-14-generic (/dev/sda1)###
title  Ubuntu 7.10, kernel 2.6.22-14-generic (/dev/sda1)
    root (hd3,0)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 7.10, kernel 2.6.22-14-generic (/dev/sdc1)###
title  Ubuntu 7.10, kernel 2.6.22-14-generic (/dev/sdc1)
    root (hd0,0)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu Feisty amdxz, kernel 2.6.20-16-generic (/dev/sdc2)###
title  Ubuntu Feisty amdxz, kernel 2.6.20-16-generic (/dev/sdc2)
    rootnoverify (hd0,1)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (hd0,3)
    chainloader (fd0)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 10.3
    root (hd0,3)
    kernel /boot/vmlinuz-2.6.22.5-31-default root=/dev/disk/by-id/scsi-SATA_WDC_WD1600JB-00_WD-WMANM7217041-part4 showopts ide=nodma apm=off acpi=off noresume edd=off 3
    initrd /boot/initrd-2.6.22.5-31-default
``` Don't worry about it too much if you don't understand what I'm talking about here, but if you do understand then you might want to set up your boot loaders something along the same lines. It's optional, but it's worth doing at some stage when you feel up to it.

Regards, Herman :)

---

