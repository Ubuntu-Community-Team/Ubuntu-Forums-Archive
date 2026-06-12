---
title: "update to 11.04 stopped at installing new version of cupsd.conf.default"
date: 2011-06-07
forum: Installation &amp; Upgrades
---

### Post by daveli on 2011-06-07
Hi,

I am trying to upgrade to 11.04 using KPackageKit and everything was running fine until it stopped after 91% of installing updates at the following:

"Installing new version of /etc/cups/cupsd.conf.default ..."

I don't know whether to stop the process or leave it but it is taking ages to finish the estimated 3 minutes remaining.

I checked for some info in the sticky thread of this category but found not much I could do, I am more of a newbie than anything else.
Has anyone got any idea or suggestions[-o<?

Thanks a lot,

Dave

---

### Post by wildmanne39 on 2011-06-07
> **daveli said:**
> Hi,

I am trying to upgrade to 11.04 using KPackageKit and everything was running fine until it stopped after 91% of installing updates at the following:

"Installing new version of /etc/cups/cupsd.conf.default ..."

I don't know whether to stop the process or leave it but it is taking ages to finish the estimated 3 minutes remaining.

I checked for some info in the sticky thread of this category but found not much I could do, I am more of a newbie than anything else.
Has anyone got any idea or suggestions[-o<?

Thanks a lot,

DaveHi, I tried several times to upgrade but it would not complete I finally had to do a clean install.

---

### Post by Zorael on 2011-06-07
Likely there's an error that KPackageKit isn't reporting.

I always upgrade via the terminal (**do-release-upgrade**), which lets me follow the procedure a little more... closely. That said, the KPackageKit approach *should* work, and if it doesn't that's a [report-worthy bug](https://bugs.launchpad.net/ubuntu/+source/kpackagekit/+filebug).

---

