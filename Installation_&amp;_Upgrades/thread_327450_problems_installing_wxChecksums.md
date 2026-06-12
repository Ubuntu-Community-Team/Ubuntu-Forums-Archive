---
title: "problems installing wxChecksums"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by stoof on 2006-12-29
Hey,

I'm having trouble installing wxChecksums. I downloaded the official .rpm and installed using alien (on ubuntu 6.10). I've got the latest wxWidgets, I hope, but when I try to run wxChecksums, I get: 
"wxcksums: error while loading shared libraries: libwx_gtk2-2.4.so.0: cannot open shared object file: No such file or directory"

So, that should only be a missing lib, but how come it's missing when I have all the wx stuff I can find in synaptic installed? wxChecksums should really be included in the reps btw...

Thanks for any help.

---

### Post by moma on 2006-12-29
Update library cache.
$ [COLOR="Green"]sudo ldconfig[/COLOR]

---

