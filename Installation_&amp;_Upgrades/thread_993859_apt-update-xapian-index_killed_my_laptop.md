---
title: "apt-update-xapian-index killed my laptop"
date: 2008-11-26
forum: Installation &amp; Upgrades
---

### Post by gilbert_george on 2008-11-26
Have recently upgraded to 8.10 and after doing so noticed a severe deterioration in my laptop. This was most notable during automatic package updating, something that used to last a few minutes and was a minor irritation now lasts nearly an hour and can grind my laptop to a complete standstill.

After some investigation it appears that apt-update-xapian-index is to blame, it uses lots of CPU and RAM and thrashes the Hard Drive all to create an index of the deb pacakage info - something I rarely use and can do without quite easily. It seems this package has made it into the core of both the debian and ubuntu releases which is a shame.

Hopefully is will be backed out of the next releases.In the meantime I have removed it and hopefully that will solve my problems.

---

