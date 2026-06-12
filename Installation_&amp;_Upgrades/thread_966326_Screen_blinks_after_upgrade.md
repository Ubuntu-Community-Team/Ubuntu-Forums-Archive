---
title: "Screen blinks after upgrade"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by kattandpeist on 2008-11-01
Older versions worked great but i upgraded to 8.10 and the screen of my vaio TX1HP blinks as every 10 secs.When i go to preferences of the system in kde4 and it appears a freq of 59.8Hz, then i edit xorg.conf and there are other intervals:

Section "Monitor" 
Identifier " Generic monitor " 
Option "DPMS" 
HorizSync 28-64 
VertRefresh 43-60 

I don't know what to change because i can't find the frequency in the manual, maybe shall i put a live cd?

P.d: The laptop has an integrated graphics from intel and i think is slower with kde4 effects, how do i deactivate it? Thanks for your time.

---

### Post by sulhi on 2008-11-02
I have the same problem but i fixed it by using a solution that i found. Maybe it can work for you too.

Kubuntu Intrepid Monitor Blinking
22 10 2008

   1. Open up System Settings
   2. Go to the Advanced tab
   3. Select Service Manager
   4. Select Detecting RANDR (monitor) changes and stop the service
   5. Uncheck the box next to the previous step in order to prevent this service from starting up at login
   6. Apply everything and close out

---

### Post by kattandpeist on 2008-11-04
Thank you very much! It works.

---

