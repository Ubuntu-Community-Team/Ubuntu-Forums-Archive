---
title: "Can't upgrade due to dbus not configuring right."
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by mail2345 on 2010-01-16
So during the upgrade from Ibex to Koala, the updater hung at
```

Setting up dbus (1.2.16-0ubuntu9) ...
The system user `messagebus' already exists. Exiting.

```
I then ctrl-ced after some time, and when I got back the update wasn't done due to errors. I tried dpkg --configure -a, and the same issue popped up.
Doing some research, I've heard that adding messagebus to the messagebus group would fix it, but it's already in that group.
How would I get this issue solved?
EDIT:
As a note, I'm doing this over ssh.

---

