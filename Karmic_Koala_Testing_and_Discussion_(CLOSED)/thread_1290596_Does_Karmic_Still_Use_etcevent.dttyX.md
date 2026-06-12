---
title: "Does Karmic Still Use /etc/event.d/ttyX?"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by JamieKitson on 2009-10-13
Hi,

The short story:

I cannot seem to get /etc/event.d/tty[1-6] to do anything, even mucking up the file does not have any effect.

The long(er) story:

Before my Karmic upgrade my /etc/event.d/tty1 script (below) would do an autologin using mingetty, now it doesn't work.

```

start on stopped rc2
start on stopped rc3
start on stopped rc4
start on stopped rc5

stop on runlevel 0
stop on runlevel 1
stop on runlevel 6

respawn
exec /sbin/mingetty --autologin jamie tty1
```Does Karmic still use these files?

Cheers, Jamie

---

### Post by JamieKitson on 2009-10-13
Ah-ha:

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/402759](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/402759)

/etc/event.d/ttyX scripts should be migrated to /etc/init/ttyX.conf

Not sure how to refresh these without a reboot.

---

