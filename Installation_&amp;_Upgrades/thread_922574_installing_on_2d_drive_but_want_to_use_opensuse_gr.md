---
title: "installing on 2d drive but want to use opensuse grub"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by Shadowmeph on 2008-09-17
ok this is what I want to do I have 2 drives and on my first drive I have Vista and Opensuse I want to install a few different Linux distros on my second drive but  Iwant to use the opensuse grub which is on the first drive.
my first install on my second drive will be Kubuntu I am not sure how to install Kubuntu onto the second drive without installing grub and after kubuntu is installed how do I tell it to use the opensuse grub this is what I have 

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a914a91

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13019 104567085 7 HPFS/NTFS
/dev/sda2 13019 38913 208000563+ f W95 Ext'd (LBA)
/dev/sda5 13019 13281 2103491 82 Linux swap / Solaris
/dev/sda6 13281 13543 2112516 82 Linux swap / Solaris
/dev/sda7 13544 16154 20972826 83 Linux
/dev/sda8 16155 38913 182811636 83 Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88008800

Device Boot Start End Blocks Id System

and this is the grub menu
# Modified by YaST2. Last modification on Sun Sep 14 20:35:43 PDT 2008
default 0
timeout 4
gfxmenu (hd0,6)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux-2.6.25.16-0.1-default###
title openSUSE 11.0 - 2.6.25.16-0.1 (default)
root (hd0,6)
kernel /boot/vmlinuz-2.6.25.16-0.1-default root=/dev/disk/by-id/scsi-SATA_ST3320620AS_6QF15JBZ-part7 resume=/dev/sda6 splash=silent showopts vga=0x317
initrd /boot/initrd-2.6.25.16-0.1-default

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
rootnoverify (hd0,6)
chainloader (hd0,0)+1

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.0 - 2.6.25.16-0.1
root (hd0,6)
kernel /boot/vmlinuz-2.6.25.16-0.1-default root=/dev/disk/by-id/scsi-SATA_ST3320620AS_6QF15JBZ-part7 showopts ide=nodma apm=off acpi=off noresume edd=off x11failsafe vga=0x317
initrd /boot/initrd-2.6.25.16-0.1-default

###Don't change this comment - YaST2 identifier: Original name: linux###
title Debug -- openSUSE 11.0 - 2.6.25.16-0.1
root (hd0,6)
kernel /boot/vmlinuz-2.6.25.16-0.1-debug root=/dev/disk/by-id/scsi-SATA_ST3320620AS_6QF15JBZ-part7 resume=/dev/sda6 splash=silent showopts vga=0x317
initrd /boot/initrd-2.6.25.16-0.1-debug

###Don't change this comment - YaST2 identifier: Original name: xen###
title Xen -- openSUSE 11.0 - 2.6.25.16-0.1
root (hd0,6)
kernel /boot/xen.gz
module /boot/vmlinuz-2.6.25.16-0.1-xen root=/dev/disk/by-id/scsi-SATA_ST3320620AS_6QF15JBZ-part7 resume=/dev/sda6 splash=silent showopts vga=0x317
module /boot/initrd-2.6.25.16-0.1-xen
```

can anyone help me with this?

---

### Post by natirips on 2008-09-17
Add something like this at the bottom (you may wish to change the kernel version):


title		kubuntu
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet


Edit: Also change root= field to /dev/sdb0 or whereever you install kubuntu to, or just do as the post below says.
Also see "man grub" from kubuntu's live CD.

---

### Post by caljohnsmith on 2008-09-17
When you get to the final stage of the Kubuntu installer, if you click the "advanced" button, you can tell it where to install Grub's boot loader. By default it is usually (hd0) or your boot drive, but change it to /dev/sdb so that it installs Grub to the master boot record of your Kubuntu drive (assuming sdb is the kubuntu drive). Then you can add entries to your OpenSUSE menu.lst for Kubuntu like natirips gave in his post, or you can simply link to Kubuntu's menu.lst:
```
title Kubuntu
configfile (hd1,X)/boot/grub/menu.lst
```
Where X will be Kubuntu's partition, but remember that Grub's numbering starts at 0, not 1. 

And just as an aside, why do you have two swap partitions on your sda drive? You should only need one. Different linux distros can even share the same swap partition. 

Let me know how it goes or if you have further questions.

---

### Post by Shadowmeph on 2008-09-17
> **caljohnsmith said:**
> When you get to the final stage of the Kubuntu installer, if you click the "advanced" button, you can tell it where to install Grub's boot loader. By default it is usually (hd0) or your boot drive, but change it to /dev/sdb so that it installs Grub to the master boot record of your Kubuntu drive (assuming sdb is the kubuntu drive). Then you can add entries to your OpenSUSE menu.lst for Kubuntu like natirips gave in his post, or you can simply link to Kubuntu's menu.lst:
```
title Kubuntu
configfile (hd1,X)/boot/grub/menu.lst
```
Where X will be Kubuntu's partition, but remember that Grub's numbering starts at 0, not 1. 

And just as an aside, why do you have two swap partitions on your sda drive? You should only need one. Different linux distros can even share the same swap partition. 

Let me know how it goes or if you have further questions.

thats what I was confused about I just used the default opensuse install and it put in 2 swap partitions  lol thanks I am going to try this so far the only distro I have tried that isn't really buggy is Ubuntu hardy but I just want to see what else is out there for Distros thank you again

---

