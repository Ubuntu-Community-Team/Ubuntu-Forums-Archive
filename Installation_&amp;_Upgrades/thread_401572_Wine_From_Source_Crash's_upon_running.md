---
title: "Wine From Source Crash's upon running"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by Ethos on 2007-04-04
Hello all i Just installed wine from source and upon running it it crash's my session and brings me back to the login screen as if i had logged out. Any idea why this might be happening? I cant even run winecfg, that crash's the session also. :(<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by Steve H on 2007-04-08
I'm getting the same thing. I have followed a few guides, updated my Software Sources so it points at WIneHQ, but still it crashes.

All i do is run "wincfg" from a terminal and the desktop restarts.....really annoying!  Someone mentioned reinstalling the Nvidia drivers, i will try this next and let you know what happens.......

:-?

---

### Post by zvacet on 2007-04-08
Install wine from repositories.

---

### Post by Steve H on 2007-04-08
After much to-ing and fro-ing, it turns out not to be a Wine problem, it is an Nvidia problem (or was for me anyway). i followed this post and it worked...

[http://ubuntuforums.org/showthread.php?t=336412](http://ubuntuforums.org/showthread.php?t=336412)

i hope it works for everyone else.

---

### Post by eightysix on 2007-04-08
I also had the same problem. I think it had to do with the recent update with new xorg packages. Gotta remember to always recompile your nvidia driver after that kind of update.

---

### Post by Steve H on 2007-04-09
I'll remember that for the future, Thanks for the Heads-up EightySix. Just out of interest, what sort of updates require me to recompile my drivers, obviously anything that changes the X-server, but is there anything else?

:?

---

