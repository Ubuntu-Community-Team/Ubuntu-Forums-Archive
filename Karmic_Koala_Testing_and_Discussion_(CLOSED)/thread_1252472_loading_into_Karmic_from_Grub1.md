---
title: "loading into Karmic from Grub1"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pt123 on 2009-08-28
I have Jaunty installed with Grub1 on my main partition (ext3).

Installed Karmic alpha 4 on another partition (ext4). 

I edited the menu.lst from the Jaunty installation to include Karmic.

```


title		Ubuntu 9.10 Karmic, kernel 2.6.31-5-generic on /dev/sda5
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-5-generic root=UUID=63ecb350-8566-45d2-b71a-631cbd56e2a6 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-5-generic
quiet

title		Ubuntu 9.10 Karmic, kernel 2.6.31-5-generic (recovery mode) on /dev/sda5
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.31-5-generic root=UUID=63ecb350-8566-45d2-b71a-631cbd56e2a6 ro  single
initrd		/boot/initrd.img-2.6.31-5-generic

title		Ubuntu 9.10, memtest86+ on sda5
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

```

But when booting up it says file not found. I am still able to boot into Jaunty.

is not possible? or do I have to add something else

Thanks

---

### Post by VMC on 2009-08-28
Where's jaunty. I see only karmic in the menu.lst

What's the output of ```
sudo fdisk -l
``` and ```
sudo blkid
```

Also, you are running grub legacy in the mbr, correct?

---

### Post by pt123 on 2009-08-29
> **VMC said:**
> Where's jaunty. I see only karmic in the menu.lst

I was  only showing what was relevant
Here is the rest:
```

title		Ubuntu 9.04, kernel 2.6.28-15-generic on /dev/sda3
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=3c043006-7aa0-4439-ab4b-0781ab42328a ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) on /dev/sda3
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=3c043006-7aa0-4439-ab4b-0781ab42328a ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu  (development branch), memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

```

> What's the output of ```
sudo fdisk -l
```
 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42d042cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1402    11261533+  83  Linux
/dev/sda2            1403        2677    10241437+  83  Linux
/dev/sda3            2678        3952    10241437+  83  Linux
/dev/sda4            3953       19457   124543912+   5  Extended
/dev/sda5            3953        5227    10241406   83  Linux
/dev/sda6            5228        6502    10241406   83  Linux
```
> and ```
sudo blkid
```
```
/dev/sda1: UUID="aee5740d-8867-4e21-b8fe-c4c3c5711d3b" SEC_TYPE="ext2" TYPE="ext3" LABEL="WinXP" 
/dev/sda2: UUID="2a8f6808-0a78-4cae-b35b-2b219a38bcee" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="3c043006-7aa0-4439-ab4b-0781ab42328a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="63ecb350-8566-45d2-b71a-631cbd56e2a6" TYPE="ext4" 

```

> 
Also, you are running grub legacy in the mbr, correct?
Yes from Jaunty

---

### Post by pt123 on 2009-08-29
I am wondering if Grub-legacy can load grub2 "images" can it handle it or know when to pass the handle over.

---

### Post by kansasnoob on 2009-08-29
I couldn't get mine to so I did this:

