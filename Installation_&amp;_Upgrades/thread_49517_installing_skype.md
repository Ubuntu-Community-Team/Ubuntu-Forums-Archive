---
title: "installing skype"
date: 2005-07-16
forum: Installation &amp; Upgrades
---

### Post by dot on 2005-07-16
l am having this error during my installation of skype "error while loading shared libraries libqt-mt.so.3" l cant seem to find this library anywhere l need suggestions on packaging skype

---

### Post by magoo on 2005-07-16
Hello,

This is the correct package to install:
```
libqt3c102-mt
```

And if you want to change the look and feel of qt applications, you will need this one too:
```

qt3-qtconfig

```
and launch from a terminal:
```

$ qtconfig

```
bye,

---

