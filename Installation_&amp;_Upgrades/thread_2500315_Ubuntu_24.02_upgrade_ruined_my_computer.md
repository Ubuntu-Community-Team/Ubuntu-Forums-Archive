---
title: "Ubuntu 24.02 upgrade ruined my computer"
date: 2024-08-29
forum: Installation &amp; Upgrades
---

### Post by kylekendall78 on 2024-08-29
I just got a new computer because I was having issues with 22.04 that led to my admittedly older laptop being irreparably lost.  I have been just fine with the new computer and a fresh 22.04 install until they offered the 24.02 supposed "LTS" upgrade.  Now my new computer became unbootable and I am reinstalling 22.04 with a USB drive.  All of which is not terrible but I had new plugin settings in Ardour that are completely lost.  I have been a loyal supporter and user since 2006 and this is how you treat me?

---

### Post by currentshaft on 2024-08-29
..

---

### Post by currentshaft on 2024-08-29
.

---

### Post by guiverc on 2024-08-29
A few responses

- there is no Ubuntu 24.02 release (2024-February), as releases are in April (.04) & October (.10) except for *respins* which don't get their month used.

- You can *non-destructively* re-install Ubuntu **Desktop** systems using the `calamares` or `ubiquity` installers, meaning no data is lost, and apps you've installed from official Ubuntu repositories get auto-reinstalled, thus even apps you use aren't impacted...  Even if using 3rd party apps, as most desktop apps store data in $HOME or your user directory; your apps settings won't get lost anyway on *non-destructive re-install*...   But maybe you're talking about a server system, where I'm a desktop user thus think of desktop products.

- the largest impact (esp. on older devices; and an *older laptop* was specifically mentioned), the largest issue I find is related to the newer kernel, and those are fixed... so the only checks you can perform on those are device specific & thus you must do yourself using *live* media prior to accepting any upgrades..  ie. 24.04 LTS is used 6.8 kernel on GA+HWE currently; where 22.04 is using 5.15/6.8 (*if fully upgraded; but it was recently 6.5 so you may have been on older kernel*), so download the ISO using the kernel you'll upgrade to & test it *without install* and get a *feel* for how it performs or importantly any problems.. 22.04 media exists with 6.8 now too (*though not yet official*).  If your 22.04 system was using GA kernel, there will be a HUGE change on any upgrade which cannot be helped.

---

