---
title: "new gutsy installation doesn't boot (or takes a LONG time)"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by bluepowder7 on 2007-11-02
hi guys!
i just did a sparkly-fresh install of 7.10 onto a JFS partition, set up wireless card, did the updates, and went to reboot.  up until that point, everything worked really well.  just before doing the reboot, i changed the display driver from a "intel experimental" or something like that to the intel i810 (for my 943GML chipset)


the first portion of the booting sequence shows the typical ubuntu graphic, but then it reverts to the following (actually, it flashes these lines 3 or 4 times before displaying them for good)


* Starting NTP server ntpd                                               [OK]
* Starting anac(h)ronistic cron anacron                                               [OK]
* Starting deferred execution scheduler atd                                               [OK]
* Starting periodic command scheduler crond                                               [OK]
* Checking battery state...                                               [OK]
* Running local boot scripts (/etc/rc.local)                                               [OK]


after some time, the screen goes blank, and.........  still nothing.  i'm watching it in case it DOES eventually boot.  hmm, if i press Enter, it brings those lines back.

still nothing.

i can actually type stuff!  i can write hello or bite me and it'll display it under those few lines...

ideas on what went wrong?  how to fix it?

---

### Post by bluepowder7 on 2007-11-02
small update?  ok, if i press Alt+F2, it gives me a terminal-style login screen.  so, i can log in with my user name and password, but it keeps me in a plain text scheme, like DOS back in the mid-80's.

so.....  what went sour?  how do i actually boot into GNOME?

---

### Post by bluepowder7 on 2007-11-02
bump?   anyone?

---

### Post by java_java_and_more_java on 2007-11-02
I get exactly the same problem but when trying to fresh install Gutsy on my laptop (i.e. before it boots into the LIVE CD mode). I think it has something to do with the graphics driver as I also get a window asking me to select the right graphics driver. 

I could however use Feisty fine on my laptop so its something new to Gutsy.

---

### Post by pmgeahan on 2007-11-02
I've had the same issue on *two* machines now, both with the Gutsy server install.  One was a VMware machine in Vmware Server on another Gutsy box.  The second was a Dell Optiplex desktop.

---

### Post by bluepowder7 on 2007-11-02
this is (was!) a brand new fresh install of Gutsy on a gateway laptop.  standard desktop edition, downloaded yesterday from the ubuntu site itself (amazingly, the iso image came across via firefox without having to resort to a torrent).

thankfully, i still have this WinXP machine to hunt for solutions (however strange and ironic that sounds)

---

