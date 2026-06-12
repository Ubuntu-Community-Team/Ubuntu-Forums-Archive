---
title: "installing exaile removed apt"
date: 2008-05-30
forum: Installation &amp; Upgrades
---

### Post by nomis3613 on 2008-05-30
I installed Exaile it did warn me that it was going to remove "apt", but I figured that there must be some reason for it so I trusted the installed and continued. Silly me! Now Synaptic is gone ("command not found") so I can't install anything. Can you please help me fix it?

When running Exaile, it wouldn't do very much, kept saying that plugins (gstreamer- which I know I have and python-cddb which I assume I would have) were missing. I'm just mentioning this in case it helps work out what is wrong.

Thanks,
Simon

---

### Post by enoughsaid05 on 2008-05-30
Hihi

Just asking, can you try opening up the terminal and type in 

sudo aptitude install synaptic

and press tab twice to see the full name of the package (i can't remember the name already :P) and press enter.

---

### Post by bapoumba on 2008-05-30
I'm curious to know how this happened. apt is not a dependency for exaile..
You may need to download the package again and install it with dpkg.
You can find apt here : [http://packages.ubuntu.com/hardy/apt]("http://packages.ubuntu.com/hardy/apt"). Were other dependencies removed to? (you may be in some depencency trouble here..).

---

