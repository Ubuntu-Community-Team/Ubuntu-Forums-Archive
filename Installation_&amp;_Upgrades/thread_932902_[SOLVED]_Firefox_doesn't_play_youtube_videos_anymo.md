---
title: "[SOLVED] Firefox doesn't play youtube videos anymore"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-09-28
It seems that during an update the ability to play Youtube movies got lost.

The settings are still there (Edit/Preferences/Applications):
Shockwave Flash file            Use Schockwafe Flash (in Firefox)

but the youtube video space remains a gray spot.

How can I get the video back?

bye

R.

---

### Post by darco on 2008-09-29
You may need to reinstall flash...check the repos and uninstall /reinstall....
also you may need to uninsta/reinstall flash support as well....

good luck

darco

---

### Post by Kentanner11 on 2008-09-29
I dont know your exact situation but firefox sometimes will only show 2 sec. of a video. To fix it you just clear your Cache.

---

### Post by ELMIT on 2008-09-29
Thanks, this did the trick:

> sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree


Now the movies are working again.

bye

R.

---

### Post by ELMIT on 2008-10-18
while it works, but it needs me to do that EACH time I start firefox!!!!!

How can I solve it permanent?

bye

R.

---

