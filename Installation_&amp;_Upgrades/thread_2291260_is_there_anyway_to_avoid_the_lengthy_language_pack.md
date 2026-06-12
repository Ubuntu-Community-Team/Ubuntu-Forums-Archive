---
title: "is there anyway to avoid the lengthy language packs that download on each install?"
date: 2015-08-18
forum: Installation &amp; Upgrades
---

### Post by eival on 2015-08-18
this is always the longest process of any install, even when you tell it not to download updates during the install, the language packs still download, which seem meaningless since you choose your language based ISO to use from the start.

---

### Post by VMC on 2015-08-18
What I do, and have done for years, is unplug the internet right after it starts installing. I leave internet on so it can determined my location. 
After all that and on reboot, a menu comes up saying language support error. Close it install bleachbit and among other items check Localizations. 
It then remove some 200+ megs. All those LC_MESSAGES files are gone.

edit: that remove internet saves me some 10+ minutes of downloading language files.

---

### Post by eival on 2015-08-19
> **VMC said:**
> What I do, and have done for years, is unplug the internet right after it starts installing. I leave internet on so it can determined my location. 
After all that and on reboot, a menu comes up saying language support error. Close it install bleachbit and among other items check Localizations. 
It then remove some 200+ megs. All those LC_MESSAGES files are gone.

edit: that remove internet saves me some 10+ minutes of downloading language files.

yeah ive done that method as well, but seems really unnecessary, especially when the checkbox to download or not is there, and it wouldnt be so bad if they at least did a server test to download from the fastest server rather than the default one and watching meaningless packages download at low triple and sometimes double digit kb's

either that, or just have a larger DVD iso version that has all that stuff included, so the "download updates" are literally just any software security updates since the ISO version was released

---

### Post by VMC on 2015-08-19
Maybe preseeding if you know how that works. I never got it to obey.
[https://wiki.ubuntu.com/UbiquityAutomation](https://wiki.ubuntu.com/UbiquityAutomation)

---

