---
title: "Ubuntu 12.10 (64Bit) and Windows 7 (64Bit)"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by jbeiter on 2013-01-11
currently I'm running windows7 64 and ubuntu 10.10 32 with mixed partitions between 2 drives.

I have never been able to complete a windows update. It always fails with mickysoft's typical unhelpful fail messages.

At one point I tried to track the problem down and ran across something that claimed windows update can't deal with grub on the MBR and to fix it you have to remove grub, redo the mbr with windows, etc...

I don't know if it was true and never tried it, but now I am about to reformat the windows and redo the partitions a bit.

Can anyone confirm if this is infact a problem? I know there are dozens of windows and ubuntu how-tos.. but none that I read seem to confirm what I want to do.. just load windows on one disk, linux on the other and have grub2 boot. Does windows *have* to be disk 0? If so, is it going to be pissy with grub on the mbr?

---

### Post by weryl on 2013-01-11
I remember reading when I did the same setup that there were a few necessary step which weren't required for winxp but are now required for win7... Sorry if this isn't very helpful but I would research complete howtos and make sure you followed this logic. If I remember correctly you had to install Ubuntu, then install Win7, then reinstall/repair Ubuntu to get everything working.

Also would you consider running win7 as a virtual machine instead of a seperate partition? I installed a Win7 VM inside ubuntu because I grew tired of rebooting to play games and switch back to Ubuntu. I'd recommend testing this setup first, as it won't affect your existing win7 partition, and see if it suits you.

---

### Post by jbeiter on 2013-01-11
thanks for the heads up Mike.. I'll try to dig deeper if nobody else chimes in with some helpful intel.

I'd love to just do virtualbox but I doubt the 3d performance is there yet. I've heard rumors that virtual box supports GL now but I haven't tried it.

I'd be pretty content if skyrim and a few valve games worked well under it.

---

### Post by darkod on 2013-01-11
I have a dual boot of win7 64bit with 12.04 64bit (earlier with 11.10 64bit) and it never said I need to remove grub2 to do the win7 updates.

I wouldn't say this is your problem with the updates, but who knows. I would definitely not use any type of windows or third party security programs that try to protect the MBR, that might act weird when it sees grub there. And they are no real protection anyway.

I even turn Windows Defender off right away, permanently.

---

