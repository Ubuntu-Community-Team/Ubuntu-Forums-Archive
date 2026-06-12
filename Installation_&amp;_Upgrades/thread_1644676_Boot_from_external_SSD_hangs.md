---
title: "Boot from external SSD hangs"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by ev06dre on 2010-12-13
Hi, I'm building a new desktop and thought I would get an SSD to use with my laptop in the mean time, then switch over when the new desktop is done. When switching the hard drives, found out my laptop was IDE (school boy error :oops:).

Got a card reader with SSD slot and eventually got it installed (clean install) etc. The applications open really quickly but the boot hangs.

BIOS and Grub load up as normal, then when the OS is selected the screen blacks out and it hangs for 120+ seconds. Then the cursor shows up, then splash (just about) and it's up and running in a flash, it's just the hang time that is dragging it down.

My HDD still has 9.10 installed and I was playing around with/without each HD plugged in trying to get it to load so I don't know if this is something to do with it??

I tried advice from another thread:

Used Grub on a LiveCD, 'grub> find /boot/grub/stage1' which gave (hd0,0) which I assumed was my HDD so I used 'root (hd0,0)' and 'setup (hd1,0)'but still the same thing.

fdisk on the LiveCD gives:

hda as my HDD and hdb as my SSD. Both have 3 partitions, boot, ext3, swap.

Thanks in advance,

Dre

---

