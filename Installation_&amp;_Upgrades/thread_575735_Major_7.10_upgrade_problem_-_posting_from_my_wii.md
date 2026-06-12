---
title: "Major 7.10 upgrade problem - posting from my wii"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by murraj2 on 2007-10-14
i upgraded from 7.04 to 7.10 last night. everything seemed fine. restarted it and after seeing first screen with ubuntu and progress bar screen goes black. using a t40 laptop, plugged into monitor gives same problem . can only get to recovery mode . unfortunately i don,t have a live cd or second computer . 

would greatly appreciate any help

---

### Post by PmDematagoda on 2007-10-14
Try:-
```

dpkg-reconfigure -phigh xserver-xorg
```

in Recovery Mode, if that doesn't work try:-
```

dpkg-reconfigure xserver-xorg
```

---

### Post by ringmaster on 2007-10-14
Try Ctrol+Alt+F7. This works for me, every time I boot the X.org server starts without sending data to monitor.

If this doesn't work try Ctrol+Alt+F1 and after login with your name and password then try what the previous post says:

Try:-

Code:
sudo dpkg-reconfigure -phigh xserver-xorg (it will ask for your password)

in Recovery Mode, if that doesn't work try:-
Code:

sudo dpkg-reconfigure xserver-xorg

---

### Post by murraj2 on 2007-10-14
The first solution works, thanks a lot. Just gotta set up my xorg.conf now.

I think I'll burn a live CD so I always have one so that I can at least get to the net/forums if i need it.

---

### Post by skompier on 2007-10-14
> **murraj2 said:**
> 
I think I'll burn a live CD so I always have one so that I can at least get to the net/forums if i need it.

Excellent idea..:wink:

---

