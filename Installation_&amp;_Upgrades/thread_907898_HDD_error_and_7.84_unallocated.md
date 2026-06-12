---
title: "HDD error and 7.84 unallocated?"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by Lateforgym on 2008-09-01
In attempting an install and it says I have a detected error on my primary HDD. I ran error checking through Windows and after booting to Ubuntus Gparted it still says the error is there. Do I have to manually type checkdisk /r command as Ubuntu says or is right clicking in windows to the check disk screen the same thing? 

Also, I did a search on "7.84 unallocated" on these forums and it didnt pull anything up. The odd thing is both my drives have 7.84 of unallocated space. What is this?

Thanks

---

### Post by xen-uno on 2008-09-02
On what partition? You want windows to check the partition on boot up ( which is mandatory with your boot partition aka c: ). Run chkdsk from a windows ...

Start>Run>cmd>chkdsk /r

... this will schedule a disk check on next boot into windows.

Having 8 MB of unallocated space is normal with windows. It has something to do with creating a dynamic partition later if wanted.

---

