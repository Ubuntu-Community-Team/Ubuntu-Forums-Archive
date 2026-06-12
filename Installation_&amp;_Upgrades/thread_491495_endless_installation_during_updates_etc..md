---
title: "endless installation during updates etc."
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by mjshepherd on 2007-07-03
Can someone help me out here?

Since upgrading to feisty ages ago I've been having repeated problems during the installation of updates (downloaded through the update manager) and new applications (through package installer).  The packages download, but during the install process the system just grinds to a halt.  My mouse cursor goes all flickery and eventually disappears altogethers, and I can hear my hard drive whirring away doing something very noisily.  There seems no way out of this (ctl-alt-backspace doesn't seem to register) except by hitting the reset button on the computer.

I've found that in some cases packages which caused problems during installation following an update can successfully be installed one by one using synaptic.  This, however is a pain, and i'd rather update the normal way.

Any ideas how to put a stop to this?

---

### Post by jpeddicord on 2007-07-05
You can try updating from the terminal to get more detailed output:

```
sudo apt-get update && sudo apt-get upgrade
```

All I can really think would be halting this would be a low-RAM system or a slow processor.

Try selecting a Failsafe Terminal from the login screen as a session. It will use less resources when you run the line above.

Jacob

---

