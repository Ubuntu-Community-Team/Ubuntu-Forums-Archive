---
title: "Setups didn't detect Windows"
date: 2009-02-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by airbornemist6 on 2009-02-08
Apparently, setup didn't notice I have Windows installed, because it didn't make an entry for it. I figure this might be because I had to change the BIOS bootorder (though, that shouldn't have had an effect on anything). I'm not sure what to do though, when I tried manually adding it to menu.lst, it wouldn't work. Should I try and restore the windows bootloader and then try and restore grub?

---

### Post by empthollow on 2009-02-08
i think the best course of action is to fix the menu.lst file.  please post your menu.lst file and the output of
```
sudo fdisk -l
```
this will tell us where the problem lies.

---

### Post by airbornemist6 on 2009-02-08
Here's the entries on the list:
```
title		Ubuntu jaunty (development branch), kernel 2.6.28-6-generic
uuid		b2b84022-559b-4657-8a3b-18b12e4094a4
kernel		/boot/vmlinuz-2.6.28-6-generic root=UUID=b2b84022-559b-4657-8a3b-18b12e4094a4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-6-generic
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-6-generic (recovery mode)
uuid		b2b84022-559b-4657-8a3b-18b12e4094a4
kernel		/boot/vmlinuz-2.6.28-6-generic root=UUID=b2b84022-559b-4657-8a3b-18b12e4094a4 ro  single
initrd		/boot/initrd.img-2.6.28-6-generic

title		Ubuntu jaunty (development branch), memtest86+
uuid		b2b84022-559b-4657-8a3b-18b12e4094a4
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows 95/98/NT/2000
root		(hd1,2)
makeactive
chainloader	+1

```

And here's my fdisk:
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd9ca562

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51cee735

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       51857       60802    71851008    7  HPFS/NTFS
/dev/sdb2               1       51856   416533288+   5  Extended
/dev/sdb5               1       51856   416533257   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc3dab189

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60673   487355841   83  Linux
/dev/sdc2           60674       60801     1028160    5  Extended
/dev/sdc5           60674       60801     1028128+  82  Linux swap / Solaris

```

I also tried getting all this to work by editing the root hd option on bootup, but the most I managed to get was a windows bootloader not found.

---

### Post by cariboo on 2009-02-08
From the fdisk out put it looks like you have two bootable windows partitions. Your windows entry in menu.lst doesn't point to either of them.

You need to use either (hd0,0) or (hd1,0) depending on which Windows partition you want to use.

Jim

---

### Post by airbornemist6 on 2009-02-08
Yeah, I've tried that. Didn't work. It was actually the first thing I tried. The proper one should have been (hd1,0). When I posted my menu.lst, I was in the process of changing it to completely random things that I knew wouldn't do anything, but I was desperate.

---

### Post by empthollow on 2009-02-08
this is a long shot, but some programming syntax is picky about having a blank line at the end of a file.  Not sure if you do or not, i haven't noticed one way or the other when using grub, but hey, it's worth a try.  good luck.

---

### Post by airbornemist6 on 2009-02-08
Nope. That's not it. Think the MBR might have somehow gotten overwritten?

---

### Post by empthollow on 2009-02-08
here's the page i refer to when i need to reinstall grub
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by airbornemist6 on 2009-02-08
I'm thinking of just reinstalling windows. I didn't put my key in, so it's about to expire anyway, I just wanted to get back into it at least once before reinstalling. But oh well. I think I'll try reinstalling both Windows and Jaunty, I'm pretty lazy.

---

### Post by empthollow on 2009-02-08
sounds easier than trying to fix it.  better luck next time around.

---

