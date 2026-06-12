---
title: "problems with a formerly working dual boot"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by kfdownard on 2010-10-02
I have recently set up my computer to dual boot between Ubuntu and Vista, everything has worked fine for a few months, but just the other day I attempted to boot my vista os and
 got this message. 
 
Warning: unrecognized partition table for drive 80 please rebuild it using a microsoft-compatible FDISK tool(err23).  Current C/H/S=16383/240/63

If I allow it to sit long enough after this error it will eventually kick me out to the GRUB command prompt.  This is especially confusing since I typically only use ubuntu and only boot to VISTA when I need to use Adobe.


Thanks for any help!!

---

### Post by oldfred on 2010-10-03
Heads are normally 255 not 240 with LBA.

I would try testdisk.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

