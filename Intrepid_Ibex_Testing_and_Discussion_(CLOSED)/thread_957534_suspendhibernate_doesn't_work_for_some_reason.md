---
title: "suspend/hibernate doesn't work for some reason"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by toastytoast on 2008-10-24
I recently reformatted my Sony Vaio VGN-S480 laptop and installed 8.1 ibex it installed and updated fine but i can not suspend or hibernate my laptop i have tried to figure out why but i can not any help would be appreciated

---

### Post by toastytoast on 2008-10-27
well since no one else has had this problem I'm going to assume my cd was damaged or something and i guess I'll reformat w/ 8.04. Then just a distro upgrade its gotten to the point where my laptop won't shut down it'll go to the splash screen and will start to shut down but then once the "bar" empties it will just hang there and i have to do a hard power off w/ the power button 

oh well I'll just do a reformat and maybe just stick w/ 8.04

---

### Post by gvigorus on 2008-10-30
Hey. You aren't alone with suspend/hibernate isssue. I've got the same deal and am trying to resolve it. Just reading through threads trying to get any useful info on this. I'm sure it can be resolved. So far in my experience with Linux, you can do anything, it'll just take some time to understand the issue and find a fix-it for it. So, don't give up:) Post if you find a fix for this. Thanks!

---

### Post by dabl on 2008-10-30
Suspend to RAM, using kpowersave, is working fine on my desktop box.  Are you talking about S2RAM, or your lid-close switch?

Did you make a swap partition that's a little larger than your memory?  Are you sure it is enabled?

---

### Post by scradock on 2008-10-30
I've been having issues with this for a long time. My HP Pavilion zv6000 laptop will hibernate (suspend to disk) but if I try to suspend to RAM it goes down OK but will not recover. The screen stays black after the lights flash and I am left with only the power-off option. So I don't even try.

I tried some work-arounds way back, in the Gutsy alpha/beta stage if I remember correctly - they involved using kpowersave (in a GNOME system!!!) but that all got swept away during upgrades, and I kept waiting for the problems to be fixed. I'm sure my problem is that the video driver doesn't play nice, but I've tried using fglrx and ati (OS) drivers, and neither will perform as expected.

There's probably a fix out there for my system; but it very likely isn't the same as the fix for yours - different drivers have different quirks.

Good luck with your search!

---

