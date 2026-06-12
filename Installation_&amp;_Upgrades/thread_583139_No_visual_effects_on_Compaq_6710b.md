---
title: "No visual effects on Compaq 6710b"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by azzid on 2007-10-20
Hi,

I just installed Ubuntu 7.10 on my Compaq 6710b (p/n GR680ET), everything worked fine.

As so many others I am really interested in all the interface bling that compiz fusion can provide, so one of the first things I tried was activating visual effects (system - preferences - appearance - visual effects) but that only rendered the following: "Desktop effects could not be enabled".

How do I go about locating what is wrong?

The machine is brand new, I have'nt really had time to get to know it yet, but I was able to find out that it has a "intel mobile GM965/GL960" graphics card.

Should that be compatible?

Gratefull for any help!

---

### Post by s_raghu20 on 2007-10-24
I have the same problem.. No compiz effects.

anbody has any clue ??

regards
raghav..

---

### Post by laminaatplaat on 2007-11-10
I was wondering if someone has managed to solve this problem... because i can buy this laptop:

Hp Compaq 6710b Core 2 Duo 1.83 ghz 120GB, 1 x 1024 MB DDR2 for €650 euro ($950)... But it would be nice if the effects work :)

---

### Post by charon79m on 2007-11-10
Yes, I have it working.

The odd solution is to install xserver-xgl.

apt-get install xserver-xgl

Once you have logged out and back in you should be able to use the desktop effects.

Now, the reason that this is odd, is that you should not need this extra layer with this Intel chipset.  I am unaware if anyone is working on fixing this.

Michael J. Knisely

---

### Post by gregorej on 2007-11-30
Confirmed, visual effects work very well on this machine (some problems with playing videos exist). You may need to set SKIP_CHECKS environment variable to YES to prevent compiz from checking for blacklisted GPUs (X3100 is on this list). If you fail to run visual effects from visual effects tab try running this from console:
SKIP_CHECKS=yes compiz --replace

---

### Post by micro_mx on 2008-03-05
perfect gregorej, that one worked fine for me :]

---

### Post by s_raghu20 on 2008-03-08
Haven't tried playing video yet, but the visual effects work for me too..

Thanks a lot for the tip. :)

---

