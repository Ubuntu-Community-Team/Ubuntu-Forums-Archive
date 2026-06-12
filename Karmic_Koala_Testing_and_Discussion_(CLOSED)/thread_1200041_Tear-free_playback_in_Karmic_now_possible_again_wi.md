---
title: "Tear-free playback in Karmic now possible again with Intel?"
date: 2009-06-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-06-29
Ever since DRI2 and UXA were introduced, proper vsync during playback has been tricky, if not impossible to achieve.



However, here's a rather fascinating  workaround(?) that can guarantee (on my laptop at the very least)  tear-free playback in MPlayer regardless of video output without the need for any further tricks:


 ```
gconftool-2 --type bool --set /apps/metacity/general/compositing_manager false
```Here are my bits



 Kernel: 2.6.30 (2.6.31-rc1 works too!)
Driver: Intel git master
Mesa: git master
DRM: git master
DRI: git master
Xorg: 1.6.1


As to whether this works on the main repos or is restricted to the xorg-edgers PPA, I can't tell for sure, but what I do know is that the workaround works and that tearing returns with this command:


```
gconftool-2 --type bool --set /apps/metacity/general/compositing_manager true
```

---

### Post by mc4100 on 2009-06-29
This only applies if:
[list][*]You've previously disabled compiz[*]You enabled metacity compositing manually, as it's off by default anyway[/list]

---

### Post by Starks on 2009-06-29
I was under the impression that Metacity compositing was now on by default.

Also, the workaround works fine with Compiz enabled, regardless of whether sync to vblank is enabled or not.

---

### Post by mc4100 on 2009-06-29
> **Starks said:**
> I was under the impression that Metacity compositing was now on by default.

Hmm, was there an announcement? I *know* that it was off the last time I checked (a while ago, definitely) because when metacity compositing was enabled compiz couldn't be enabled (an annoying bug) -- a particular of appearance prefs, as --replace worked fine.

---

