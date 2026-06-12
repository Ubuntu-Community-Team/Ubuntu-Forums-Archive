---
title: "HPLIP Status Service fails - no system tray detected"
date: 2009-03-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-03-11
For several days I get the following error message on every start up:

[ATTACH]106142[/ATTACH]

And of course the HPLIP widget doesn't show up in the panel like it used to.

Anyone else notice this?

---

### Post by kansasnoob on 2009-03-11
Hmmmm, let me try that screenshot again:

[ATTACH]106146[/ATTACH]

---

### Post by The Cokeaholics on 2009-03-12
I had that as well but have not noticed it since latest updates.

When needed I started it manually.
```
sh -c "sleep 15; exec hp-systray"
```

Robert

---

### Post by kansasnoob on 2009-03-12
It's not a big deal. Printing still works OK.

I just like to see if something is repetitive enough to consider it a true bug before filing a bug report.

It's probably time for me to do a fresh install with Alpha 6 as I've modified, re-modified, and de-modified trying different desktops and window managers, etc.

Alpha 6 should be available within the next few hours.

---

### Post by kansasnoob on 2009-03-18
I've been away for a few days and see this has been resolved!

Jaunty's shaping up nicely!

---

### Post by pixolex on 2009-04-19
> **kansasnoob said:**
> I've been away for a few days and see this has been resolved!

Jaunty's shaping up nicely!

Updated yesterday do jaunty RC and I have exactly the same problem. How did you resolved that?

---

### Post by tgyorgyi on 2009-04-19
Same here: have this problem since updating to Jaunty RC three days ago. First it did not happen at every boot, but today I got this error message every time I switched on my machine.

---

