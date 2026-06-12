---
title: "Help: Can't release my packaging DB"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2006-06-24
Hi,
Initially, Adept worked flawlessly.
Yesterday, after connecting an external fax, I tried to install several fax related packages. One of them, I think (but are not sure) it's lprfax, erred as it didn't find the modem (it repeatedly asked to define the modem), and eventually I had to close Adept in the middle of he process.

Eversince, trying to run Adept (even to remove lprfax) I get a message that the packaging database is locked and I won't be able to apply any changes.

I tried to run dpkg --configure -a which brought me back into the lprfax configuration process, which was suck again.

Please advise to to regain Adept functionality ?

TIA
:D

---

### Post by aysiu on 2006-06-24
Maybe ```
sudo killall adept
sudo killall dpkg
``` might work?

---

### Post by mibadt on 2006-06-24
[QUOTE=aysiu]Maybe ```
sudo killall adept
sudo killall dpkg
``` might work?[/QUOTE]

Thanks, but these two didn't help either.

---

### Post by aysiu on 2006-06-24
Well, good luck.

I did a Google search for your error, and these were the only promising things that came up:
[http://kubuntuforums.net/forums/index.php?topic=6088.new](http://kubuntuforums.net/forums/index.php?topic=6088.new)
[http://www.ubuntuforums.org/showthread.php?t=149438](http://www.ubuntuforums.org/showthread.php?t=149438)

Unfortunately, of the three suggested approaches (which worked for the people in those threads), you've already tried two of them.

The one thing you haven't tried yet, though, is this: ```
sudo rm /var/lib/dpkg/lock
```

---

