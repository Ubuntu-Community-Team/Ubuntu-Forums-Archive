---
title: "ATi card not detected in Ibex"
date: 2008-07-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Mazza558 on 2008-07-06
Just upgraded from Hardy, and whilst everything else is working fine, Ibex can't detect my ATi card - it doesn't show up in the Hardware Drivers tool, and I've tried installing fglrx manually, but no luck. Note that I can't use the .26.3 kernel as it results in a black screen (no Ubuntu logo or anything). Laptop details in signature.

What's up?

---

### Post by psyke83 on 2008-07-06
> **Mazza558 said:**
> Just upgraded from Hardy, and whilst everything else is working fine, Ibex can't detect my ATi card - it doesn't show up in the Hardware Drivers tool, and I've tried installing fglrx manually, but no luck. Note that I can't use the .26.3 kernel as it results in a black screen (no Ubuntu logo or anything). Laptop details in signature.

What's up?

You're using a [development]("http://ubuntuforums.org/showthread.php?t=838315") [release]("http://ubuntuforums.org/showthread.php?t=842777").

---

### Post by Mazza558 on 2008-07-06
> **psyke83 said:**
> You're using a [development]("http://ubuntuforums.org/showthread.php?t=838315") [release]("http://ubuntuforums.org/showthread.php?t=842777").

Whoops, didn't notice I was using a development release! Must have accidentally done a "sudo update manager -d", accidentally pressed the "Upgrade" button and left my Laptop for an hour to find myself on Ibex! It's an easy mistake ... thanks for the information!

Either way, I thank you for at least providing the information. Looks like it's still way too early for anything remotely usable. If I recall correctly, Hardy's fglrx drivers came in earlier than this, but I'm probably wrong.

---

### Post by Nullack on 2008-07-06
No the closed binaries arent in the repos yet. Im on NVIDIA and that required manual install of a patched driver.

---

### Post by plun on 2008-07-06
Please take a look at this thread

[http://ubuntuforums.org/showthread.php?t=845236](http://ubuntuforums.org/showthread.php?t=845236)

RAOF explains the situation and the open source driver should be fine...

---

