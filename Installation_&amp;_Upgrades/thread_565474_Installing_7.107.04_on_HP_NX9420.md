---
title: "Installing 7.10/7.04 on HP NX9420"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by koytetsu on 2007-10-02
I had 6.10 working very well on my HP nx9420 laptop some time ago.  I remember it taking a lot of work to get the resolution (1680x1050) to work properly on my ATI X1600 but eventually I did.  I've tried installing both 7.04 and 7.10 beta with not much luck and was wondering if anyone else has tried with this card and had similar problems.

7.10 -  System seems to install fine.  But I can't get it to take anything higher than 1280x1024, and it won't recognize the second monitor.  I've tried the old howto for installing fglrx and it seems to install fine, also I enable the restricted ATI driver but nothing seems to do the trick.

7.04 -  I get xorg failure right after booting from the DVD, after choosing to "Start or Install Ubuntu" so I haven't had a chance to even install.

Another question for anyone with a laptop and dual monitors.  My laptop is on a docking station and remains closed while the signal goes to a pair of dual LCDs (one VGA one DVI).  With ubuntu, if i boot the laptop off of the station with just its own single screen, will this cause issues with xorg or is it smart enough to detect when there is dual monitors present and when not.

Thanks for any light anyone can shed.

---

### Post by depele on 2007-10-02
> **koytetsu said:**
> I had 6.10 working very well on my HP nx9420 laptop some time ago.  I remember it taking a lot of work to get the resolution (1680x1050) to work properly on my ATI X1600 but eventually I did.  I've tried installing both 7.04 and 7.10 beta with not much luck and was wondering if anyone else has tried with this card and had similar problems.

7.10 -  System seems to install fine.  But I can't get it to take anything higher than 1280x1024, and it won't recognize the second monitor.  I've tried the old howto for installing fglrx and it seems to install fine, also I enable the restricted ATI driver but nothing seems to do the trick.

7.04 -  I get xorg failure right after booting from the DVD, after choosing to "Start or Install Ubuntu" so I haven't had a chance to even install.

Another question for anyone with a laptop and dual monitors.  My laptop is on a docking station and remains closed while the signal goes to a pair of dual LCDs (one VGA one DVI).  With ubuntu, if i boot the laptop off of the station with just its own single screen, will this cause issues with xorg or is it smart enough to detect when there is dual monitors present and when not.

Thanks for any light anyone can shed.

Here's easy instruction how to install Feisty with new X-series Ati cards: [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

