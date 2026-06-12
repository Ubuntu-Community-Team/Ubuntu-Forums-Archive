---
title: "SSH connect delay."
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hikaricore on 2009-07-24
I've been noticing since the update to Karmic a few days ago that ssh
connections take between 8-12 seconds to establish after password entry.
This occurs remotely as well as locally and as of yet I've not been able
to find an exact cause for it however I expect landscape-sys may be to blame.
Just looking for input to see if anyone else has noticed similar behavior.

Thanks in advance.  ^_^

---

### Post by taavikko on 2009-07-24
landscape isn't installed by default...
```
taavikko@hp-dv5:~$ dpkg -l landscape\*
No packages found matching landscape*.
```


I'm not seeing this behaviour in my setups.
From 9.10 Gnome ssh -> 9.10 KDE through dydns nameserver so the connection travels quite a bit...

---

### Post by hikaricore on 2009-07-24
Landscape was installed by default at some point, this is an upgrade from Jaunty
which I may have also upgraded from Intrepid and from Hardy.  :p
I'll try removing it and see if that speeds things up a bit.

---

### Post by Rocket2DMn on 2009-07-26
Thanks for the heads up about landscape, I wasn't able to establish a connection at all until I installed landscape-common.

---

### Post by psyke83 on 2009-07-26
It may also be the avahi daemon slowing down dns lookups. See [this]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940") bug.

---

### Post by Nyoro on 2009-07-27
Maybe the ssh server(s) are having trouble doing reverse lookup of your hostname. See

[http://aldatacom.ro/index.php?option=com_content&id=33&task=view&Itemid=31&mosmsg=Thanks+for+your+vote](http://aldatacom.ro/index.php?option=com_content&id=33&task=view&Itemid=31&mosmsg=Thanks+for+your+vote)!

---

### Post by superfoor on 2009-07-27
We had a problem much like yours with some severs. It ended up being a screwed up dns setting.

---

### Post by hikaricore on 2009-07-28
Thanks for the input but that's not the cause.
Upon testing I found that temporarily removing landscape-sys resolved the issue..
Now the question is, why is landscape hanging for so long?

---

