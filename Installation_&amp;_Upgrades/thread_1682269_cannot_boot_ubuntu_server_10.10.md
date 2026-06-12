---
title: "cannot boot ubuntu server 10.10"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by lucas911 on 2011-02-05
hi guys,

i have a proliant dl380 server running with RAID 0.

I've installed ubuntu server edition 10.10 on it with the default configurations.  Grub2 installed.

When i boot it give me the /dev/disk/by-uuid ... error

The thing is that when i check for the "by-uuid" directory, it doesn't exist.  There is a directory called "by-path" instead.

i can go to the shell and i've checked that FSTAB and GRUB.CFG point to the correct UUID.  

I also get an error during booting: 

udevd-work[73]: '/sbin/modprobe -bv pci:v0000...i00' unexpected exit with status 0x0009.

I tried everything, any help would be appreciated.

------------

solved my own post:

here is what i did. 

booted through live Cd

add cpqarray to /etc/mkinitramfs/modules (nano /etc/modules and add "cpqarray" as the last line)

and re-installed ... 

no more error loaded great

now i'm gonna try it on RAID 5

---

