---
title: "HP 710C won't print after upgrade to Gutsy - Fix"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by penguinhugger on 2007-11-02
After an upgrade to Gutsy my HP 710C printer stopped working: CUPS was reporting (rather misteriously) that" /usr/lib/cups/filter/foomatic-rip failed".

I dived thorugh *a lot* of 710C-related threads, and eventually found out on [http://openprinting.org]("http://openprinting.org") that this behavior is caused by the new AppArmor security framework in Gutsy: simply open a terminal and type ```
sudo aa-complain cupsd
``` and your printer should be working again.

I *suspect* this could apply to more printers than just the 710C... Some feedback on that would be appreciated.

Hope it helps. Happy printing everyone :)

---

### Post by nilsglow on 2007-11-02
I had the same problem and first suspected there is a bug in ghostscript. I wouldn't have thought about AppArmor cause I have no experience with it, but your sugestion fixed the problem. do you know whether this problem is known at launchpad? should I file a bug report?

thanks a lot!

---

### Post by penguinhugger on 2007-11-03
> **nilsglow said:**
> I had the same problem and first suspected there is a bug in ghostscript. I wouldn't have thought about AppArmor cause I have no experience with it, but your sugestion fixed the problem. do you know whether this problem is known at launchpad? should I file a bug report?

thanks a lot!

I just checked launchpad and there is a bug report already about this issue ([https://bugs.launchpad.net/ubuntu/+bug/133982]("https://bugs.launchpad.net/ubuntu/+bug/133982")). The last post also mentions the same fix I came up with, which I guess it makes this post redundant. Oh well, at least it will benefit those who check the forums before launchpad (like me :lolflag::).

---

