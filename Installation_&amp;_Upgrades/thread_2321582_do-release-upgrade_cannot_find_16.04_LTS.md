---
title: "do-release-upgrade cannot find 16.04 LTS"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by oz1cz on 2016-04-23
I have two Linux boxes, one running 14.04 LTS and one running 12.04 LTS. I want to upgrade both of them to 16.04 LTS, but the updater cannot find the release.

On the 14.04 LTS box, "do-release-upgrade -c" says "No new release found". If I write "do-release-upgrade -c -d", I can install 16.04LTS, but why is it considered a development upgrade for which the "-d" flag is required?

On the 12.04 LTS box, "do-release-upgrade -c -d" allows me to upgrade to 14.04.4 LTS, but not 16.04 LTS. Do I need to go via 14.04 to get to 16.04?

---

### Post by Rocky_Bennett on 2016-04-23
If I were you I would back up all of my data and perform a clean install of Ubuntu 16.04 on those machines. A clean install will be a much better option.

---

### Post by Bucky Ball on 2016-04-23
The upgrade path from 14.04 to 16.04 becomes 'official' at the first point release of 16.04(.1) in a few months (and perhaps you'll need to use -d until then). 16.04 upgrade will also be available via the GUI at that time.

LTS upgrades to the NEXT LTS. e.g. 12.04 LTS> 14.04 LTS> 16.04 LTS> 18.04 LTS> etc ...

LTS to LTS leapfrogs the interim releases in between but you can't LTS to LTS and leapfrog and LTS in between.

Upgrade possible on the 14.04 LTS machine. Clean install for 12.04. Not worth the time and effort. Goes without saying, backup both machines before proceeding. 

Good luck.

---

