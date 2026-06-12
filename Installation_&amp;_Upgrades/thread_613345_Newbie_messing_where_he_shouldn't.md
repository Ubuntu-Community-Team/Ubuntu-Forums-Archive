---
title: "Newbie messing where he shouldn't"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by xprinceps on 2007-11-14
Okay, this is no one's fault but mine. In the process of trying to get a java program running (which I did), I uninstalled the following packages:
libx11-xcb-dev
libx11-xcb1
libx11-xcb1-dbg
Now they don't show up in Synaptic, so I have no idea how to reinstall them. Possibly (hopefully) related: Compiz and anything to do with it will no longer launch.
Can anyone tell me (using small words, since I don't know what I'm doing) how to reinstall these packages, since they don't show up in Synaptic?
Any help would be greatly appreciated.

---

### Post by callan79 on 2007-11-14
> **xprinceps said:**
> Okay, this is no one's fault but mine. In the process of trying to get a java program running (which I did), I uninstalled the following packages:
libx11-xcb-dev
libx11-xcb1
libx11-xcb1-dbg



Hi,

This answer will be useless to you, but I just wanted to tell you that I can't find them at all within my repositories using :

```

sudo apt-cache search libx11-xcb-dev

```

Looks like time for a reinstall if you ask me :)

Cheers
Callan

---

### Post by oldos2er on 2007-11-14
You should be able to find them with Google.

---

