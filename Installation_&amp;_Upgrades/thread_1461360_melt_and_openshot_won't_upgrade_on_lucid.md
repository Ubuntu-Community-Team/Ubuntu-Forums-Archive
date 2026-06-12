---
title: "melt and openshot won't upgrade on lucid"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by karesz on 2010-04-24
The day before yesterday, I've upgraded my 32bit karmic to 32bit lucid rc. The upgrade was flawless, so is the system. My only problem is, that melt and openshot won't upgrade... :( Not with upgrade, nor dist-upgrade. :( I've also tried apt-get install -f, no use. Any idea?

---

### Post by Tetchy Tony on 2010-05-09
No expert here, 64bit Lucid via WUBI.  Update Manager merely showed me greyed-out boxes for these two.  In Synaptic, I was able to mark Openshot for upgrade, but Melt only offered to uninstall - 'no support available'.  So I did the Synaptic upgrade for Openshot.  After that, Synaptic offered 'reinstall' for Melt, so I did.  Update manager is now satisfied, no entries, greyed-out or otherwise, at all.  Job done? ...What's all this for? (I only use WUBI for elderly-intellectual exercise, but Lucid works so well, I'm tempted to find out).

---

### Post by c0ns0lat0r on 2010-06-16
I confirm this solution that worked also on my Kubuntu using Adept:
- remove first your current Melt installation package (ex.: version 0.4.4) and it'll remove also Openshot;
- select and install then again Melt (updated version ex: 0.5.4) and it'll install other dependencies of the new multimedia framework MLT

---

