---
title: "Help me get rid of Vista"
date: 2007-11-27
forum: Installation &amp; Upgrades
---

### Post by eclipse13 on 2007-11-27
I need help.  Bought a Dell inspiron a while back and first thing I did when I pulled it out of the box is shrunk the vista partition and threw Fiesty on it.  I tried to get rid of Vista and go back to XP but couldn't figure out how to do it.  Decided I would just play with Vista for a while and see how I liked it.  Well basically Vista sucks **** I want to go back to XP without having to wipe everything and start over.  Trying to kill the Vista partion I discovered that gparted won't even recognize the partions on my drive just shows one big 250 gb drive.  Here is what fdisk shows

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x98000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       30075       30402     2620416    c  W95 FAT32 (LBA)
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3   *        1314        9079    62376795+   7  HPFS/NTFS
/dev/sda4            9080       30402   171270246+   f  W95 Ext'd (LBA)
Partition 4 does not end on cylinder boundary.
/dev/sda5           30075       30402     2620416   dd  Unknown
/dev/sda6   *        9080       29366   162955264+  83  Linux
/dev/sda7           29367       30074     5686978+  82  Linux swap / Solaris

Partition table entries are not in disk order

Can anyone help me kill Vista and get my drive cleaned up so that I can load XP.  I would love to reclaim the whole drive for Ubuntu but alas there are a few apps I still need windows for.  It doesn't get much use but when it does I'd like something that doesnt take 20 minutes to boot.

---

### Post by Jose Catre-Vandis on 2007-11-27
Dells have a couple of hidden partitions on board as well. Looks like Vista is on sda3?

Suggest you use a live cd and operate gparted from there, or download the excellent Parted Magic iso and use that.
[http://partedmagic.com/downloads.html](http://partedmagic.com/downloads.html)

---

### Post by eclipse13 on 2007-11-27
I'll try the boot cd you posted unfortunatly the ubuntu boot cd won't work.  If I remember right there is something it doesn't like with the video card in these things or something.  I know it was a pain in the butt to get installed originally.  Been a while though and don't remember the work around.

---

### Post by Pumalite on 2007-11-27
You have a Partition Table problem. Use TestDisk to fix it: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

