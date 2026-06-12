---
title: "Upgrade to 11.04 ATI Graphics &amp; Wifi problems"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by PhilCash on 2011-06-11
G'day All,

This forum has been so useful to me in the past that I thought I'd offer a tip of my own. After upgrading to 11.04 I had TTY only (no graphics). I could boot to recovery mode with minimal graphics, but then had no WIFI. I could boot to earlier versions of Ubuntu and all was well - including the new style interface. I'm computer literate, but not not not linux literate.

I tried the main sticky posts on such stuff without success and with much bemusement. Much trolling/searching in this forum indicated a possible driver problem. Using recovery mode low graphics, I checked my Additional Drivers settings and found that my ATI driver and WIFI driver had been disabled in the upgrade - seemingly as they are not open source. Simply re-enabling them (with a wired Internet connection) has reinstalled them and I'm back up and running.

I hope this helps someone to resolve their problems more quickly than it took me.

Lessons learned:
1. Don't upgrade unless there are really good reasons to do so.
2. If you plan on upgrading, plan on wasting a couple of days fixing the upgrade.
3. Open source advocates seem to have the same regard for proprietary software as proprietary advocates have for open source software. Come on developer guys and gals, its not a tit for tat competition. Don't follow proprietary dude standards of behaviour, show em how it should be done.

Cheers,
Phil

---

### Post by el_koraco on 2011-06-11
The ATI driver you used in the previous version would not have worked in 11.04, because 11.04 uses a new version of the Xserver, for which the 10.10 version of Catalyst was not written. So, it's not an open/proprietary source thing.

---

### Post by PhilCash on 2011-06-11
As you say el_koraco. Nevertheless, the upgrade to 11.04 resulted in no graphics and no wifi on my laptop.

I would expect an upgrade installer to analyse the existing system before making any changes and retain or replace existing drivers and settings with working compatible ones rather than leaving the system broken.

Simply re-installing the propriety drivers fixed the problem. If a near clueless end user such as myself can do this, I fail to understand why a dedicated upgrade installation application did not check it and do it as a matter of course.

Cheers,
Phil

---

