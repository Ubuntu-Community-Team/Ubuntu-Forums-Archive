---
title: "My ubuntu partition is full... need to increase the space..!!"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by shsaifee on 2011-07-21
Hi,

I have recently installed Ubuntu 10.10 on my Windows XP computer. I did not use WUBI. It was installed directly using the Ubuntu CD. Now I have run out of space in Ubuntu and need to add space to it from the Windows partition.

Please help me as I need to install some programs and it says disk full...!!!

Thanks
Saabir

---

### Post by ddastoor on 2011-07-21
Try downloading an ISO of the "parted magic" distro ([http://partedmagic.com/doku.php?id=programs]("http://partedmagic.com/doku.php?id=programs"))
or any other live unix modern distro like knoppix. Boot off it using the CD drive and then load the gparted partitioing program (there are others too, u can choose any)

I believe, u can then increase the size of ur partition from there.

Backup first
-------------
If you want to be extra careful, then first download another distro called clonezilla ([http://www.clonezilla.org/clonezilla-live/doc/]("http://www.clonezilla.org/clonezilla-live/doc/"))

and backup you partition on an external USB drive.

---

### Post by Bucky Ball on 2011-07-21
Just boot the Ubuntu install CD and choose 'Try Ubuntu'. Gparted is already there on that disk so you already have it right there (unsure how you missed that, ddastor ;)).

But it's not quite that easy. With Windows, defrag that partition several times. Power Defragmenter is more affective than the default windows one. You will get wrong disk usage details and possible data loss if you don't do this. DON'T create any Ubuntu partitions or do anything Ubuntu related there. Ub uses EXTx partitions and Windows wouldn't have a clue about 'em.

Shrink the Windows partition using Windows software, definitely ***NOT*** Gparted. 

Once you have the Win partition shrunk, reboot using the Ubuntu LiveCD, once at a desktop, System>Administration>Gparted (or partition editor) and expand the Ubuntu partition into the free space created by shrinking Windows. Done.

---

### Post by ddastoor on 2011-07-21
Bucky Ball, your right, yes.. but doesn't modern windows partiton software defrag while shrinking?

Also, are u suggesting that Gparted is not "smart" enough to (in one shot) increase an ubuntu partition and decrease a windows partion, given that they are side by side because gparted would "not know" hwto defrag/and reduce the windows partition?

In the same vein, is gparted THE most sophisticated partitioning program around or any other good PPA ones?

---

### Post by Bucky Ball on 2011-07-21
I'm suggesting that Gparted can totally screw a Windows partition during resize as has been my experience and that of many others. (Perhaps not yourself, though, if you've done it that way.) This can kill the MBR and data (but usually at least the MBR).

It is generally not advised to resize Win partitions with Gparted from a LiveCD (or any other way).

(PS: Defragging is not really a Linux thing, that is from Windows world and has to do with how data is stored by Win and NTFS and FAT; NOT the same as EXT, so no, Gparted would not defrag any partition you were resizing in a Windows way.)

---

