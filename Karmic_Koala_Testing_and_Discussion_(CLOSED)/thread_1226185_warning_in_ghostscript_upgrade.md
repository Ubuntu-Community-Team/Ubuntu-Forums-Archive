---
title: "warning in ghostscript upgrade"
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zika on 2009-07-29
Is this a problem or not?
```
Setting up ghostscript (8.70.dfsg.1~rc1-0ubuntu1) ...
update-alternatives: using /usr/bin/ps2pdf14 to provide /usr/bin/ps2pdf (ps2pdf) in auto mode.
update-alternatives: warning: not replacing /usr/bin/ps2pdf with a link.
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/ps2pdf14 because link group ps2pdf is broken.
update-alternatives: warning: not replacing /usr/bin/ps2pdf with a link.
update-alternatives: warning: forcing reinstallation of alternative /usr/bin/ps2pdf14 because link group ps2pdf is broken.
update-alternatives: warning: not replacing /usr/bin/ps2pdf with a link.
Updating font configuration of gs...
```

---

### Post by mrsurb on 2009-07-29
Don't know, but the same happened to both of my computers when they updated today.

---

### Post by colorprint on 2009-08-09
I have this issue after this upgrade:
[https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/410556](https://bugs.launchpad.net/ubuntu/+source/ghostscript/+bug/410556)

---

