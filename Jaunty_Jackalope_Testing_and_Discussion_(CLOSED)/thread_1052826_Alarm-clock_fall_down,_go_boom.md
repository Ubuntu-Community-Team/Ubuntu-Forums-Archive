---
title: "Alarm-clock fall down, go boom"
date: 2009-01-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by IanW on 2009-01-28
Starting from menu, alarm-clock simply vanishes when adding a new alarm.
Starting from terminal gives the following error message:-
```

python: ../../src/xcb_lock.c:33: _XCBUnlockDisplay: Assertion `xcb_get_request_sent(dpy->xcb->connection) == dpy->request` failed.
Aborted (core dumped)

```

Bug filed [#321795](https://bugs.launchpad.net/bugs/321795).

---