[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

I was fiddling around yesterday and did a reinstall of Karmic alpha 4 (for unrelated reasons) and I got it done again, but it was a pain because Nautilus kept crashing. 

Not sure if gedit is still crashing or not as I've been using leafpad in it's stead until they get it worked out.

Anyway, reverting can be done, although I hope to just get used to dealing with grub-2.

---

### Post by Rallg on 2009-08-29
I am able to boot into Karmic using "Grub4DOS" on a USB stick.

My machine has Windows XP. I installed Karmic on an ext2 partition, and put GRUB2 on that partition. I can boot to it using the modified XP bootloader (a technique that transfers control to Karmic's GRUB2 directly), or I can boot to it using Grub4DOS on a bootable USB stick. Since Grub4DOS is Grub1, I must imagine that it is possible to boot to Karmic when Grub1 is on the hard drive root, transferring control to Grub2 on the Karmic partition.

---

### Post by Nickedynick on 2009-08-29
I managed to set up booting into Karmic via Jaunty's grub. I just mounted the Karmic filesystem from Jaunty to check that the kernel image is the right number, and checked with GParted to see if the UUID number was the same. If you upgrade the kernel in Karmic you'll have to manually edit grub 1, but it seems to work.

---

### Post by pt123 on 2009-08-29
> **Nickedynick said:**
> I managed to set up booting into Karmic via Jaunty's grub. I just mounted the Karmic filesystem from Jaunty to check that the kernel image is the right number, and checked with GParted to see if the UUID number was the same. If you upgrade the kernel in Karmic you'll have to manually edit grub 1, but it seems to work.
That is pretty much what I did, can you post your config for the Karmic installation in your grub1. I just want to see if it is similar to mine.

---

### Post by Nickedynick on 2009-08-29
I'll have to do it tomorrow (not at home atm) but when I get back I'll make a point of posting it :)

---

### Post by pt123 on 2009-08-29
Thanks

---

### Post by Nickedynick on 2009-08-30
Here's the 'Other Operating Systems' part of my menu.lst, hope it helps! :)

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows 7
rootnoverify	(hd0,2)
savedefault
chainloader	+1

title		Ubuntu Karmic
uuid		1079e106-9f92-46be-8c3c-4b29982682ef
kernel		/boot/vmlinuz-2.6.31-7-generic root=UUID=1079e106-9f92-46be-8c3c-4b29982682ef ro  quiet splash
initrd		/boot/initrd.img-2.6.31-7-generic
```

---

### Post by mdurham on 2009-08-30
> **Nickedynick said:**
> If you upgrade the kernel in Karmic you'll have to manually edit grub 1, but it seems to work.

I think that you could eliminate the need to edit grub by changing /boot/vmlinuz-2.6.31-7-generic to /vmlinuz and /boot/initrd.img-2.6.31-7-generic to /initrd.img. That way it should always boot the latest kernel.
Cheers, Mike

---

### Post by pt123 on 2009-08-31
> **Nickedynick said:**
> Here's the 'Other Operating Systems' part of my menu.lst, hope it helps! :)

```

title		Ubuntu Karmic
uuid		1079e106-9f92-46be-8c3c-4b29982682ef
kernel		/boot/vmlinuz-2.6.31-7-generic root=UUID=1079e106-9f92-46be-8c3c-4b29982682ef ro  quiet splash
initrd		/boot/initrd.img-2.6.31-7-generic
```
Thanks very similar but on mine there is line with root
```
root	(hd0,4)
```

I will try removing it and see what happens

---

### Post by pt123 on 2009-08-31
> **pt123 said:**
> 
```
root	(hd0,4)
```

I will try removing it and see what happens

That didn't help:(

---

### Post by Nickedynick on 2009-08-31
I notice you didn't have the separate uuid line - maybe add that? to be honest I'm no expert, it just seemed to work for me!

mdurham - thanks for that, I'll give it a go! :) EDIT: Just tried that, it doesn't work for me.

---

### Post by ranch hand on 2009-08-31
You need the root line in your menu on grub-legacy.  Do not use the the same root as in grub2.

If it says (hd0,9) in grub2, you should enter (hd0,8) in grub-legacy.  Grub-legasy starts counting everything from 0.  Grub2 starts counting the drives from 0 and the partitions from 1 (as does gparted).

Other than tht just make your menu entry up with info from your grub.cfg entry to look like it should in your menu,lst (check your other entries).

---

### Post by mdurham on 2009-08-31
> **Nickedynick said:**
> mdurham - thanks for that, I'll give it a go! :) EDIT: Just tried that, it doesn't work for me.
Sorry about that Nickedynick. There are always two links in the root dir "/vmlinuz and /initrd.img" on every Ubuntu that I've installed, so I imagined you would have them too.
Cheers, Mike

---

