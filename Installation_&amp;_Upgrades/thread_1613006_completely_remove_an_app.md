---
title: "completely remove an app?"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by dominik.l on 2010-11-03
hey

ok, so i've decided to give ubuntu another try. used arch for a while...
how exactly can i completely remove an application (for example evolution)?
in arch pacman would take care of it all with a simple pacman -R  evolution... that completely deleted evolution. i used apt-get remove  --purge evolution
also just purge and autoremove

also if anyone knows a nice list with all apt commands.

thanks in advance

cheers,
d

---

### Post by Quackers on 2010-11-03
Be careful removing default programs. Some of them (like Evolution) have tie-ins to system files. I uninstalled Evolution completely using Synaptic and my system wouldn't boot, due to some other associated things being removed. See here

[http://ubuntuforums.org/showthread.php?t=1559996](http://ubuntuforums.org/showthread.php?t=1559996)

---

