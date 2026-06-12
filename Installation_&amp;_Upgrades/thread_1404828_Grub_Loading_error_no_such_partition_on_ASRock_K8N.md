---
title: "Grub Loading error no such partition on ASRock K8NF4G-SATA2 board wd 250g drive"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by kevana on 2010-02-11
This is driving me crazy. 

History:
- bought 2 x 2nd hand motherboards on ebay :- ASRock K8NF4G-SATA2 with AMD Sempron 64 2800+
- Board1 - installed ubuntu server 9.04 on 40g drive works great
- Board2 - installed ubuntu server 9.04 on wd250g drive recieved error after install using same options as Board1

GRUB Loading.
error no such partition
GRUB rescue>

performed 'ls' returned
(hd0) (hd0,1)

Tried to install 9.10 to see if fixed, Nope same error.
After search on google tried install 9.10 again but change partition to use 80g of disk.

Now have the following

GRUB Loading.
error no such partition
GRUB rescue>ls     *(I typed 'ls')*
(hd0) (hd0,1)
error: out of disk

NOTE this is not a dual boot drive is only used for UBUNTU SERVER with ssh and samba packages only installed

HELP!!!

PS

perfomed 'set'
returned
prefix=(hd0,5)/grub
root=hd0,5

---

