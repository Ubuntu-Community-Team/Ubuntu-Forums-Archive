---
title: "triboot"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by Vrekk on 2008-03-28
Hey, i have a friend wants a new computer, and i am the one making it for him.  Well, he wants to triboot between ubuntu 7.10, windows xp media center, and os x 10.  I know how to make a dual boot between windows and ubuntu, but not a triboot, can anyone hlep me?

---

### Post by el_ricardo on 2008-03-28
hmmm, I'm assuming you're using the hackintosh OSX cd? If i were you I'd do this with 2 drives. I'd partition the first drive into a windows partition, and an ubuntu one, and install windows to it first. Then I'd turn the computer off, remove the drive you just installed windows to, insert your OSX drive and install OSX to it. Once that's done I'd put the windows/ubuntu drive back in, so you've got both in now, and boot into the ubuntu installatoin disk. Install ubuntu to the ubuntu partition you made earlier, the ubuntu installer should see both OS's and set up GRUB accordingly, and if all has gone to plan you should have a triple boot system.

please bare in mind that i've never tried this myself, and i'm not sure how hackintosh's OSx86 installer handles bootloaders, this is why i said to install it while the other drive wasn't present. Also, if you haven't got the hardware yet, check it's supported by OSX before you buy it!

hope this helps, good luck!

---

### Post by Vrekk on 2008-03-28
Ok thanks, that should help alot.

---

