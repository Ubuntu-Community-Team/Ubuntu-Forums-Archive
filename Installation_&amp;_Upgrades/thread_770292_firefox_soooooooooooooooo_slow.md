---
title: "firefox soooooooooooooooo slow"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by timbosity on 2008-04-27
Upgraded my Xubuntu laptop baby to hardy yesterday and have only really begun to explore the changes today...
Of note:
- I had about 2Gb free space on /root. I now have 600Mb; Surely it cant have taken up an entire Gb of my space? What did it forget to remove?

- Firefox 3 Beta 5 is about as slow as IE explorer on solvent fumes. Takes a full minute to even show up after launch (from terminal or through menus) and then, changing pages, clicking links etc, just takes it ages... Very unhappy with this I must say. To try and diagnose: when I start firefox there is no cpu peak which is something im pretty sure happened previously; I only have 256 ram so maybe therein lies the problem? Although never had an issue previously...When it does finally load up and run its only uses about 8%CPU behind xorg, and 20% memory which is much less than before (in gutsy it was always around 30%memory and top of the CPU list). Oh yes and the icon is gone from the quicklaunch panel... The
/usr/share/pixmaps/firefox.png does not appear to be there...

- Apart from that all looks well. Wifi seems to be more efficient, as does memory management. Allother apps are running a little more sweetly although maybe a little slower at the start. Still unsure about what the changes actually are apart form seeming a little bit more heavy under foot with navigation/loading programs... Is Xubuntu looking more and more like Ubuntu with Xfce thrown in on top?

Anyone have any ideas how I can get firefox running sweetly again?

---

### Post by timbosity on 2008-04-27
Ok, just to add another note here: using the mouse scroll wheel, although sometimes problematic previously, is now a big no no in terms of making firefox hang... not that I mind because im used to using arrows and page down-page up but it could be an issue with mousey folk :-D

---

### Post by timbosity on 2008-04-27
ok this is really starting to grind my gears...i cant do anything without my browser :(
does anyone have any idea as to why its being so slow and whether I can hope to make it more responsive? Should I just revert back to firefox 2? Anyone?

---

### Post by Rallg on 2008-04-27
I reverted to FF 2. Even during beta testing (where the users have a lot of patience) many liked 2 better than 3beta5.

As for the disk usage: Maybe a lot of the space is taken up by cached installation packages? Try
sudo apt-get clean
but be aware that if you do that and later have to re-install a package, you'll have to use apt-get to obtain it from the Internet.

---

### Post by Chris Sharman on 2008-04-27
Me too.
Just upgraded from Gutsy, and switching between tabs is taking about 3s.
It updates the tab bar graphics almost instantly, then nothing appears to happen for 3s until it suddenly & swiftly updates the page image.

No idea what's going on.
Same when I close a tab.

---

### Post by timbosity on 2008-04-27
Thanks mate. The clean thing worked a treat and now back to ~1.5GB free space on /root :)
For FF, it seems to be working fine now but every now and again it just appears to hang like for example clicking the quick reply yoke just now: it took a full 30s for the text box to come up. Then with three tabs open it seems to be just fine browsing in and out of pages etc... 

Anyway, Ill probably put FF2 back on... Shame, it looks pretty handy with the smart bookmarks etc...

---

