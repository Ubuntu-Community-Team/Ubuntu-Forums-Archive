---
title: "Cannot boot windows xp after ubuntu installation"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by dsims on 2007-05-10
Ive searched threads everywhere and cant find solution... 
And yes Im new to ubuntu  so command lines are asked...

Problem:
I cannot access my windows xp that I initially preinstalled onto the computer...

 After the installation of ubuntu I was directed to the grub screen where windows xp was an option to boot... but when i tryed to load the os I was taking to another screen that said some thing like

please wait...
something to stage 2

I could only see that screen for a second and directed me back to the grub screen... 
my xp os is currently set to root hd0,1 someone help me soon... I have a bunch a files that I need to access to on xp.... 

Thanks in advance

---

### Post by canadianwriterman on 2007-05-10
Look at your GRUB file and see what it says for your XP install.

```
sudo gedit /boot/grub/menu.lst
```

Make sure the location hd0,1 is correct.

---

### Post by dsims on 2007-05-10
Yes it is here it goes...

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=b3e9e35c-a512-4398-b4e8-71ab6b1570b6 ro quiet splash
initrd		/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.20-15-generic root=UUID=b3e9e35c-a512-4398-b4e8-71ab6b1570b6 ro single
initrd		/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
chainloader	+1

---

### Post by lsutiger on 2007-05-10
Same happened to me when I originally installed Ubuntu. What I did was do a repair install of Windoze, and that fixed it - but I could not boot into Ubuntu. So I did it a little differently.

Just as reference, did you have Ubuntu resize your hardrive for your installation or did you choose a partition that was already there? The first time, where I came across this problem, I had Ubuntu resize and partition. The second time was successful, where I had Windoze create a second partition that Ubuntu was able to installed on.

Just my 2cents

---

### Post by confused57 on 2007-05-10
If you can't boot into Ubuntu, you can do this from the live cd...open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
the -l is a small "L"

Post the output of the results, that may tell us something about what's going on.

---

### Post by dsims on 2007-05-10
I can still load up ubuntu... i get "Please wait... GRUB loading stage 2" but then it resets back to GRUB when I i choose the xp selection...

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       11228    90132682+   7  HPFS/NTFS
/dev/sda3           13804       14409     4867695   db  CP/M / CTOS / ...
/dev/sda4           11229       13803    20683687+   f  W95 Ext'd (LBA)
/dev/sda5           11229       12952    13847998+  83  Linux
/dev/sda6           13561       13803     1951866   82  Linux swap / Solaris
/dev/sda7           12953       13560     4883728+  83  Linux

Partition table entries are not in disk order

---

### Post by dsims on 2007-05-10
I used partition magic on windows to resize my partition... But to make the /, /boot, and swap partitions i resized in ubuntu during installation

---

### Post by Sand Lee on 2007-05-10
try changing window's root from "(hd0,1)" to "(hd0,0)"
 - it might not work, but it's worth a try..

---

### Post by confused57 on 2007-05-10
You might try a Window's entry similar to this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Windows XP Media Center Edition
rootnoverify  (hd0,1)
savedefault
makeactive
chainloader +1
```

---

### Post by dsims on 2007-05-11
ok tried the hd0,1 to hd0,0 and took me to a system disk check utility... and the previous the altered root entry and the same action with the flash of loading grub stage 2 occured.... Is there any more suggestions... I feel like im getting warmer to the solution...

---

### Post by confused57 on 2007-05-11
> **dsims said:**
> ok tried the hd0,1 to hd0,0 and took me to a system disk check utility... and the previous the altered root entry and the same action with the flash of loading grub stage 2 occured.... Is there any more suggestions... I feel like im getting warmer to the solution...

I would recommend that you download & burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

It's only a 5-7 Mb download & it might be able to boot your Windows...did you add the "makeactive" line to your Window's entry, in addition to "rootnoverify (hd0,1)"?

---

### Post by dsims on 2007-05-11
I did... i copied and paste the command you had... but ill try right now the super grub thing and tell you happen

---

