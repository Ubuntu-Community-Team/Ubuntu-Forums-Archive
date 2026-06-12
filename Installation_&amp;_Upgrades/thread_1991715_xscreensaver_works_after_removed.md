---
title: "xscreensaver works after removed"
date: 2012-05-30
forum: Installation &amp; Upgrades
---

### Post by andoras on 2012-05-30
Hi!
I am using 12.04
A few days ago I installed xscreensaver but after I removed it.
Now it still works, after ten minutes my screen become black (it's very annoying at watching movies)

What I've done:
[LIST]
[*]sudo apt-get remove xscreensaver
[*]I removed everything from startup applications
[*]Deleted ~/.xscreensaver
[/LIST]

After those, it still works.
Could anyone help? I really don't understand at all

Thanks
andoras

---

### Post by raja.genupula on 2012-05-30
i think screensaver was set to 10 min and so its getting up after 10 min . look the time was set to screensaver .

---

### Post by andoras on 2012-05-31
Hi Raja!
Yes the screensaver was set to 10 min, but it worked after I removed.
But, i found a solution, and I wright it to anyone else who needs.
1. reinstall screensaver
2. change times to very high. You can do it by changeing ~/.xscreensaver to the following
timeout:	10:00:00
cycle:		10:00:00
3. Take care (that was my mistake) don't change minutes more than 59...

That's it, once you installed it, better to keep it.

andoras

---

