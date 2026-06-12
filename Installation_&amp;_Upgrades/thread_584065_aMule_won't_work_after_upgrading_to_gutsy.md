---
title: "aMule won't work after upgrading to gutsy"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Heywood Floyd on 2007-10-20
I upgraded my Ubuntu from feisty to gutsy and it all worked OK but for aMule. When I try to run it I get this error ```
amule: relocation error: amule: symbol _ZN12wxStringBase8InitWithEPKwjj, version WXU_2.8 not defined in file libwx_baseu-2.8.so.0 with link time reference

```

I reinstalled both aMule and wxwidgets but I keep getting the same error. Other programs using wxwidgets work fine, it's just aMule which won't (of course, aMule worked perfectly before the upgrade).

Any assistance you could provide would be much appreciated. Thank you very much.

---

### Post by sovereign_soul on 2007-10-22
I am also facing the same problem. I tried to compile amule from the source but that too doesn't work. Errors like class wxGIFDecoder has n member names ReadGIF etc etc

Any help would be appreciated

---

### Post by sovereign_soul on 2007-10-29
Solved it , recompiled wxwidget with unicode enabled

---

