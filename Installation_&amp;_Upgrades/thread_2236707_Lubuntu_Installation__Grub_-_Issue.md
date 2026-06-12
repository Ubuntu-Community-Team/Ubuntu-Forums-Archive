---
title: "Lubuntu Installation : Grub - Issue"
date: 2014-07-28
forum: Installation &amp; Upgrades
---

### Post by crawf777 on 2014-07-28
Dear All,

I recently installed Lubuntu 14.04 for a friend, on an old xp machine, a Packard-Bell AMD Athlon 64...

The installation, apparently went smoothly, however when I rebooted, lubuntu booted straight to the lubuntu splash screen, that is, bypassing the expected grub screen.

Just wondering has anyone seen this type of behaviour before?

I am unsure if it is a bad install or just an artifact of the older hardware?

Thank you in advance

Crawf.

---

### Post by Bucky Ball on 2014-07-28
Welcome. Hit shift a few times when you boot and that will bring up the grub list. If you want it permanently at boot, then open a terminal and:

```
sudo nano /etc/default/grub
```

Change these four lines to this, if they aren't like it already:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Press ctl+x, 'y' to save and exit. Then:

```
sudo update-grub
```

For some reason the list is not set to come up on new installs anymore, at least not the recent few I've done with 14.04.

---

### Post by crawf777 on 2014-07-28
Thank you very much for the useful information Bucky Ball.

That has answered my question.

---

### Post by Bucky Ball on 2014-07-28
All good. Please mark thread as solved to help others using the second link in my signature. Good luck with it. ;)

---

