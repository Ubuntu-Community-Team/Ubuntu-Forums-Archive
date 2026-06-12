---
title: "Move /boot to a new partition"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by soldonz on 2007-05-23
Hi,

I have ubuntu dapper6.06 installed on an USB HDD and it have worked fine on most PCs in my lab, except the main server (intel xeon) which complains that the boot partition is too large.  I think it's because I didn't give /boot its own small partition. 

So, I have spend hours working on this after hours of searchign on the net without any guide or tutorial on how to move /boot to its own partition. 

Here is what I have done:

I have resized the harddisk and created a new 64mb partition at the beginning of the disk.
I have installed grub on this partition and move everything in /boot to this partition.
I have changed the menu.lst to reflect the change so now grub seems to work fine.
I have changed fstab to mount the new partition as /boot
it now loads the kernel and initrd.. etc..  however, at the end of grub, it says something like "uncompressing linux ok. booting kernel" and it then it just hangs there forever.
so I think grub had no problem finding the files it needs. Donno why it still doesn't boot, I must have one or a few steps here. 

FYI: 
Here is my menu.lst
```

title		Ubuntu, kernel 2.6.15-26-k7
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-k7 root=/dev/disk/by-id/usb-StoreJet_StoreJet-part3 ro quiet splash
initrd		/initrd.img-2.6.15-26-k7
savedefault
boot

```

Here is my device.map
```

(hd0) /dev/disk/by-id/usb-StoreJet_StoreJet

```

here is my fstab
```

proc            /proc           proc    defaults        0       0
/dev/disk/by-id/usb-StoreJet_StoreJet-part3       /               ext3    defaults,errors=remount-ro 0       1
/dev/disk/by-id/usb-StoreJet_StoreJet-part1       /boot           ext2    defaults        0       2
/dev/disk/by-id/usb-StoreJet_StoreJet-part4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

kindly note that I use by-id pointers to my partitions since I want to be able to plug it in any USB bootable PC and be able to use it. UUID screwed up for me somehow by changing, so by-id pointers has been most stable. The installation has been working very well in the past on all modern PCs. it just that this one intel server is giving me problem. 

Would someone kindly provide the correct procedure to move /boot to its own partition and the files that need to be changed? 

Many thanks,

Soldonz

---

### Post by Metacarpal on 2007-05-23
You have kernel set to /vmlinuz-2.6.15-26-k7 and initrd set to /initrd.img-2.6.15-26-k7 in your menu.lst
I think that if you check, you'll find these are both in /boot
So those two lines need to read:
```
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/disk/by-id/usb-StoreJet_StoreJet-part3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
```

---

### Post by soldonz on 2007-05-24
Thanks Metacarpal

I tried your suggestion just now but it didn't help.
Grub failed with Error 15, stating that it can't find the needed files anymore. 

As I stated in my original post, grub was able to find the files, go through kernel and initrd command without problem. it failed at the final stage when it executes the boot command. 

well.. this seems like a complicated problem. I hope someone would be kind enough to post a tutorial or guide for this. 

Thanks,

Soldonz

---

