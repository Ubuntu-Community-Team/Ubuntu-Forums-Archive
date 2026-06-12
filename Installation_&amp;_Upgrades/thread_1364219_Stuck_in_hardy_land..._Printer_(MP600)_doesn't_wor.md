---
title: "Stuck in hardy land... Printer (MP600) doesn't work under karmic."
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by saturnine fei on 2009-12-25
I took some advice from starcraft.man (thank you again) and now have hardy (my current installation) and karmic (my potential installation) running side by side.

Sadly, I'm having the same problem I had when I tried to upgrade to intrepid.  I can't get my printer to work (Canon MP600) and the fix that worked for hardy doesn't work for intrepid or karmic.

Does anyone know how to get this printer to work or am I stuck with using hardy? Not really an option, as I can't get the latest versions of applications or new applications.

I haven't even tried using bluetooth yet, that was a disaster under intrepid.

Cheers,
Saturnine

---

### Post by woodmaster on 2010-01-10
same problem here...I can't make my printer work "properly" in Karmic.  Using MP610 driver it prints B/W ok but color is not good at all.  I tried some suggested solutions.  I found a driver on Canon Japan site and downloaded it.  It was .rpm so I got alien and converted it to .deb.  Using GUI installer I supposedly successfully installed it, but it doesn't show as an option in the drivers selection menu.  Maybe there's something I'm missing, like updating the file that has the available drivers in it but IDK how to do that if it's possible.  Running Karmic with 2.6.32 kernel cause going to the newer kernel solved my random crashing issue.  Any suggestions for the printer out there?  This is really my last hurdle with my Ubuntu install.  After 1 1/2 months I've almost got it set up so my wife accepts it instead of Winblows.

---

### Post by Malta paul on 2010-01-10
My Canon printer did not work when I change from 9-04 to 9-10. libcupsys2 has been changed in Karmic to libcups2 which wouldn't work with my printer driver.

Try #11 post link at:
[http://ubuntuforums.org/showthread.php?t=948312&page=2](http://ubuntuforums.org/showthread.php?t=948312&page=2)
It may help you ;)

---

### Post by woodmaster on 2010-01-11
downloaded and installed but no help here...still doesn't show an MP600 driver even though it says I installed it out of gdebi package installer...I'm lost here:(

---

### Post by saturnine fei on 2010-07-01
So on another thread someone said they were using the driver for the MP500.  I just went into the printer properties and changed it to the MP 500 on a fresh install of lucid and it seems to be working so far (Minimal testing).  Scanner seems to work under the new simple scan program as well.  Perhaps this is fixed enough...  If not I'll update again.

---

### Post by Roboload on 2010-09-22
Thanks for useful tip, Saturnine! Had same problems with mp600. Installed mp500 drivers on amd64 Lucid, and it seems to be working atleast on document printing - all I needed for this day :)

---

