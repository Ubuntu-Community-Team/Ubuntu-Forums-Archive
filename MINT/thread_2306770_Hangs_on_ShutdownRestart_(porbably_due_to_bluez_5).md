---
title: "Hangs on Shutdown/Restart (porbably due to bluez 5)"
date: 2015-12-18
forum: MINT
---

### Post by Jility on 2015-12-18
Dear Community,
I just recently upgraded (completely new installation) to Mint 17.3 (Ubuntu 14.04 based). Also I got a new Logitech MX Anywhere 2 mouse and because bluez 4 does not support it, I had to upgrade to bluez 5.35. 
However, after I managed to get my mouse working, I could not restart or shutdown normally anymore. Indeed, not at all.
```
sudo shutdown -P now
``` nor ```
sudo shutdown -h now
``` is working.
I attached the message that I have got when restarting.
I hope somebody can help me fix this problem, as shutting down manually is probably not the best for the notebook (Acer V5-573G).
Best, Felix

---

### Post by saltydingo on 2016-10-28
I think I've got the [same problem]("https://ubuntuforums.org/showthread.php?t=2341469") - have narrowed it down to the bluetooth service, but don't know how to fix it.

---

### Post by z0rn on 2016-12-30
> **saltydingo said:**
> I think I've got the [same problem]("https://ubuntuforums.org/showthread.php?t=2341469") - have narrowed it down to the bluetooth service, but don't know how to fix it.

Please share your solutions. I also struggle with this problem.

---

### Post by howefield on 2016-12-30
Moved to the "*MINT*" forum.

---

