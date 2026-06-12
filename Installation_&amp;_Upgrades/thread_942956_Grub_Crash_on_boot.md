---
title: "Grub Crash on boot"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by Anoth on 2008-10-09
Hi,

I had a Vista Business SP1 x64 and installed Ubuntu 8.04.1 , I then lost the ability to access Vista, but recovered it with the startup repair from Vista.

After this all seemed to be OK, but then, when I restart from Vista Grub crashes in the next boot, it just says "Loading Grub" and nothing more. However, turning the pc off and back on solves the think, but everytime I do a restar from Vista, the same thing happens.

I would like to know if anyone has encoutered this before or knows a solution or how to tackle the problem.

Thanks

---

### Post by Anoth on 2008-10-13
Well, I didn't find the solution, but if someone does run into the same problem I solved it by going into ubuntu and seting up grub locally to ubuntu(out of mbr I think), then I went into windows and with easybcd I configured an Ubuntu entry for the vista bootloader and then through easybcd again I reintalled the vista bootloader in the mbr.

And that was all for me.

---

