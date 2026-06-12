---
title: "Freezed, now locked up, can't start WinXP or Ubuntu"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by KTNAJR on 2010-08-22
Hi., everyone.

My first post here, though I have read posts here before. Sorry for anything.

I had Windows XP installed on my PC, but I decided to try Ubuntu.
I downloaded the .ISO, burned the Live CD and installed Ubuntu 10.04. I configured the grub2 for dual boot with WinXP, and it was working fine until this morning (WinXP included). This morning, Ubuntu freezed completely out of nowhere.

I had to restart the PC, and when it started again, the boot screen looked strange, with different colors ... and when I started Ubuntu, I got several "segmentation fault" warnings (among many other stuff), and the system didn't even start.

Now, when I turn on the computer, it goes well up to the point where the boot screen would show up, and then it restarts.

I tried using the LiveCD to reinstall Ubuntu, but I can only go to that first screen (Try Ubuntu without installing, Install Ubuntu, Check disc for defects, etc). If I choose any option, it gives me many warnings, always ending with things like "? unknown_bootoption+0x0/0x19e" and "i386_start_kernel+0xaa/0xb1".

I could format the computer, but here's the problem, I don't have the WinXP installation CD (and I can't get any OS started). 

So, do you guys have any word of help?

Thank you.

---

### Post by zvacet on 2010-08-23
Download Gparted live CD from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) and with it delete Ubuntu partitions.Leave it as unallocated space.After that try to install Ubunntu again.Grun should recognize both OS by default,so I don´t think you have to configure grub.

---

### Post by Ad@m on 2010-08-23
> **KTNAJR said:**
> 

I tried using the LiveCD to reinstall Ubuntu, but I can only go to that first screen (Try Ubuntu without installing, Install Ubuntu, Check disc for defects, etc). If I choose any option, it gives me many warnings, always ending with things like "? unknown_bootoption+0x0/0x19e" and "i386_start_kernel+0xaa/0xb1".



Can you run the memtest option?

Let it run for 1 pass or if your screen turns red, stop and post.

---

