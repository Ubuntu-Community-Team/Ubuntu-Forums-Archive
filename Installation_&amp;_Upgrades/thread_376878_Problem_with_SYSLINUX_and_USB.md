---
title: "Problem with SYSLINUX and USB"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by papercuts on 2007-03-05
I have read on this site the guide to installing ubuntu from a USB stick (which is by the way not at all clear). Anyhow in the end I got syslinux from Synaptic and ran the commands on the console. My USB stick is 1GB and formatted with FAT16 (I checked) and was recognized as /dev/sda.  I even reformatted it with FAT16. 

But the problem is syslinux says that the drive is not FAT16!!  It is!  

How can I go on from here? Any ideas will be greatly appreciated, otherwise I have to buy a CD-ROM Drive for nothing. 

Thanks everyone.

Caner

---

### Post by Jonie on 2007-03-05
Maybe your stick is partitioned, i.e. /dev/sda refers to the stick as whole and the filesystem is /dev/sda1. As some sticks are and some are not, this may be confusing a bit.

---

### Post by papercuts on 2007-03-06
Hmm there seems to be both when I look at it. So should I try it with sda1?  In the beginning I did that but there was another problem there, it said that this was a directory, so not valid media.

---

### Post by Duggeek on 2007-03-15
> /dev/sda refers to the stick as whole and the filesystem is /dev/sda1
That would ordinarily be true with an internal HD, but USB Flash is kinda different. In just about every case, you want to stick with the normal **pmount** behavior that Ubuntu handles automatically through **udev**. It's a good way to be assured that the drive is still working (instead of banging your head against it) and it makes things easier in the long run.

You can "partition" USB drives, to be sure, but it's not very practical or effective. Did SysLinux give you many options on formatting the drive? I hate to say that you wasted time with Synaptic, but Ubuntu is already designed for lots of cross-compatibility with Win32 environments. (as much as MSFT allows, to be sure) Besides, you'd end-up with a drive that doesn't work with other machines or platforms. (...and what do we normally use a USB stick for?)

The best bet is to use the Unix command to create the filesystem on the USB stick. It's reliable, it gives consistent results, and it's indifferent to the "temperament" of your system at the time. The  program I like to use is **mkdosfs**.

[COLOR="DarkRed"]**REMEMBER:**[/COLOR] Umount (**pumount**) the drive first! You can always use **blkid** to find the device while it's connected.

Here's the syntax:
```
[SIZE="4"]your@xterm.con$ **mkdosfs -F 16 -I -v /dev/sd[COLOR="SeaGreen"]x[/COLOR]** [/SIZE]
```

[SIZE="3"]Explained: [/SIZE]
The **mkdosfs** program was originally designed for simple FAT16 formats on hard drive partitions. (e.g., /hdb1) 

The team has since updated it with FAT32 compatibility, though there's some ambiguity on certain technical details. (that is, the FAT32 from Win98 isn't *quite* the same as the FAT32 in WinXP)

In the command I've given; 
[LIST]
[*]**[COLOR="SeaGreen"]-F 16[/COLOR]** forces FAT16 format, rather than allowing it to default to FAT32 (seems to do that with >512MB drives)
[*]the **[COLOR="SeaGreen"]-I[/COLOR]** is another forced option, only this one tells **mkdosfs** to use the full capacity as one volume (basically, as one large partition, but only the *starting* sector will be marked in the superblock)
[*]the **[COLOR="SeaGreen"]-v[/COLOR]** is just so it gives some informative feedback while the formatting is going on and of course...
[*]the **[COLOR="SeaGreen"]/dev/sdx[/COLOR]** refers to your device (just replace "x" with the appropriate letter)
[/LIST]

Once you've formatted the drive, you can test it out right away with a **pmount** command:```
[SIZE="4"]your@xterm.con$ **pmount /dev/sdx**[/SIZE]
```
Beware! The default codepage for Ubuntu is UTF-8, and doesn't match Windows FAT16 very well. 

I wish they'd address it as a bug, but I guess it will have to be a "wishlist" item for now; if you want to be sure that the filesystem/files can be read by Windows, use a special **pmount** command instead:
```
[SIZE="4"]your@xterm.con$ **pmount -c iso8859-1 /dev/sdx**[/SIZE]
```This will set the mounted FAT16 volume to use Windows "rules" for filenames, a'la Win95-OSR2 or Win98. Take notice that copying some files will be *refused* by the drive so long as their filenames contain certain "illegal" characters. In a nutshell, the only "legal" characters for FAT16 are *A thru Z*, *0 thru 9*, **~**, and **!**.

What I'm looking for is a way to set this as the default manner for mounting, or to give special assignment to certain devices to be mounted one way or another. (not just the Ubuntu defaults every time)

Anyone care to pitch in on this?

---

### Post by sdman on 2007-03-20
opss wrong window

---

