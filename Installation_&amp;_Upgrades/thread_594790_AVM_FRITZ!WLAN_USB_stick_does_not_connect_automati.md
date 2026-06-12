---
title: "AVM FRITZ!WLAN USB stick does not connect automatically"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by li009 on 2007-10-28
My AVM FRITZ!WLAN USB stick will unfortunately only establish a connection to my router automatically, if the stick is inserted at system-bootup. I could not find a comfortable way for it to connect automatically if I insert the stick later on.

For now I help myself out by typing those commands ...```
sudo ifdown wlan0
sudo ifup wlan0
```

But perhaps there is a more comfortable way. I was also thinking of putting those commands into a shell but I do not get this to work since administrative privileges are needed by those commands.

---

