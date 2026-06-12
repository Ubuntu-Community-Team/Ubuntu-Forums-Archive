---
title: "Upgrade to Karmic Koala breaks eclipse"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by amadain17 on 2009-11-29
I upgraded from *Jaunty Jackalope* to *Karmic Koala* and my installed eclipse seems to have broken. When I try to 'intall new software' onto it the install wizard does not appear. This worked in Jaunty. I tried uninstalling through synaptic and reinstalling but it still does not work. Is there something in theis new version of ubuntu that could make it incompatible with the latest version of eclipse. I need eclipse with certain packages installed for work. Can anybody help? Do I need to revert back to jaunty?

A

---

### Post by lightstream on 2009-11-30
Could be related to the issue with UI introduced with Karmic. Try the following:

```
export GDK_NATIVE_WINDOWS=true
```

---

