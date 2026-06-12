---
title: "Make Bootable External HD"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by kierhon on 2008-01-12
I'm trying to boot Ubuntu Gutsy Gibbon from an external HD. The ideal conditions i'm looking to meet are:

1. If External HD is plugged in: boot Ubuntu from it
2. If External HD is NOT plugged in: boot XP from internal IDE

So far i've set up my computer's BIOS to boot in this order:
1. CD/DVD
2. USB
3. HD

I've successfully installed Ubuntu on the external HD with GRUB without effecting my MBR on my internal IDE HD. I get the Loading Grub 1.5 screen and then Error 17. 

sudo fdisk -l    returns:
> Disk /dev/sda: 160.0 GB (device boot /dev/sda1)
Disk /dev/sdb: 50.0 GB (device boot /dev/sdb1 : linux, /dev/sdb2 : extended, /dev/sdb5 : swap)

This was the default device.map and menu.lst:
> 
device.map
(hd0)  /dev/sda
(hd1) /dev/sdb

menu.lst
Linux root as (hd1,0)
XP root as (hd0,0)

I tried switching them (having linux be hd0) thinking that on boot it might be mounted first, but that didn't change anything. Any help/advice is greatly appreciated! :)

---

### Post by logos34 on 2008-01-12
> **kierhon said:**
> I tried switching them (having linux be hd0) thinking that on boot it might be mounted first, but that didn't change anything

But did you also change linux root in menu.lst to (hd**0**,0)?

---

### Post by kierhon on 2008-01-12
Yes i did, i also tried uncommenting groot and changing that to hd0 as well

---

### Post by logos34 on 2008-01-12
> **kierhon said:**
> Yes i did, i also tried uncommenting groot and changing that to hd0 as well

groot should have a '#' before it, so put it back

But (hd0,0) should work...hmm.  Not sure why it's giving you a problem.

add: You could[ reinstall grub from the live cd]("http://ubuntuforums.org/showthread.php?t=224351").  Might fix it.

---

### Post by kierhon on 2008-01-12
I'm stumped as well. Poop.

To reinstall grub from live CD how would i do a find? Wouldn't i have to mount the external HD

/media/disk/

---

### Post by kierhon on 2008-01-12
tried reinstalling grub... still nothing. I'm going to remove my internal HD and try to install on the usb, maybe that'll offer something..

---

### Post by kierhon on 2008-01-12
Okay it boots GRUB and ubuntu just fine without internal HD. Is is possible there's another grub loader on internal HD? If so how would i remove it?

---

### Post by logos34 on 2008-01-12
boot without the external usb connected...if you see grub then it's overwritten windows bootloader.  To restore windows bootloader go into the recovery console on the XP install cd and execute **fixmbr**.  Or use Super Grub Disk.

for future reference: root partition does not need to be mounted to reinstall grub from live cd

---

### Post by kierhon on 2008-01-12
I booted without external and my MBR is just fine. I ran fdisk /mbr just to make sure of this as well. I have a feeling that my BIOS is mounting it in a different order. Not really worth all this hassle anyways. I just backed up everything and i'll dual boot on my internal from scratch. Thanks for the tips tho.

---

