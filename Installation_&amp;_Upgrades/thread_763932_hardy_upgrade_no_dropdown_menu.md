---
title: "hardy upgrade no dropdown menu"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by gupi-gupi on 2008-04-23
Hi I just upgraded to hardy (a bit too early I guess) and on reboot gdm does not show up menu dropdown, please help:(

just noticed that this happen on screen 0 but in the second monitor it works... I have separete X sessions in the two monitors, any idea?

it must be an xorg bug or something of that kind

---

### Post by gupi-gupi on 2008-04-24
up :)

I tried almost anything I could think of, I replaced the xorg.conf with an old one, where the second screen was not added yet, but still when compiz start I get no menu dropdown in any application, please suggest me something, I'm open to experiment anything.

---

### Post by Peter09 on 2008-04-24
What video card have you got?

PC

---

### Post by gupi-gupi on 2008-04-24
nvidia GeForce 6600
32 bit architecture
hardy, just upgraded (that made the trouble)

---

### Post by Peter09 on 2008-04-24
In System->Administration

do you have the nvidia setting application?

PC

---

### Post by gupi-gupi on 2008-04-24
yes, and I tried many different settings in there, (I had the dual monitor set up with separate X session and couriously I noticed that in the second monitor everything works, compiz emerald and the dropdown menu just work, but on screen 0 there is no way, I also tried some script to solve a similar problem gutsy hed (slow menu visualization) but without luck.
Let me know if you have some suggestion :)

---

### Post by wfroelich on 2008-04-24
I had a similar problem after upgrading from 7.10 to Hardy on my laptop last week.  My problem isn't that I didn't get the drop downs but that they appeared and disappeared immediately.  It has something to do with the mouse settings in the xorg.conf.

I commented out the section for the Synaptics Touchpad (I'm on a laptop) and then the left click started working as expected but of course I can no longer tweak my settings.  

Unfortunately I haven't had much free time lately to experiment more to see if it's been fixed or narrow it down more.  

Just thought it might be the same problem.

Good Luck!

---

### Post by ad_267 on 2008-04-24
If you have an nVidia card then try using nVidia's TwinView rather than xinerama with separate x screens. I've found that TwinView works a lot better than using separate x screens.

---

### Post by gupi-gupi on 2008-04-25
thanks for reply, I did quite a mess, I just fresh reinstalled hardy since I could not find a solution, and after a long surch I found out that the old configuration of compiz was messing with the x session /home/.config/compiz (Ihad menu desappearing immediatly like wfroelih) now it's all working with the two separate session (had to add a script for sturtup compiz). Now, I just have to reinstall everything. (always a mess the dist upgrade)
thanks anyway:)

---

