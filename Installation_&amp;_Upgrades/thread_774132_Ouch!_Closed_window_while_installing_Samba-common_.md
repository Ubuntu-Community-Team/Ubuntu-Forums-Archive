---
title: "Ouch! Closed window while installing Samba-common via Adept"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by DizMan on 2008-04-29
Yes, I'll admit it right away: I'm not that clever!

I'm used to windows, so when I couldn't get samba to work, the natural thing to do was to uninstall it - and install it again.

I uninstalled all samba items in Adept package manager without any problems.

I then rebooted and tried to install about 9 sambla related items in Adept. While installing a dialogue came up (from Samba Common, I believe) asking me if I wanted to keep my old samba.conf (I think it was) or to install a new file.

Then I chose the option of comparing the two files. But - I'm an idiot - then I closed the dialogue window by accident. Now I'm stuck. Adept is stuck, saying configuring Samba Common, and I can't get it to go either back or to keep on installing.

What to do? Thanks for any reply!

Greetings from diz!

---

### Post by dstew on 2008-04-29
I don't know much about Adept, but in general you might be able to kill the process using **killall adept** from the command line. Whether this will leave the system in some unstable condition, I don't know. Since it is a front-end for apt, it probably will be OK to kill it.

---

