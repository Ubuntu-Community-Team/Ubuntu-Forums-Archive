---
title: "Not upgradeing"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by rosanbio on 2010-04-23
hai, when i am tryg to upgrade to lucid from karmic, update manager starts and shows my system is up-to date.
command used "update-manager -d"
os karmic 64bit
any idea any one???

---

### Post by 2hot6ft2 on 2010-04-23
You might try going to
System > Administration > Software Sources
Click on the Updates tab and at the bottom is Release Upgrade
Change it to either Normal Releases or Long Term Support releases
Then close and go to
System > Administration > Update Manager and see if it's there.

---

### Post by garvinrick4 on 2010-04-23
Copy and paste this into your terminal.


sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list  && sudo aptitude update && sudo aptitude dist-upgrade

---

