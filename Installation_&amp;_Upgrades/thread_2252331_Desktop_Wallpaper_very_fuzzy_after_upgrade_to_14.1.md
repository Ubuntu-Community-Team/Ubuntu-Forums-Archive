---
title: "Desktop Wallpaper very fuzzy after upgrade to 14.10 (Lubuntu)"
date: 2014-11-11
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2014-11-11
I upgraded from Lubuntu 14.04 to 14.10. Lubuntu 14.04 was working great, for the most part. The upgrade, not so much.

One of the probems I have is that the Desktop wallpaper, no matter which one I choose, is always completely fuzzy upon any type of reboot, cold or otherwise. I can re-set the Wallpaper back to normal via Desktop Preferences. But then when I reboot the Wallpaper becomes very fuzzy again and I have to re-set via Desktop Preferences.

Also a number of the PPA's that worked with 14.04 no longer work with 14.10, or at least I cannot get them to work.

Maybe it is due to the kernel upgrade?

If anyone can be of assistance with fixing the Wallpaper issue I would appreciate it. Thank you.

---

### Post by Frogs Hair on 2014-11-11
> [COLOR=#000000]Also a number of the PPA's that worked with 14.04 no longer work with 14.10, or at least I cannot get them to work.[/COLOR]

PPA's are not official software and updated by the provider.You will have to check the Launchpad page and see if there are Utopic packages and if there are change the source from Trusty to Utopic. I would consider purging them and installing updated versions if available. PPA software sources are automatically disabled prior to upgrade.

---

### Post by roler2 on 2014-11-11
How about the Wallpaper problem? Is that a kernel issue? Wallpaper works just fine on 14.04. No fuzzyness at all. You can't even figure out the colors of the Wallpaper in 14.10 unless you reset the Wallpaper in Desktop mode. Once a reboot occurs, then the fuzzyness returns.

Should I switch back to 14.04?

---

### Post by Frogs Hair on 2014-11-11
I don't know the cause of the wallpaper problem and because Lubuntu 14.04 is based on a long term support release may be a better option. You will have to reinstall though.

---

### Post by roler2 on 2014-11-11
From the information I have been reading, both on this site and other forums, it apparently has to do with the Intel drivers, which are apparently different in 14.10 than in 14.04. It looks like I will have to go back with 14.04. I hope the issue is cleared up with the next LTS version.

---

### Post by vasa1 on 2014-11-11
> **roler2 said:**
> ...
One of the probems I have is that the Desktop wallpaper, no matter which one I choose, is always completely fuzzy upon any type of reboot, cold or otherwise. I can re-set the Wallpaper back to normal via Desktop Preferences. But then when I reboot the Wallpaper becomes very fuzzy again and I have to re-set via Desktop Preferences.
...
All I can say is that this doesn't seem to be a common problem among Lubuntu users, at least those on mailing lists and other Lubuntu haunts. I have a Dell Inspiron 1545 laptop and don't have this problem.

Upgrades, instead of clean installs, can have peculiar effects.

I feel going back to 14.04 would be the most practical thing to do if you do a clean install. If you carry over stuff such as config files etc, I wouldn't consider that clean.

If you do want to stay with 14.10, then people here will ask for more details and after some back and forth, you may find a solution!

In my opinion, and without knowing any facts other than what you've described, I feel the issue should be solvable if the wallpaper does finally display correctly.

---

### Post by roler2 on 2014-11-12
Actually I did start over today with an upgrade. Took about 5 hours being I have a slow DSL connection. Did a clean install with 14.04 and then a clean upgrade. Still the same problem. Wallpaper displays correctly with 14.04. Very fuzzy and distorted with 14.10 after every reboot. I can re-set with Desktop Preferences and the Wallpaper displays correctly. Then a reboot causes the Wallpaper to be very distorted and fuzzy until a reset. It doesn't matter which Wallpaper is utilized. It can be any of them. Even the generic ones.

Either a kernel issue as a result of the upgrade or the Intel driver or due to upgrading rather than a clean install or a combination of all three.

14.10 boots faster than 14.04. A lot faster. At least for me. But the Wallpaper distortion is a major issue for me. And it is really distorted. You can't even figure out the colors or anything. Until a reset occurs. Then everything returns to normal until reboot. Kind of a pain to reset all the time.

---

### Post by vasa1 on 2014-11-12
Why did you not do a clean install of 14.10 if that is what you want to use? Why go via 14.04? I'm confused.

---

### Post by roler2 on 2014-11-12
Because I would have to go to the Library to download it and put it on a DVD. I don't have those DVD capabilities at home, unfortunately. The Library did not have an opening at their Windows 7 station. It takes a minimum of two and a half hours. 
For 14.10 you need a DVD and that takes their Windows 7 computer at the Library. So I thought I could install successfully 
via the upgrade. Apparently not.

---

