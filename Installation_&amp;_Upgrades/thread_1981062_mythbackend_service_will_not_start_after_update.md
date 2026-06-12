---
title: "mythbackend service will not start after update"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by Gaute91 on 2012-05-16
Hello!
I resently updated my mythtv installation from 0.24 to 0.25. But now mythbackend wont start at boot, and when i type service mythbackend restart i just get:
```
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.34" (uid=1000 pid=5630 comm="start mythtv-backend ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

```
But when i start mythbackend normally its start and runs like a charm...
Does anyone have any idea what this can be?

Thanks

---

