---
title: "Grub Error 13: Invalid or unsupported executble format"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by evets25 on 2008-08-30
Alright so here's the situation: I had Ubuntu installed on my computer, and I decided to install windows XP again to play a few games that I just couldn't get working properly in wine. I'm aiming for a dual-boot setup, but there's a catch: I have a rather complicated partition setup, with 3 drives. I'll list them as the BIOS sees them. Here we go: 

(IDE) Primary Master: 20Gb Maxtor with 3 partitions 
    - swap
    - /boot
    - /

(IDE) Primary Slave: 80Gb WD with 1 partition now, 2 partitions before
    NOW: 
    - Windows XP 
    BEFORE: 
    - swap
    - ~/backup

(SATA) Third Master: DVD-RW drive

(SATA) Fourth Master: WD 500Gb drive with 2 partitions:
    - swap 
    - ~/storage

When I installed Windows XP, what I did was simply unplug everything except the second drive (the 80Gb one) and the DVD drive, and set the drive's jumper settings to "master" instead of "slave". Then, I booted from the winXP install CD and installed normally. 

So far so good. I then tried to plug in the other drives, setting the fresh winXP drive back to the primary slave, and then booting into ubuntu. I managed to do that, although it spewed a bunch of error messages into console and I had to do some fstab hacking to make it happy again. I could even mount the windows partition through nautilus, as if it were a removable device. 

So then, I went to edit my grub menu, to add winXP, and this is where it screwed up. I backup it up, then added the following entry to /boot/grub/menu.lst:
```

title         Windows XP
root          (hd1,0)
savedefault   
makeactive 
map           (hd0) (hd1)
map           (hd1) (hd0)
chainloader +1

```
I copied that by hand, not copy-and-paste, so there may be typos, either in this version or the actual version on my computer. 

I get to the grub OS selection screen, select "Windows XP" and that's when I get this error:
```
Error 13: Invalid or unsupported executable format

Press any key to continue...

```

I suspect that the problem is that i've got the wrong numbers for the root(hd#,#) line, but AFAIK, the primary slave, first partition should be (hd1,0), like I have it. I've also tried endless variations on that grub entry, rearranging the lines, using "rootnoverfiy" instead of "root", and removing/adding the "makeactive" and "savedefault" lines. I can't think of anything else to do. 

Help.

---

### Post by gmxgeek on 2008-08-30
I don't understand. Why didn't you just let windows dominate the mbr like it wants, then reinstall grub? makes life so much easier.

What i would do, is use the XP recovery or install CD, get a recovery console, type fixmbr, which will wipe grub and put in windows' boot loader, then launch your ubuntu livecd and reinstall grub from there. That way everything should be happy

---

### Post by evets25 on 2008-08-30
I didn't do that because I wanted something to fall back on when it screwed up my MBR. This way, the ubuntu install is completely untouched and works fine. I thought it would be a simple matter to simply add an entry to grub to make it boot windows. There's also no risk of losing anything that I have stored on my ubuntu partitions.

---

### Post by gmxgeek on 2008-08-30
well, try running fixmbr and see if you can boot into windows. If so, then reinstall grub and it should be good. If not, then a larger problem exists than just a grub config

---

### Post by evets25 on 2008-08-30
Running fixmbr with all the drives set up the way they are will break everything, since windows is on the primary slave, not the primary master. That would make the windows bootloader be placed in the MBR of the primary master, REPLACING grub (although not entirely since it's on it's own partition). The windows bootloader would then proceed to look for a windows partition on the primary master, find a bunch of weird partitions it doesn't know, and then proceed to keel over and die with an obscure error message. 

Running fixmbr with the windows drive set back to primary master as the only drive would result in... nothing changing. If I set it to primary master and boot, I can boot into windows just fine.

Linux boots, windows boots, grub isn't set up right.

There's no reason doing it my way wouldn't work. I know it's possible, I've seen other examples of it. I'm just not doing something right.

---

### Post by gmxgeek on 2008-08-30
If you can boot into windows just fine when windows is master, can you boot into ubuntu?

---

### Post by evets25 on 2008-08-30
If I set windows to master, then I unplug the other drive, so no, I can't boot into ubuntu. If I were to switch the primary master and secondary slave, (i.e.: windows is master, ubuntu is slave) then I still wouldn't be able to boot into ubuntu, since that would involve adding *ubuntu* to the NT bootleader, instead of the other way around.

---

### Post by gmxgeek on 2008-08-30
Ah i see. Well installs across multiple partitions with grub are out of my depth. Sorry

---

### Post by JohanSwe on 2008-11-08
I also get the same message when trying to start Windows XP from grub:

> Grub Error 13: Invalid or unsupported executble format  Reply to Thread

What could be the problem?

```
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		ce48d26f-447c-47d5-8ecd-9b66c63c7fba
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ce48d26f-447c-47d5-8ecd-9b66c63c7fba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		ce48d26f-447c-47d5-8ecd-9b66c63c7fba
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=ce48d26f-447c-47d5-8ecd-9b66c63c7fba ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.24-21-generic
uuid		ce48d26f-447c-47d5-8ecd-9b66c63c7fba
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ce48d26f-447c-47d5-8ecd-9b66c63c7fba ro quiet splash 
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
uuid		ce48d26f-447c-47d5-8ecd-9b66c63c7fba
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ce48d26f-447c-47d5-8ecd-9b66c63c7fba ro  single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.10, memtest86+
uuid		ce48d26f-447c-47d5-8ecd-9b66c63c7fba
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb16db16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7295    58597056    7  HPFS/NTFS
/dev/sda2            7296        9726    19527007+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x9f3cfba7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         323     2441848+  82  Linux swap / Solaris
/dev/sdb2             324        1615     9767520   83  Linux
/dev/sdb3            1616       32301   231986160   83  Linux

```

---

### Post by caljohnsmith on 2008-11-08
JohanSwe, try this entry for Windows:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
If that doesn't work, let me know exactly what happens when you select it from the Grub menu.

---

### Post by JohanSwe on 2008-11-09
> **caljohnsmith said:**
> JohanSwe, try this entry for Windows:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
If that doesn't work, let me know exactly what happens when you select it from the Grub menu.
Thanks!

I now know what caused it though.

In bios I had by mistake set drive1 as startup drive where it should be drive0.

Problem fixed :)

---

### Post by altima on 2009-02-21
I've got exactly the same issue but trying to load Mac OS iDeneb with grub.

I've got three hdd's: Swap and boot partitions are on 1 hd0, hd1 is a data hdd, and mac os is on hd2.

and the remapping you've described doesn't help.

---

