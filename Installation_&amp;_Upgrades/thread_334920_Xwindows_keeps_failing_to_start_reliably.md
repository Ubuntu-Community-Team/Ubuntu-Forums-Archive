---
title: "Xwindows keeps failing to start reliably"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by sdowney717 on 2007-01-09
So what can I say, it runs XP just fine. I have a builtin video 
My computer is 2ghz HP EVO with intel brookdale video chip.

And I wish it would work, but sometimes Xwindows will work, and sometimes all I get is a blank screen. But the Live CD always comes up on Xwindows. 
Now why is that?

---

### Post by hal10000 on 2007-01-09
Need more info:
Post the output of the following command:
sudo lspci -v
upon next time when the xserver fails, post the output of **cat /var/log/Xorg.0.log**

---

