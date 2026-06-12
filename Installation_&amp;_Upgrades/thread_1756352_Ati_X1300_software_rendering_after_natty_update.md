---
title: "Ati X1300 software rendering after natty update"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by kfoe on 2011-05-12
Hi,

I've recently updated my computer from 10.10 to 11.04 and since then I get software rendering on my graphics card which makes everything run very slow. I'm not using compiz or any other visual effects. 

Here is my card :
```
lspci |grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
```

And this is what I see in Xorg.0.log :
```
(II) AIGLX: Trying DRI driver /usr/lib/dri/r300_dri.so
[    31.930] (EE) AIGLX error: Calling driver entry point failed
[    32.005] (EE) AIGLX: reverting to software rendering
```

I'm not using a xorg.conf file.

Unfortunately restricted drivers are not compatible with my card so I can't try using them. Any ideas?


Thanks

---

