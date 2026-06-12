---
title: "grub error 17 (no multiboot related)"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by sarte on 2008-01-19
I have a strange problem with my Kubuntu/ubuntu installation. Few days ago my old HD died. I was anticipating this so no data was lost. Yesterday I decided to install the Kubuntu to my machine. It should've been an easy task - after all I had successfully installed kubuntu and ubuntu to that particular machine before, but no. Only thing that's changed is the HD. it used to be 80GB now its 500GB. The HW it self is an old HP desktop with 1.6GHz p4/512MB GF4 ti 4200.

And the problem it self:

Grub gives me error 17. First I checked the menu.lst. All is ok in there. Grub points at 0,2 which was correct. Then I tried to reinstall the grub. No luck there either. From somewhere (probably an old windows habit) I get in to my head that the system should be in the first logical partition. I used GParted livecd and made a nice EXT3-partition for kubuntu as first partition and reinstalled the kubuntu. Still no luck. Error 17 persisted. At this point I'm beginning to be quite hopeless about this. What the hell is wrong with my system??

Few things you probably wanna know:

**When starting from LiveCD (boot from first hard disk):**

```
Booting from local disk...
isolinux: Disk error 05, AX = 0000, drive 80
boot failed. Press any key to continue...
```

**Fdisk gives following:**
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       35143   282286116   83  Linux
/dev/sda2           35144       35274     1052257+  82  Linux swap / Solaris
/dev/sda3           35275       60801   205045627+  83  Linux


```

**Menu.lst (cut out the commented lines)**
```


title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=564a88d7-b5f3-4cbe-b12
5-71d549755415 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=564a88d7-b5f3-4cbe-b12
5-71d549755415 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

**Device.map**
```

(hd0)   /dev/sda

```

---

### Post by confused57 on 2008-01-19
I'm guessing that your grub error should be error 18, instead of error 17...sometimes grub gets it wrong:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

You can either install a /boot partition(approx 500 Mb) at the beginning of the hard drive or reduce your first partition to less than 137 Gb.

---

### Post by sarte on 2008-01-19
> **confused57 said:**
> I'm guessing that your grub error should be error 18, instead of error 17...sometimes grub gets it wrong:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

You can either install a /boot partition(approx 500 Mb) at the beginning of the hard drive or reduce your first partition to less than 137 Gb.

That did the trick. Thank you very much. I reduced the partition size to 20GB and it now runs like a charm.

---

