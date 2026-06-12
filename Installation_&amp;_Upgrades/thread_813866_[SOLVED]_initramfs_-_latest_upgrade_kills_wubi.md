---
title: "[SOLVED] initramfs - latest upgrade kills wubi"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by ubunutgoz on 2008-05-31
Have been using Hardy under wubi without any problem since the day it was launched. After yesterday's updates, however, I couldn 't get passed the **initramfs** prompt.  I figured I'd done something wrong, so de- and re- installed.  

All was fine, so I hit the update button and hey, am back to no boot and the initramfs prompt.

This in NOT hardware (its been working perfectly for 6 weeks)
This is NOT Windows (I was able to re-install)

So, does anyone have any ideas. Is it a BUG, in which case surely many users are being hit?

Please help.  Am not a nooby, but also not a poweruser. Am not afraid of command line, but do want to know what gives?

Thanks in advance

---

### Post by paulphillips on 2008-05-31
I don't suppose there's any way of working out what the updates were that caused the breakage?

---

### Post by ubunutgoz on 2008-05-31
Thanks or fast reply!

All i did was hit the update notification icon.

Are you suggesting re-install and then do the updates 1 at a time?

Alan

---

### Post by ubunutgoz on 2008-05-31
OK, I did some more digging.  Head over to this post 812072 ([click here]("http://locoteam.ubuntuforums.org/showthread.php?t=812072&highlight=initramfs&page=2")) and it confirms...

(1) Sure, there's a bug with the latest kernel
(2) Hitting 'esc' during boot and using the -.16 kernel will boot your system
(3) The issue is logged, accepted and a fix will be included in a later update

Cheers
Alan

---

