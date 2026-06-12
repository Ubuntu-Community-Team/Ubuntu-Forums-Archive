---
title: "nvidia breaks after reboot"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by kraylus on 2007-08-16
problem:
after installing latest driver from nvidia webiste, works great til i reboot. if i use the nvidia-glx that is in apt-get, it does not work. and of course, using just plain nv isn't good enough.

solutions i've tried:
-ensuring that the nvidia module was added to /etc/modules
-tried envy (says it wasnt compatible with my "operative"(sic) system
-tried uninstalling and reinstalling glx
-something else i cant remember and cant seem to find again

i recall gentoo having some wierd thing where modules wouldnt reload after a reboot because of some wierd precache thing it ran... i don't really remember. this is my first dip into linux in several years, so im a bit rusty.

i just dont like having to reinstall the nvidia drivers every reboot. im so close to not needing windows....

thanks,

ryan

---

### Post by kraylus on 2007-08-16
ok, so the problem with envy was that i was using an old version .8 or some such. got .9.6-ish and it worked... sorta. it installed an updated driver that was able to survive boot, but the screen had a green hue, poor refresh, and if it were a crt it woulda been buzzin at me.

sooo... i figure maybe envy fixed the other stuff that might been wrong with whatever kept the driver from stickin on a reboot. so i reinstalled the official nvidia driver, rebooted, and bingo.

problem solved.

---

