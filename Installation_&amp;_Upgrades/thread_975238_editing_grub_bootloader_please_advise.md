---
title: "editing grub bootloader please advise"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by theevilhacker on 2008-11-08
ok guys 

I am successfully dual booting vista and ubuntu 8.10 
but I want to take it a step further I have also installed osx 10.5
"I actually own a copy of leopard so don't flame me!" and for the life of me cant figure out how to add my mac osx partition to the grub bootloader 

here is the output from my fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x82eaff01

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5047    40539996    7  HPFS/NTFS
/dev/sda2            5048        9039    32065740    5  Extended
/dev/sda5   *        6093        9039    23669760   af  Unknown
/dev/sda6            5048        6041     7984242   83  Linux
/dev/sda7            6042        6092      409626   82  Linux swap / Solaris

Partition table entries are not in disk order

the "unknown" partition is my mac partition but it's labeled "sda5" and not the standard hd0,0 configuration

I have added an entry to my grub file but it wont see the partition how do I label an sda partition  ?

here is the entry I made ignore what there now thats after trying any combination I could think of 

title OSX86
root (hd0,6)     <-------the question is what do I put here?
makeactive
chainloader +1 

any help would be greatly appreciated ! thanks in advance.

---

### Post by Mr_JMM on 2008-11-08
0,4

So you'll have:
```
title         OSX86
root          (hd0,4)
makeactive
chainloader +1
```

Make sure it all goes below the line that says:

```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

The hdx,y starts at 0 so is one less than sdyz

---

### Post by theevilhacker on 2008-11-08
thank you trying now.. I knew the part of being below the debian banner..

so to ask one more stupid question so I never run into this problem again how does grub number these partitions?? is the a complete list so I can have it on hand for future reference?

---

### Post by Mr_JMM on 2008-11-08
Not 100% what you're after but...

As mentioned above, hd is one less than sd so:

sda1 = hd0,0
sda2 = hd0,1
sda3 = hd0,2

...

sdb1 = hd1,0
sdb2 = hd1,1
sdb3 = hd1,2

...

sdc1 = hd2,0
sdc2 = hd2,1
sdc3 = hd2,2

Is this what you meant? Sorry if it's not.

---

### Post by bulldog on 2008-11-08
Take a look here,all you want to know about GRUB is here,thanks to Herman.

[http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible](http://users.bigpond.net.au/hermanzone/p15.htm#Common_Booting_Errors_and_Some_Possible)

---

### Post by theevilhacker on 2008-11-08
ok just tried it and got error 12

Error 12: Invalid device requested 

now is this a problem of macosx or am I still having issues with grub?

I tried doing the 

"press e to edit"

while in the grub menu and tried all from (hd0,0)-(hd0,6) and nothing boots mac osx..any suggestions?


now to add something to this whole thing I'm not sure how many of you have osx installed but after installing ubuntu I'm not able to boot from the macosx dvd either into leopard and that's how I was booting into macosx do I have to copy the mac bootloader somewhere somehow?

---

### Post by theevilhacker on 2008-11-08
anyone?

---

