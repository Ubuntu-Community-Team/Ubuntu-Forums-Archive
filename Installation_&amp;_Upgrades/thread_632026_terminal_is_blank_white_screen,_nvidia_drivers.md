---
title: "terminal is blank white screen, nvidia drivers"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by Mindflux0 on 2007-12-05
The terminal is now a blank white screen (it's running, if I type exit->enter it quits but I can't see anything)
I assume this has something to do with the nvidia drivers I just installed.  I need to edit the x config file or something I think.
Help would be appreciated.

---

### Post by PmDematagoda on 2007-12-05
Go to a terminal after Ubuntu finishes loading by pressing Ctrl+Alt+F1 and then do:-

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

After you get your GUI we can set out to reinstall the Nvidia driver properly.

---

### Post by Mindflux0 on 2007-12-05
the gui runs fine except that the terminal comes up as a blank white screen.
Should I still do that?

---

### Post by VonDecker on 2007-12-07
Just go to System->Preferences->Appearance, "Visual Effects" tabs, and select "none". No more cute effects, but it solved it for me. 

Hope it helps...

---

