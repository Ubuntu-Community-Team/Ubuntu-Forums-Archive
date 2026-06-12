---
title: "Frustrating problem with Ubuntu"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by aasodi on 2006-11-07
OK, I surrender.

I can't find the way how to install Ubuntu on HDD and boot Windows.

First, a was try to install beside my old Windows installation. After Ubuntu 6.10 installation I was unable to boot Windows (When in GRUB menu point windows installation, screen is clear with message starting up and blinking cursor. Nothing happens). I have try to play with SuperGRUB with no results. Only option is that I rewrite MBR with Windows loader, but then I don't have GRUB and Ubuntu :(

Then I was deleted all partitions from HDD and create new partitions in form:

1. Primary NTFS (Windows installation)
2. Primary Ext3 (root)
3. Extended
4. Logical NTFS (Windows data)
5. Logical Ext3 (/home)
6. Linux SWAP

Install Windows first, then Ubuntu (all default) with no luck. Same problem.

Here we go again...

All partitions deleted...

1. Primary NTFS (Windows installation)
2. Primary NTFS (Windows data)
3. Primary Ext3 (root)
4. Extended
5. Logical Ext3 (/home)
6. Linux SWAP

Install Windows, install Ubuntu... and, of course, no change :((

In this point a was totaly mad...

Here is my GRUB menu

[HTML]title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash noapic
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1[/HTML]

Here is output of fdisk -l (one of many :-))

[HTML]Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      101546    51179152+   7  HPFS/NTFS
/dev/sda2          101547      117737     8160264   83  Linux
/dev/sda4          117738      484518   184857593    5  Extended
/dev/sda5          117738      119818     1048792+  82  Linux swap / Solaris
/dev/sda6          130228      484518   178562632+   7  HPFS/NTFS
/dev/sda7          119820      130227     5245600+  83  Linux

Partition table entries are not in disk order[/HTML]

Hardware: Abit KN9Ultra AM2(nForce570Ultra), AMD X2 4200+, 2x1GB RAM, GeForce 7600GT, Seagate 250 GB (16MB cache, SATA II)...

ANY SOLUTION?
PLEASE HELP!
THANKS!

P.S. Sorry on my english, I hope that I was clear enough...

---

### Post by zek725 on 2006-11-07
Are these fresh installs? If you want to have fresh installation of both OS, install Windows (just as you did) then install Ubuntu. GRUB will change the MBR. 

When installing Ubuntu, the default settings will erase entire disk (including the windows ntfs partition) and automatically partition it for you. If you've partitioned your drive to have the first half to Windows and no partition yet for Ubuntu, choose the next option in the partition menu to have it automatically partition free space for you.

---

### Post by louieb on 2006-11-07
I'm not going to be much help. But after looking at your fdisk output and your menu.lst. I don't see a thing that I haven't seen work before. The only thing I suggest you try is change the root line to: ```
rootnoverify (hd0,0)
```
By the way your English is just fine. You described what you have done well.

---

### Post by aasodi on 2006-11-08
> **zek725 said:**
> Are these fresh installs? If you want to have fresh installation of both OS, install Windows (just as you did) then install Ubuntu. GRUB will change the MBR. 

When installing Ubuntu, the default settings will erase entire disk (including the windows ntfs partition) and automatically partition it for you. If you've partitioned your drive to have the first half to Windows and no partition yet for Ubuntu, choose the next option in the partition menu to have it automatically partition free space for you.

Yes, I have done fresh install of windows and ubuntu. I am familiar with ubuntu install options. I all cases I was select manual partitioning and then mount every partitions "manual". Windows partitions is mounted as /media/sda, and ubuntu partitions as root, home and swap.

Thanks!

---

### Post by aasodi on 2006-11-08
> **louieb said:**
> I'm not going to be much help. But after looking at your fdisk output and your menu.lst. I don't see a thing that I haven't seen work before. The only thing I suggest you try is change the root line to: ```
rootnoverify (hd0,0)
```
By the way your English is just fine. You described what you have done well.

Where do I change that line? In windows section of menu.lst?

Oho, my English is fine... That is nice to hear.
Thanks!

And now something on my language :-)
Pozdrav.

---

### Post by louieb on 2006-11-08
Yes in the windows section of your menu.lst
In you menu.lst Change:

```
title		Windows XP Media Center Edition
[COLOR="Red"]root		(hd0,0)[/COLOR]
savedefault
makeactive
chainloader	+1 
```
to:
```
title		Windows XP Media Center Edition
[COLOR="Red"]rootnoverify (hd0,0)[/COLOR]
savedefault
makeactive
chainloader	+1 
```
To make a copy of the file before you edit it, at a terminal window enter:
```

lou@gameu:~$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lstbak

``` 
To open the file so that you can edit it, at a terminal window enter:
```

lou@gameu:~$ gksudo gedit /boot/grub/menu.lst

```

---

### Post by aasodi on 2006-11-10
No change... :(

---

### Post by bulldog on 2006-11-10
If I may ask a question.....how about the live cd,did it run when you boot it?
Cause Ubuntu can't run on every peace of hardware it's possible you have the configuration which it can not deal with.

I should try the 6.06 instead of the 6.10 to see if it runs from cd and see if there are any troubles with it.
Of course you can try to run the 6.10 live cd to see if it goes well too.

But installing 6.10 is more of a hassle then installing 6.06.

The way you partitioned and your menu.lst and fstab there is nothing wrong as I can see,so I think there's some hardware which is not running properly with Ubuntu.
Just check the live cd to find out.

---

### Post by aasodi on 2006-11-10
> **bulldog said:**
> If I may ask a question.....how about the live cd,did it run when you boot it?
Cause Ubuntu can't run on every peace of hardware it's possible you have the configuration which it can not deal with.

I should try the 6.06 instead of the 6.10 to see if it runs from cd and see if there are any troubles with it.
Of course you can try to run the 6.10 live cd to see if it goes well too.

But installing 6.10 is more of a hassle then installing 6.06.

The way you partitioned and your menu.lst and fstab there is nothing wrong as I can see,so I think there's some hardware which is not running properly with Ubuntu.
Just check the live cd to find out.

Live CD runs just fine. Ubuntu 6.06 and 6.10 working perfectly like live CD. It runs perfectly even form HDD. I was able to install nVidia drivers, apps, upgrades, sound works, network, modem... in short term everything work. A have problem only with dual-boot.

I also try to instal SUSE 10.1 and this distro GRUB won't boot windows...

I will try to swap HDD or MBO (work in computer store :-)), and then will see.

Thanks.

---

