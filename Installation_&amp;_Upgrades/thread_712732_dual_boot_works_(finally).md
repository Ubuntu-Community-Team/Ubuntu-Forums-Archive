---
title: "dual boot works (finally)"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by soluby on 2008-03-02
on my notebook I have xp, ubuntu7.10, solaris 10

The first 2 went easily, I did xp first (hd0,0) a primary partition (actually 2 windows, the other is (hd0, 1) also primary. Then I put ubuntu, first the ext3 root in (hd0,3) a logical partition followed by swap (hd0,4) also logical - the extended partition (hd0,2) which is primary, maps across both of the logical partitions. This all went smoothly, ubuntu found the windows partitions and put the in the grub menu.

Solaris loaded up ok in (hd0,5) but the grub menu only picked up the windows partitions and not the linux - it was fairly clear that solaris simply wrote their grub on top of the linux grub, the result, no linux. I put the lines in the solaris grub to point to first hd0,3, the ext3 root and then hd0,2 the extended primary root - no go.

After all the normal nonsense, reading web pages, trying, re-trying - on loading ubuntu 7.10 there is an "Advanced" button after you specify the partitioning, in there it specifies the grub partition as (hd0), edit this to point to the extended primary partition (hd0,2) ... of course your numbers will be different ... this puts the linux grub in a safe place so solaris won't overwrite it. When I installed Solaris (solaris doesn't have an option to place the grub - it goes in (hd0,0) no matter what), it still didn't find linux but when I edited the /boot/grub/menu.lst to add the "other OS" as ubuntu 7.10  (hd0,2) everything worked. The startup grub is the solaris list which now has ubuntu 7.10 on it and when I select it, the linux grub menu pops up.

---

### Post by zxscooby on 2008-03-02
congratz! :KS

---

### Post by NightwishFan on 2008-03-02
Enjoy. :popcorn:

---

