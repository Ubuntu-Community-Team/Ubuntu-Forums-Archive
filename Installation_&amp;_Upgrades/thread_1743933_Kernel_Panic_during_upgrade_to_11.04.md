---
title: "Kernel Panic during upgrade to 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by zonedabone on 2011-04-29
I've got a desktop running ubuntu 10.10. I decided that It would be easy and quick to use the automated update manager. (My mistake. Last time I used a nice graphical thing like that I ruined my partition table) Anyway, I got through to installing packages, and that's where everything has gone wrong. When it gets to

```
Setting up udisks (1.0.2-4ubuntu1)
```

I got a kernel panic. (That's what I've been told the blinking lock keys mean. I haven't done any rebooting or anything, because 11.04 is now half installed. Can I somehow repair the install, or should I just burn a 11.04 disk and start from scratch?:(

---

### Post by Nanodeath on 2011-04-30
I got the same thing -- while down to 1 minute in installing packages I got a kernel panic (flashing numlock/capslock), so after a while I restarted and got a black screen + kernel panic.  If I choose the latest entry under Previous Linux Versions it boots fine...so I guess I'll be doing that for now.

---

### Post by Nanodeath on 2011-04-30
So, after booting up with the old kernel, I was able to get far enough to run dpkg --configure -a (I forget the exact command) and was able to finish the installation, and now the regular latest kernel works fine.  So...that fixed it for me.

---

