---
title: "/ became hda7 (was hda6): kernel installer sticks to old values"
date: 2006-03-26
forum: Installation &amp; Upgrades
---

### Post by obnibolongo on 2006-03-26
Hi!
I meddled with partition numbers a while ago, by creating another partition.

/ was hda6, became hda7
swap was hda5, became hda6

I can fix the kernel panic at boot editing /boot/grub/menu.lst .
/etc/fstab was edited by me as well.

The problem is everytime I install a new kernel the kernel install scripts retrieve the old values from somewhere I don't know where and force me to manually reedit the menu.lst to get a bootable system again.

I'd like to know where it gets them (the old partition numbers) so I can manually fix the problem.

TIA,
-- 
obnibolongo

---

### Post by oscar on 2006-03-26
there should be a section in your /boot/grub/menu.lst that looks something like this:
```
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/mapper/linux-dapper ro vga=0x315
```

I think the last line is the line you need to change, dont uncomment it.
I guess it currently looks something like this:
```
# kopt=root=/dev/hda6 ro 
```
If this is right I think you need to change it to:
```
# kopt=root=/dev/hda7 ro 
```

---

### Post by obnibolongo on 2006-03-26
Thanks!
I found out another problem, but after playing with busybox and locate I also found the solution.

In addition to changing the lines you mentioned, one must edit /etc/mkinitramfs/initramfs.conf and at the bottom change

```
RESUME=/dev/hda5
```
to
```
RESUME=/dev/hda6
```

so resume works out-of-the box (and afterwards remove and install the kernel so the changes take effect in the initrd).

Thanks again :)

---

