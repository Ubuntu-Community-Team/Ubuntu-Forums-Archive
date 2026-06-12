---
title: "GRUB doesn't show Windows br"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by trunks14 on 2007-07-14
Hello, I'm proud to say that now i only use ubuntu :), no more windows anymore, i have firefox, gaim, compile with cc, use java from the terminal etc BUUTT there're some games i still want to play, from time to time... when i installed ubuntu i partitioned my Disk like this:

1GB for Swap
20 GB for the old Windows Installation
10 GB for filesystem
7 GB unused :P

One thing, what used to be windows is now mounted on /dev/hda6 and the data is still there, a 'File Programs' folder, 'Windows' folder :)

Well my problem is: Cannot boot windows, GRUB only shows ubuntu, i know i can fix it with 'fixmbr' but i want to keep ubuntu since we all know Microsoft will screw up other OS boot records.

Any idea?

---

### Post by bdtgp on 2007-07-14
Sounds like you lost your Windows bootloader.  There is a way to find it and use it. Search for it.  I can't think of which thread of the top of my head.  Sorry, but I just wanted to let you know that I *think* I saw a solution for that somewhere today.

---

### Post by trunks14 on 2007-07-14
you mean like using it with GRUB?

I think i just found a way, gonna try that

---

### Post by trunks14 on 2007-07-14
Here's my layout according to fdisk:

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         131     1052226   82  Linux swap / Solaris
/dev/hda2            1040        4864    30724312+   f  W95 Ext'd (LBA)
/dev/hda5            1040        2314    10241406   83  Linux
/dev/hda6            2315        4864    20482843+   7  HPFS/NTFS

```

I only have one HardDisk, ok according to this information i added this to GRUB list:

```

title		Windows XP
rootnoverify	(hd0,5)
makeactive
chainloader	+1

```

hda6 shows my files that were in the Windows partition, as th GRUB menu shows ubuntu to be intalled in (hd0,4) i supposed that the right configuration for Window XP should be (hd0,5), but I'm not really sure. Also, following some advices from other source i put i like 'rootnoverify' as 'GRUB must not understand NTFS in order to do a chain load'. Ok i thought this was going to work but GRUB throwed:

'Error 12: invalid device requested'

I don't know what else to do, any idea?

---

Now I'm almost sure it's because the Windows installation is a logical partition....any idea on how to make it primary or something like that?
actually i did a fixmbr (booted from a Windows CD) and i wasn't able to boot, so i booted from a live CD and restored grub :(

Here's the layout, per GPartED :P

[[IMG]http://img223.imageshack.us/img223/9546/gpartedlayoutkz7.th.png[/IMG]](http://img223.imageshack.us/my.php?image=gpartedlayoutkz7.png)

What's that Alert Symbol for?

Hope remains here :)

---

### Post by trunks14 on 2007-07-15
it seems nobody has ever been able to solve this problem, :(

---

### Post by confused57 on 2007-07-15
This explains problems booting Windows on a logical partition:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#12_)

---

### Post by trunks14 on 2007-07-15
it appears that this is a known problem across the linux community, caused by a bug in 'parted' which many installations use, fedora and ubuntu included. It has to do with the disk's geometry.

Do you know of Geometry checking and partition restore tools?

---

### Post by trunks14 on 2007-07-15
It's official, it's impossible to boot Windows from a Logical Partition :)
Be more careful the enxt time you set up your partitions :(

---

