---
title: "partitioning issue"
date: 2005-10-29
forum: Installation &amp; Upgrades
---

### Post by hollowhead on 2005-10-29
With breezy I can only create one primary partition or numerous logical ones.  If I create logical ones it screws up my 3 windows primary ones.  I have messed around for ages with the installer.  I wish to create a root and swap only.  If I create a primary drive then the breezy partioner says no more free space is available, although it is.  If I create a swap partition (as logical) first I cannot create a primary drive only another logical one.  Whats going on?  Although both breezy and msdos Fdisk see my windoze paritions as primary in reality two were set as extended by a friend of mine.  RH9 installed OK on this setup though.  The only way I can see through this is create root only then create a swapfile.  Prefer not to do this though.  Can anyone help?

---

### Post by paddyg on 2005-10-29
If you want to dual boot, why don't you use Windows Partition Magic to organise your disk before ubuntu installation?

Just create a root (extended) plus a swap (extended). If PM just uses ext2, ubuntu partion tool will change to ext3 then.

---

### Post by hollowhead on 2005-10-29
Thanks I don't think I have a recent enough copy but I will have a look.  Hollowhead

---

### Post by hollowhead on 2005-11-03
Cheers it worrked although even PM5 (which I had  free on a PC magazine cover disk) would not let me set it up as it wanted to. Had to create a primary with 2 logicals inside.  Ta.  Hollowhead.

---

