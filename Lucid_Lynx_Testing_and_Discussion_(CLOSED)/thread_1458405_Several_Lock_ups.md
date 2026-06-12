---
title: "Several Lock ups"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by John Marter on 2010-04-20
I have had 5 lockups in the last week.  What information would be useful in diagnosing this?

In two cases, it happened while switching users.  Once it happened while unpowering and repowering a USB scanner.  Once it happened while maximizing an evince window.

The last two times, I took a picture of my old serial text terminal which was running top and froze up at the same time as the desktop.

When the lockup occurs the screen typically goes blank and the only recovering is the reset button on the computer.

---

### Post by John Marter on 2010-04-20
Here is the screen shot of top when the lock-up occurred maximizing evince.

---

### Post by Reiger on 2010-04-20
Try dmesg | tail -n 20. Perhaps things segfault like mad?

I noticed that if enable KMS, and set pci=nomsi on boot; the whole system seems a lot more fragile with segfaults occuring in a shared Qt dbus library... That wouldn't be so bad, if at least the damage was limited to only one process. But if, for instance VLC segfaults, the problem will next cascade to Opera, and then take out my X session.

---

