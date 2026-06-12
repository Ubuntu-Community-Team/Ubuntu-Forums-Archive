---
title: "Broken essential package at the repository"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by pibb69173 on 2008-03-27
--------------------------------------------------------------------------------

what i did was edit my html on my psp and got all the packages then i ran into major trouble i installed a package called e2fsprogs 1.40 then it told me the package was broken and i cant install any more packages without removing it and if you didnt know its an essential part of ur system and if u remove it then it removes a tune of essential packages so now i cant finishing updating and cant install any .deb's or remove the broken package, im in a state of panic plz plz help

---

### Post by Joeb454 on 2008-03-27
I'm not sure if you can or not, but if you *can* then run ```
sudo dpkg --configure -a
```

It should repair any broken packages :)

---

### Post by pibb69173 on 2008-03-27
the reson i used my psp was because i dont have internet on my comp yet i was woking on the when up dating but ill try it

---

