---
title: "grub not seeing XP"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by mab1376 on 2008-04-29
what info should i post so someone can get me the proper menu.lst entry to boot XP also, i have to change my ubuntu grub entry from hdd (1,0) to hdd (2,0).

---

### Post by dstew on 2008-04-29
We should be able to fix you up if you post the output of```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by mab1376 on 2008-04-29
```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d6ad8de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           2       30515   245103705    f  W95 Ext'd (LBA)
/dev/sda5               2       30515   245103673+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03a903a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       36332   291836758+   7  HPFS/NTFS
/dev/sdb2           38790       38913      996030   82  Linux swap / Solaris
/dev/sdb3           36333       38789    19735852+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000db6dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60801   488384001    7  HPFS/NTFS

```

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=aa0c1539-363e-4cbe-a0ca-6f90454afb40 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=aa0c1539-363e-4cbe-a0ca-6f90454afb40 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

sdb1 is my XP partition

---

### Post by mab1376 on 2008-04-29
bump

---

### Post by munky99999 on 2008-04-29
One of the best tools I have is actually the "super grub disk" not really sure where to get it. I've had it for awhile. Google it no doubt will pick it up.

Basically you boot it and it'll fix grub real well. I've even used it to repair systems which dont have any grub nor ntloader working properly because boot.ini was deleted or damaged.

It all has help and such built in to easily understand it.

---

### Post by zvacet on 2008-04-29
Maybe this can help but backup menu list

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-bak
```

```
sudo gedit /boot/grub/menu.lst
```

and replace your windows entries with this 


title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


sava file and close it.After reboot you should be able to boot in windows.

---

### Post by mab1376 on 2008-04-29
thanks!!

my XP is actually hd(0,0)

looks like this now and works great!

> title Microsoft Windows XP Professional
rootnoverify (hd0,0)
makeactive
chainloader +1

---

### Post by adrian15 on 2008-04-30
> **munky99999 said:**
> One of the best tools I have is actually the "super grub disk" 
I've even used it to repair systems which dont have any grub

That's right because you can use **Boot Linux directly**.
> **munky99999 said:**
> 
 nor ntloader working properly because boot.ini was deleted or damaged.

So... you mean in a windows only computer.

If you take a Windows partition and delete its boot.ini it does not boot. However if you boot with SGD and select Boot Windows... it does boot ok?

That's what you're saying?

adrian15

---

### Post by munky99999 on 2008-04-30
> So... you mean in a windows only computer.

If you take a Windows partition and delete its boot.ini it does not boot. However if you boot with SGD and select Boot Windows... it does boot ok?

That's what you're saying?
I've done it twice.
[Eveonline deleted boot.ini]("http://www.eve-online.com/news/newsOfEve.asp?newsID=500")
I used the super grub cd to repair/boot windows. Instead of doing it all with recovery console and such.

The other time I wanted to clean up the boot.ini because 1 option was dead and didnt really exist but the msconfig thing which checks said it was fine. So I deleted the one entry. Obviously I chose the wrong one :( So again I used super grub to repair.

---

### Post by mab1376 on 2008-04-30
it does a nice job, it rubuilt grub for me, must be something with the new distro not detecting my xp partition i had to manually edit it.

it can also restore a windows bootloader completely removing grub or can just boot into a windows partition without any changes at all.

---

### Post by adrian15 on 2008-05-05
> **munky99999 said:**
> I've done it twice.
[Eveonline deleted boot.ini]("http://www.eve-online.com/news/newsOfEve.asp?newsID=500")
I used the super grub cd to repair/boot windows. Instead of doing it all with recovery console and such.


I have read your answer and that link and I still do not know what steps you save by using SGD.

And my question is still there... You delete boot.ini and Windows does not boot... but you somehow boot it with SGD... how?


> **munky99999 said:**
> 
The other time I wanted to clean up the boot.ini because 1 option was dead and didnt really exist but the msconfig thing which checks said it was fine. So I deleted the one entry. Obviously I chose the wrong one :( So again I used super grub to repair.

So you left your boot.ini with one boot entry that did not boot because partition number or whatever was incorrect...

and you said that with SGD you did repair it?

How?

Thank you.

adrian15

---

### Post by jerrallan on 2008-05-05
I agree with Munkey 9999. Super Grub did a good job for me when I lost my Linux Boot. [Although I LOST the grub fiddling around with it]. A good utility located at:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

