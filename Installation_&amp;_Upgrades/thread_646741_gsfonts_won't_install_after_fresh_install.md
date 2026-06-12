---
title: "gsfonts won't install after fresh install"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by docdailey on 2007-12-21
Just got done doing a netboot install converting a thin client to a thick client using the alternate desktop iso.  (WHEW!)  Never thought I'd be able to get something like that done but it went ok...

anyway, I tried to install mythbuntu and it said I needed gsfonts...so I tried to  apt-get install them and it says they arent in the repository (gsfonts gsfonts-x11).  Something wrong with aptitude?

I will say this, after I converted it to a thick client I then moved it over to the non pxe side of the network it wouldn't update and I realized the netboot installer left my install proxy settings in apt.conf.  So I deleted apt.conf (that was the only thing in there).

I am not at home right now to recheck sources but I am almost 100% sure that main, universe, restricted and multiverse are enabled (100% sure on universe and multiverse).

TIA,

Doc

---

