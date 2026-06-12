---
title: "(EE) VESA: Kernel Modesetting driver in use, refusing to load"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by mwang25 on 2010-05-30
Today, I upgraded from my Ubuntu 9.10 to 10.04 (Lucid Lynx)
The installation was pretty uneventful, but when I rebooted, I got this rather scary looking message:

Ubuntu is running in low-graphics mode
The following error was encountered. You may ned to update your configuration to solve this.

(EE) VESA: Kernel Modesetting driver in use, refusing to load
(EE) No devices detected

Long story short, I chose the "restart X" option and my display seems to be working fine.  Actually, works better in Lucid Lynx because it properly recognizes by Dell 2407WFP monitor as 1920x1200.

In 9.10, it thought my Dell 2407 was only able to do 1600x1200.  I tried briefly to fix it, can't remember what commands I used, but I was not successful.  I don't think I modified any settings, but maybe I did and that is why I get this "Kernel Modesetting driver in use" message. 

More details in my blog for anyone interested (mwang25.blogspot.com).  

Just thought I mention it in this forum in case anyone else encounters this issue.

---

### Post by davidmohammed on 2010-05-30
possible you still have an xorg.conf trying to load drivers.

look in /etc/X11

if you've got a xorg.conf file - rename it and reboot.

---

### Post by mwang25 on 2010-05-31
Hi David,

Yes, you are right.  I did have a xorg.conf file in /etc/X11.  After I moved it to xorg.conf.save and rebooted, the system boots up fine without that annoying message about "Kernel Modesetting driver in use".

Thanks!

Michael

---

### Post by manolomanolo on 2010-07-14
Ok, so how to discover which driver is in use when not using xorg.conf?

---

### Post by avidscavenger on 2010-07-20
And how to force vesa to be used (when X wants to use buggy intel drivers that cause system crash)?

---

### Post by Paloseco on 2010-07-22
I am experiencing the same issue with xubuntu 10.04 and gparted.

---

### Post by stlsaint on 2010-07-22
> **avidscavenger said:**
> And how to force vesa to be used (when X wants to use buggy intel drivers that cause system crash)?

He was not saying that you CANNOT use xorg, should you choose so you can, then set your own settings via it.

---

