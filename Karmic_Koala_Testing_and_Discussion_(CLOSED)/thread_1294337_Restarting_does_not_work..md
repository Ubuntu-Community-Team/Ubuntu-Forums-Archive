---
title: "Restarting does not work."
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by amano on 2009-10-18
]When I choose "Shutdown" everything works as expected. When I choose "Restart" I see the usplash screen and then everything goes black and no restart happens.

Sometimes I can see a command-line message:

> * Will now restart
[ 6366.812595] Restarting system ..

Does anyone have this problem as well? Is there a launchpad bug already? Which component is affected by this bug?

---

### Post by dino99 on 2009-10-18
hi,

i've the same problem since karmic a2: like you, shutdown is ok but restart don't work at all. When i want to restart, system is ended but not stopping, then restart freeze after choosing the partition to boot.

The solution for me is to unplug the psu, wait some seconds and turn power on again, then i can boot.
I suppose that it is a problem with grub2 (still beta !!!): as final karmic release is close now, i hope this been fixed.

---

### Post by dentaku65 on 2009-10-18
What about doing:
```
sudo init 6
```
in a console?

---

