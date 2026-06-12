---
title: "GRUB on floppy, formatted C, lost Ubuntu"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by JohnLauritsen on 2008-07-20
I recently upgraded to Hardy Heron.  My setup was a triple boot of sorts: Windows 98SE and Dr-DOS dual boot on the HD.  Then, using the GRUB on a floppy I would get into Ubuntu. All this worked fine.

Well, to use some necessary software it was necessary to upgrade to Windows XP.  I wanted a clean install, and naively thought that the GRUB floppy had all the necessary information to boot into Ubuntu.  So, I formatted the C: drive and installed Windows XP and DR-DOS.  Alas! -- now when I boot up from the floppy all I get is a grub> prompt.

I do have both the alternate install and the live CDs for Hardy Heron.

What should I do now to get back Ubuntu?  Any help would be most gratefully appreciated.

John

---

### Post by Shazaam on 2008-07-20
Does it boot straight to Windows without the floppy?
To start boot the Ubuntu live cd, open terminal and run this and post the output...
```
sudo fdisk -lu
```
(small L)
This will list your partitions so we can see whats there.

---

### Post by JohnLauritsen on 2008-07-20
From the command sudo fdisk -lu I got:

device        boot      [...]         ID            system

/dev/sda1       *                     6             FAT16
/dev/sda2                             f             W95 Ext'd (LBA)
/dev/sda3                             83            Linux   
/dev/sda5                             6             FAT16
/dev/sda6                             b             W95 FAT32
/dev/sda7                             b             W95 FAT32
/dev/sda8                             b             W95 FAT32
/dev/sda9                             82            Linux swap  /Solaris

On your question: When I boot up without the floppy I get a dual boot installed by DR-DOS: either Windows or DR-DOS.

John

---

