---
title: "&quot;Uncompression error&quot; after update, RAM modules are fine -- 9.10/Karmic"
date: 2010-11-15
forum: Installation &amp; Upgrades
---

### Post by ketarax on 2010-11-15
So today I noticed update-manager was requesting a reboot (not sure when the update actually occured), and I gave it a go.  On reboot, I get

Uncompression error
System halted

This happens with kernel version 2.6.32.  My RAMs are fine -- no, they really are, I'm writing this on the same machine running the previous kernel (2.6.31).  Also I did try taking all the modules out one by one, rebooting with each setup, and after all four modules (2x1G + 2x0.5G) were out, I even had some spare 1GB modules to try -- same difference, Uncompression error.

I installed a second LCD just before the reboot, and it was working fine.  No, I don't think it's the cause either, it wasn't connected during the tests.  Opteron dual core on an Asus A8V board, radeon HD 2600 PRO AGP for what it's worth.

I'm pretty sure this is some sort of an issue with the update/kernel, though I admit that I don't know if a new kernel came with the previous update (NOR am I even 100% sure there couldn't be a couple of updates accumulated since the previous reboot).

Didn't run memory tests yet, though I will.  I'll be happy to use the older kernel if no other problems appear.  Just reporting this in case someone else is having the same issue, and knows it's not the RAM modules this time.

---

