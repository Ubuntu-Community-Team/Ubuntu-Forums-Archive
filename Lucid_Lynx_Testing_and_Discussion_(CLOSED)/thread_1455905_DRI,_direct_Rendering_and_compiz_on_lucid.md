---
title: "DRI, direct Rendering and compiz on lucid"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dracayr on 2010-04-16
Hi,

After upgrading to Lucid, I found that Dri was disabled: from Xorg.0.log:
```
(WW) intel(0): i845 or i855 chip detected.  Disabling DRI to prevent system instability.
...
(II) intel(0): direct rendering: Failed
```

As a result, compiz, games, etc. won't work. I used Dri with my chipset before, and although there were performance issues, I found a fix somewhere (never had crashes). So, despite the warning, I want to at least try to use DRI. So, does anyone have an idea on how to enable DRI? I tried 'Option   "DRI" "On"' and 'Load   "dri"' in xorg.conf, and both times, dri was loaded only to be unloaded again because of 'System instability'.

Thanks,
dracayr

---

