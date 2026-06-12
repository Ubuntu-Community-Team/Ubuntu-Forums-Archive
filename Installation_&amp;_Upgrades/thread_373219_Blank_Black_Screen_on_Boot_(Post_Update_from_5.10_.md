---
title: "Blank Black Screen on Boot (Post Update from 5.10 -&gt; 6.06)"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by Naithin on 2007-03-01
Hi there guys,

Basic scenario is that I've just completed the update from 5.10 -> 6.06 (via synaptic and updating the repository references).

During the configuration page it asked me if I'd like to overwrite the existing configs with the new versions available, or to keep the existing config.

Considering the scope of the upgrade, I figured it would be best to allow the new config, thinking it would simply change it to a default safe mode that worked on more or less anything until could get in there and configure in full. But evidently, this is not the case, and Gnome/Xorg no longer inits in any meaningful way.

Now I've heard I can generally go back to the shell by ctrl-alt-backspace and try to fix things from there, but I'm not entirely sure what I would need to enter into the conf file in any case.

Will the old conf have been backed up? And if so, is it possible to simply rename to be current and have it work, or will as I originally suspected this file no longer be relevant with such the large version jump?


As for my system specs to assist me here:

AMD Athlon64 3400+ (running x86/32bit kernel)
1GB RAM
ATI Radeon X800 Pro w/ 256MB DDR3
Creative Audigy2 ZS
160GB Western Digital SATA HDD
Mobo chipset is VIA


My own experience with linux while existant, is still very limited. Any assistance in this issue would be much appreciated, if you have any further queries in regards to the issue, let me know. :)

---

### Post by zvacet on 2007-03-01
Go to the terminal with ctrl+alt+F1 and when you are there
```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Naithin on 2007-03-01
Hey there, thanks for the reply, very good to know how to access that. :)

I ended up having to rectify the issue manually with vim-ing the xorg.conf, changed the ATI driver to vesa and dropped the 1600x1200 support which seems to let me login now. Using the ati driver no longer does.

I couldn't say it was the ATI driver I was using before - never had occasion to check it, everything was fine ;p - but I have noticed that now the window refresh is very slow (ie when scrolling firefox, it jumps rather than scrolls) so I had a better driver before.

Will be lookin to install the ATI propriety driver now I think and see how that goes.. <finger crossed>

Thanks again for the reply! :)

---

