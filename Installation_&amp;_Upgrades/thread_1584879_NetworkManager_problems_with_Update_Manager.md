---
title: "NetworkManager problems with Update Manager"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by jeff17237 on 2010-09-29
Everytime Ubuntu decides it wants to do an automatic update, if I let it update itself it uninstalls NetworkManager.  A few weeks ago after switching to Lucid Lynx, I had problems getting wifi to work (no Network Manager icon in panel).  I ended up reinstalling the network-manager-gnome package and things seem to be working fine.  However, whenever I tell Update Manager to "Install Updates" itself, it always re-uninstalls NetworkManager and I am once again left with no wifi.  This has caused me to have to manually install all the updates through aptitude.  This works fine, but a large amount of updates results in a large of amount of time wasted manually installing each updated package.  I would like to avoid this is if at all possible.  Any suggestions?

---

### Post by jeff17237 on 2010-09-29
bump

---

### Post by wilee-nilee on 2010-09-29
> **jeff17237 said:**
> bump

Bumps are on a 24 hour time between.

I would look through your log files. This is a problem I have never seen, so it may be up to you to figure this out, maybe also trying other forums as well. 

Personally If this was happening to me I would do a install to a thumb via the disc creator, with persistence enough to do a update and upgrade and see if this happens on the thumb as well. If it doesn't I would probably reinstall, after backing up what I wanted. If you have a 8 gig or larger thumb you coild do a full install, jsut make sure grub is pointed at the thumbs mbr at the advanced button on the last install screen.

---

