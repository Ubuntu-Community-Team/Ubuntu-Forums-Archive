---
title: "startx command not found"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by scoorocks on 2005-10-28
Hi all,

I finally got to install all the gnome and other packages on my ubuntu server with aptitude. The packages were all on my cd. However I'm just unable to get into graphical mode. My system as usual boots into text mode and after logging in giving a 'sudo startx' makes the shell tell me 'startx --command not found'..
can anyone kindly help me out eith this issue?

Thanks

---

### Post by adwait on 2005-10-28
try
```
sudo /etc/init.d/gdm start
```

---

### Post by leezer3 on 2005-10-28
Sounds far more likely that the xserver was never installed. It should be a dependancy of Gnome, I would have thought, but still :rolleyes: 
Anyway, the fact that this was a server install makes this much more likely, so run 
```
apt-get install xserver-xorg
```
The only other possibilty I can think of, is that they symlinks haven't been setup properly somewhere, but I'm afraid that's out of my depth :(

Cheers

-Leezer-

---

