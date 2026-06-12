---
title: "Chrome after upgrade to Karmic"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by Hagar55 on 2009-11-14
I installed Chrome in Jaunty, all was well I received upgrades on a regular bases.
Since I upgraded to Karmic chrome still works just fine, but I haven't received any updates whatsoever.
If i go to the software sources in Admin and I choose Other Software, I no longer see any entries for chrome. But if I go to the Authentication tab there is still a key for Chrome.

Will I still receive updates for chrome or do i need to renter the software source for chrome in Karmic, and if so where do I find it.

---

### Post by tbone7 on 2009-11-14
Hey, I'm getting chrome updates from [this ppa]("https://launchpad.net/~chromium-daily/+archive/ppa")

Do

sudo add-apt-repository ppa:chromium-daily/ppa
sudo apt-get update

to add it.

---

### Post by Hagar55 on 2009-11-15
Added the PPA, getting updates again, thanks.

---

