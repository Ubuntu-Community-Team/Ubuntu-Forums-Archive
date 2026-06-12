---
title: "Removing x86 Kernel"
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by Zmija on 2006-08-14
Yesterday I download i686 Kernel! And now I use only i686 kernel... But, I want to remove old x86 Kernel... I go to Synaptic and choose linux-386 etc (3 package's) and mark like Complete Removal.. Click Apply and first I have to Update old x86 Kernel to remove same one? can I manualy remove it without update? :confused: 


THNX for Help, and sorry for my bad English..

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-686 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-686
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by Zmija on 2006-08-14
Bump

---

### Post by Zmija on 2006-08-15
bump bump :confused:

---

