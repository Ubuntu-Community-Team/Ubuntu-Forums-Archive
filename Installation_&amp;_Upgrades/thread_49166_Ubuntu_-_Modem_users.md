---
title: "Ubuntu - Modem users"
date: 2005-07-15
forum: Installation &amp; Upgrades
---

### Post by saadat on 2005-07-15
Now Ubuntu looks promising.... however, for slowwww dialup users like me who have to rely on getting updates from elsewhere........ what would be the procedure to download the updates on another machine else where and then bring them on a usb stick!!!

---

### Post by jasmuz on 2005-07-15
[QUOTE=saadat]Now Ubuntu looks promising.... however, for slowwww dialup users like me who have to rely on getting updates from elsewhere........ what would be the procedure to download the updates on another machine else where and then bring them on a usb stick!!![/QUOTE]
 To be honest, i have dialup and i download all my updates via web, because if you want to bring the packages manually you would have to know every dependency and file you need, store it and  then manually place install them on /var/cache/apt/archives, so when you fire up synaptic it will read it from there.

Or sudo dpkg -i everypackage

---

