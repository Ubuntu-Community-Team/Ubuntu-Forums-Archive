---
title: "Just finished installing Karmic on my Sony Vaio P11Z (P series)"
date: 2009-08-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by excogitation on 2009-08-17
Karmic runs quite nicely - just that there's no GMA 500/US15 driver so it runs on Vesa ](*,) (detecting the native resolution though).

The keyboard keys for setting the LCD brightness don't work and the external Monitor doesn't get detected (might be related).

Is anybody working on getting the Poulsbo (psb) drivers to work with Karmic? (would be nice for Acer Aspire One 751, MSI Wind U115, ASUS Eee PC 1101HA, Dell Inspiron Mini 10/12, Sony Vaio P series, ... -users)


WWAN and GPS aren't working (or I don't know how to use it).
WLAN does work sketchy.

Clicking with the pointing stick doesn't work by default (the same as with touchpads).

Apart from these issues everything works fine.

---

### Post by zekopeko on 2009-08-17
look here for GMA500.
i think that the solution is on page 2

[http://ubuntuforums.org/showthread.php?t=1235843&highlight=psb+500](http://ubuntuforums.org/showthread.php?t=1235843&highlight=psb+500)

---

### Post by excogitation on 2009-08-27
> **zekopeko said:**
> look here for GMA500.
i think that the solution is on page 2

[http://ubuntuforums.org/showthread.php?t=1235843&highlight=psb+500](http://ubuntuforums.org/showthread.php?t=1235843&highlight=psb+500)

Thanks, but afair that's not working for Karmic (yet?).
Also I managed to mess up my Karmic test installation trying to get it running.

So now I setup Jaunty for the time being.

From what I read the problems with the ath9k module are known for a long time ([#333730]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/333730")) - but in Jaunty using the backport modules seems to do the trick.

---

