---
title: "installing OSS on Hardy"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by mab1376 on 2008-04-29
im trying to install the new version of OSS that compatible with the X-Fi sound card but it will not intstall

```
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
```

help!

also whats a ood volume manager for OSS?

---

### Post by lemming465 on 2008-05-05
Ubuntu converted the backend sound support from ALSA to pulseaudio.  You may be able to get legacy OSS applications to work, but I wouldn't try installing new OSS drivers.

The specific message suggests that either it isn't running as root when it needs to, or that some prerequisite is missing.

---

