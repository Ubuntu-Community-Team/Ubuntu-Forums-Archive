---
title: "Hardy Restricted Driver Install Limited Resolutions"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by SteveF on 2008-09-23
I just installed Hardy (am having a lockup problem but that is another post).  I selected enable on the nvidia restricted drivers and it installed the package.  I rebooted.  The screen comes up in 1024x768.  I went to screen resolution, but that is the highest setting.

Under Gutsy (no restricted) I am using 1280x1024 and it supports up to 1600x1200.

Shouldn't I be able to at least match that setting?

Steve

---

### Post by Partyboi2 on 2008-09-24
Have you tried changing the screen resolution using nvidia-settings?
```
 gksudo nvidia-settings
```

---

### Post by SteveF on 2008-09-24
> **Partyboi2 said:**
> Have you tried changing the screen resolution using nvidia-settings?
```
 gksudo nvidia-settings
```

Thanks.  I installed nvidia-settings and I was able to change the resolution.  One problem down, one other to go.

Steve

---

