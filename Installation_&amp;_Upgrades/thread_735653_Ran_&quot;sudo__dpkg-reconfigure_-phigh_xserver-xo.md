---
title: "Ran &quot;sudo  dpkg-reconfigure -phigh xserver-xorg&quot; and now black screen on reboot"
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by Droce on 2008-03-25
I looked at the other posts and couldn't find one that offered anything besides what I've tried. I have ubuntu running in 1024/768 resolution, but the problem is I have a widescreen monitor and it looks weird. I created a back up of xorg.conf then tried to change the resolution, but it just ended up looking even weirder, like low resolution mixed with a truncated picture. 

After that I tried to restart to see if it cleared up the problem, but I just get a black screen on start up, no prompts no HD use, and I can't get into any of the other selections (like ctrlshiftf1). I went to the recovery in grub and put in "sudo  dpkg-reconfigure -phigh xserver-xorg" but it only lets me select the resolution, and it doesn't fix the problem. 

I can still access the terminal through recovery with no problems, but can't log into ubuntu proper. Does anyone have any ideas, or a post that I missed entirely with the solution?

---

### Post by steveneddy on 2008-03-25
PC specs?

Video card?

Correct driver installed?

Monitor type and model?

thank you

---

### Post by Droce on 2008-03-25
Centrino 1.67 dual core, t5450
2 gigs of ram, 200gig HD (25 partitioned for Ubuntu, 1 gig swap)

Ati mobility Radeon HD 2400, I didn't install any drivers for it, the default driver worked when I started ubuntu. 

It's a laptop, toshiba a200-st2, device manager just says "generic PnP Monitor"

---

### Post by zvacet on 2008-03-26
[Here](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

