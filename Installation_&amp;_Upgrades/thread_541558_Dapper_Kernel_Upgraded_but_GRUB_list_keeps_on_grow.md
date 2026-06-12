---
title: "Dapper Kernel Upgraded but GRUB list keeps on growing"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by coolcar on 2007-09-02
Hi There,

This is a query related to GRUB entries. I am on Dapper Drake and have a dual boot set up for Windows XP. Recently Synaptic proposed a kernel upgrade. After the upgrading to the kernel 2.6.15-29 GRUB was correctly updated. I am not sure if I need to have the previous entries of the kernel 2.6.15-28 and 2.6.15-23 along with their recovery modes in the list. 

So the boot list has 3 Linux kernels with recovery entries for each, Memtest86+ and the windows entry. 

I was wondering if I could just get rid of the older kernels entries from GRUB and also from the disk ?

Thanks !

---

### Post by tgalati4 on 2007-09-03
Grub will keep adding kernels until it reaches its limit.  That's typically 7 as specified in menu.lst.  You can change it.  The backup kernels are helpful when something breaks so it's good to keep a few around.  

If you don't want to see them, you can put a # in front of kernel entries in menu.lst.  It's a good idea to keep them because you never know when you need them.

If you are running low on hard disk space then you can carefully delete those old kernels to free up some room.

---

### Post by logos34 on 2007-09-03
> If you don't want to see them, you can put a # in front of kernel entries in menu.lst.  It's a good idea to keep them because you never know when you need them.


Either that or edit the relevant option to keep, say, only the second most recent:

> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=2
# howmany=2

---

### Post by coolcar on 2007-09-03
Hi ! 

Thanks for the tips of how to control the growing list of Kernels in GRUB.:KS

Actually this is a new bee forum question. I am new to Linux / Unix so can you give me some tips on how kernels are stored and how to remove old kernels from disk:confused:. 

Well not that I am running that low on disk. One thing I have learned fast..Linux OS is lightweight in size but heavyweight in performance and stability :)

Cheers,

---

