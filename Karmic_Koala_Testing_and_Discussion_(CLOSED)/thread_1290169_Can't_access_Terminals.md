---
title: "Can't access Terminals"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by shadowhywind on 2009-10-13
Ever Since updating to kernal 2.6.31-12, I have not been able to access the terminal [alt+F1-F6]. During boot, I do get the splash screen, but afterwards (since I use nvidia drivers from their website) it defaults to terminal till i reinstall the drivers. If i use the stock driver 'nv' I can login,  but even when I try to switch to a terminal, its still just plain black. It is also happening on kernal 2.6.31-13. Anyone have any ideas?

---

### Post by taavikko on 2009-10-13
also happening here, with free radeon driver.
xorg/mesa related bug.

---

### Post by whoop on 2009-10-13
Isn't it this bug:
[https://bugs.launchpad.net/ubuntu/+bug/447692](https://bugs.launchpad.net/ubuntu/+bug/447692) ?

---

### Post by taavikko on 2009-10-13
> **whoop said:**
> Isn't it this bug:
[https://bugs.launchpad.net/ubuntu/+bug/447692](https://bugs.launchpad.net/ubuntu/+bug/447692) ?

most likely, thanks for the link.

---

### Post by shadowhywind on 2009-10-13
Thanks for the link, that was the bug that I am running into, thankfully theres a fix, might not be the "perfect" fix, but at least it makes the computer user-able again. Thanks again

---

