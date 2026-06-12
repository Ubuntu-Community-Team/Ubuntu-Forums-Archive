---
title: "duplicate os's in grub?"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by 565Customz on 2008-06-14
hey guys, when i boot up the grub shows like 4 operating systems (not counting my windows and utility partitions, there are all identical herron os's. it seems like i get one more after each major update. any ideas?

---

### Post by overdrank on 2008-06-14
> **565Customz said:**
> hey guys, when i boot up the grub shows like 4 operating systems (not counting my windows and utility partitions, there are all identical herron os's. it seems like i get one more after each major update. any ideas?

HI and yes you will see a addition with at kernel upgrade. Here is mine
Example
```
title		Ubuntu 8.04, kernel 2.6.24-18-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ef397f4a-7784-4cf2-83c3-6818b5a0fde0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=ef397f4a-7784-4cf2-83c3-6818b5a0fde0 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ef397f4a-7784-4cf2-83c3-6818b5a0fde0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=ef397f4a-7784-4cf2-83c3-6818b5a0fde0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
If you wish to not see them during the grub you can comment them out with #
Here is a good link on the grub
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by lisati on 2008-06-14
The version numbers usually increase, and let you go back to a working older version if the update doesn't work as well as is hoped.

---

### Post by 565Customz on 2008-06-15
thanks for the link, but i think there is more to it than just commenting them out, my computer seems way to slow for there not to be more to the problem? wouldnt it be better to completely remove the unused stuff?

---

### Post by housam on 2008-06-15
You can uninstall unused kernel from synaptec package manager.
just go for system >> admin >> synaptec package manager and search for the kernels that you need to uninstall it and uncheck the square infront of it and teck apply.this will remove them from your system.
I suggest to keep one of those kernels as a spare just in case something happened to the current one.

---

### Post by 565Customz on 2008-06-15
thanks worked perfect

---

