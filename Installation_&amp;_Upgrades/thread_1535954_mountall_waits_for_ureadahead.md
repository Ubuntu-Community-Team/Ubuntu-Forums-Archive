---
title: "mountall waits for ureadahead?"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by doixanh on 2010-07-21
I'm in the progress of optimizing lucid for faster boot.

This is my current result:
[img]http://dnxp.comule.com/images/dxlaptop-lucid-20100721-1-15.62s.png[/img]

As can be seen, mountall waits for ureadahead to finish then it starts.
I'm wondering why we can't run ureadahead and mount at the same time (because mounting doesn't read from hdd much).

I change /etc/init/ureadahead.conf like this
Original
```
exec /sbin/ureadahead --daemon
```

Modified
```
exec /sbin/ureadahead --daemon &
```

and the result is :
[img]http://dnxp.comule.com/images/dxlaptop-lucid-20100721-8.png[/img]

As can be seen, mountall waits ureadahead to finish before actually calls "mount".

My question is, is there any way to force mountall to call "mount" before ureadahead finishs its job?

---

