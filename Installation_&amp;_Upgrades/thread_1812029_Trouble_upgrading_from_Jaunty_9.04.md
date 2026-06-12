---
title: "Trouble upgrading from Jaunty 9.04"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by jensenguy on 2011-07-25
I've read through multiple threads about this but haven't found anything that works for me yet. I'm trying to upgrade 9.04 to 10.04, and I can't come up with anyway to do so short of a fresh install which I do not want to do. 

I've modified my sources.list and *.distupgrade to use the old-releases.ubuntu.com, but doesn't change anything. I don't seem to have the option to try to upgrade to 9.10 either. 

Any ideas?
thanks, jim

---

### Post by zvacet on 2011-07-26
You can try with [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by jensenguy on 2011-07-26
The EOL page instructions don't work - I think 9.10 has gone EOL since it was written. 

 I've managed to get an upgrade to 9.10 started, by editing my meta-release file to show karmic as supported, The GUI update manager still is set on 10.04, but running do-release-upgrade has 9.10 downloading as we speak.
We will see in a few hours if it worked!

---

### Post by dino99 on 2011-07-26
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

