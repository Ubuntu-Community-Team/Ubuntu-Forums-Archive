---
title: "Gutsy RC no bootsy with ATI X1250 (IGP)"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by jabeez on 2007-10-17
Tried messing with the different video modes, booting into safe graphics mode, still end up with garbled screen and then dumped back to "running xxx scripts" and it never goes any further. Bummer, I installed Gutsy beta on my laptop (averatec 2370 with Nvidia graphics) and it is SWEET. Wireless (ralink) working outta the box, nvidia driver a snap to install.....Feisty installed and works on same build, so what happened???? Anyone with this chipset able to install?

---

### Post by radthad on 2007-10-17
I'm having the same problem with the ATI X1300 Pro.  I've just decided to wait until the actual release to see what happens.

---

### Post by jabeez on 2007-10-17
stoopid ATI, I was really hoping the "new" ATI drivers would be out soon when I built this computer, but I might have to just break down and buy a cheap Nvidia card.....

---

### Post by radthad on 2007-10-17
I'm not sure if its the drivers, or if it's the monitor.  My monitor will flash the refresh rate on the screen, and its 90-something.  My LCD only supports up to 75.:mad:

---

### Post by jabeez on 2007-10-17
definitely seems to be a refresh rate issue, but is there any way around it?

---

### Post by radthad on 2007-10-17
You can change the resolution and color depth from the installation menu on the CD before you load up the live environment.  However, none of them have worked for me :|

---

### Post by radthad on 2007-10-17
At this point, I give up.  I'm just going to wait until the final release tomorrow and hope that does better.  If not, I'll try to figure out the work around or find help.

---

### Post by jabeez on 2007-10-18
So anyone had any luck with the final version? I haven't downloaded it yet, but assumed the servers are swamped and I'll bet there isn't any difference between the RC. I've only tried Kubuntu, are you guys using Ubuntu with the same issues? Maybe I'll attempt the alt. cd download......

---

### Post by radthad on 2007-10-18
It seems to be going fairly slow.  I'm only pulling about 35-50 kb/sec :(

---

### Post by rad_sci_guy on 2007-10-18
I have the x1250 onboard graphics and did the gutsy upgrade yesterday.  Still unable to get proper refresh rate listed in the selection box and when I set 1680 x 1050 resolution I end up with a 60 hz refresh which causes intermittent flickering as well as multiple boot up errors where the screen settings are not accepted.  None of the ATI drivers would stick in the selection box for card drivers and the system would not keep the widescreen checkbox on for my syncmaster 205bw. On another note the compriz 3d deskop always gives an error message when I select the desktop effects.  

Gutsy has slowed my AMD X2 64 5000+ to a grinding halt when web browsing on Firefox and my CPU monitors are constantly showing 40-50% usage when I'm not even doing anything.

My linux install has been rendered pretty useless now so I'll have to use XP unit the video drivers are resolved.

On a side note   my HP 1020 laserjet while being recognized by ubuntu still won't print.  I had fix this in Fiesty, looks like I'll have to do the same fix.

On a positive note I was able to write onto a windows partition which really makes using ubuntu much better for me as I do have to work from a windows platform for some things.

I hope some updates are instore real soon, otherwise I'll be forced to go back to XP until things get better

---

### Post by radthad on 2007-10-18
are you using the RC or the final release?  If the final release proves to be like this, I might be switching to openSUSE or Ultimate Ubuntu a shot.  I've been tinkering with openSUSE and it seems to work quite nicely with my setup.  Even though I can't get 3D acceleration, I can at least get 1280x1024@75Hz, which is what my LCD is fully capable of.

---

### Post by jabeez on 2007-10-20
As an update, I managed to DL a Kubuntu 7.10 alt install CD and installed from that, picking my resolution and refresh (detected correctly) during install, and it installed fine. I then used the restricted drivers utility and installed the ATI driver and it's working great, even better than under Feisty and Envy. I really haven't used it much, been dealing with laptop wireless issues, but so far so good, not sure about regular Ubuntu, I plan on installing on a separate partition eventually.

---

