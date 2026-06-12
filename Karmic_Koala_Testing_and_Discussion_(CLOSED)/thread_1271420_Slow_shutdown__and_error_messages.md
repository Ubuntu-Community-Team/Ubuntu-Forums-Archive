---
title: "Slow shutdown  and error messages"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andresmh on 2009-09-20
Others have reported the strange and innocuous error messages when booting. I also see errors when shutting down the system. In fact the whole shutdown  process has slowed down significantly in comparison to Jaunty (at last on my laptop).

Since Alpha 6 I get these kind of messages:
```

sierra ttyUSB0: resubmit read urb failed. (-1)
rc main process stopped by STOP signal
rc main process stopped by CONT signal

```

Which is OK since I assume they will get fixed. But this one baffles me as it has been here since the first Alpha and it's not really an error, it simply sits there waiting for a while when showing:

```

 [2383.977568] Restaring system

```

The number changes from one restart to another.

Where in launchpad should this problems be submitted? Is there a bug open for it already? I couldn't find one.

See attached image for an example.

---

### Post by VMC on 2009-09-20
Are you current on updates? I find it just the opposite. The shutdown happens so fast I'm sure I will have fsck issues on next boot, which I don't.

It could be several things. Have you checked your log files (/var/log/ or System>Admin>LogFileViewer)for further help. What is your system specs?

---

### Post by FuturePilot on 2009-09-20
I'm getting those too on a fresh install. Looked for a bug report but I couldn't find one.

---

### Post by alexmurray on 2009-09-20
Looks like this bug: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/401333](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/401333)

---

### Post by Framli on 2009-09-20
Same here :
- slow shut down (20 seconds or so)
- rc main process stopped and continued again and again.

But I don't have these two messages :
```
sierra ttyUSB0: resubmit read urb failed. (-1)
...
[2383.977568] Restaring system
```

This is weird because time to time I have a nice and "normal" shut down.

Edit : Bug status = Won't Fix

---

### Post by trulan on 2009-09-20
I agree shutdown is often quite slow, especially on a re-start.  According to the bug linked above that has nothing to do with the rc stop/rc cont messages.

And, as was stated above, sometimes I get a nice clean shutdown, splash screen and all.

---

