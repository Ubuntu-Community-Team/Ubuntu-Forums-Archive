---
title: "How to restart all the configuration of Ubuntu"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by SpecialNeeds on 2010-10-04
I need to restart all the configuration of my ubuntu, that's because I ruine something in the configuration of Audio/Video, that's nobody can help me:

[http://ubuntuforums.org/showthread.php?t=1587035](http://ubuntuforums.org/showthread.php?t=1587035)

Then seems that I need to restart all the configuration, but I don't want to reinstall Ubuntu, because that I don't have a ISO of Lucid Lynx, only the ISO of Karmic Koala.

Thanks for all answers.

---

### Post by andrewthomas on 2010-10-04
If you are just having a problem with mencoder you could just

```
sudo aptitude purge mencoder
```
then

```
sudo aptitude update && sudo aptitude install mencoder
```

---

