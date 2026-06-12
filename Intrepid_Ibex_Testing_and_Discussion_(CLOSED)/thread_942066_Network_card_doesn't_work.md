---
title: "Network card doesn't work"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Enigmatic on 2008-10-08
Have an Intel PCI-E 1000/1000 PT network card. I know about the e1000 bug, but I don't think I would have been affected as my motherboard has an ICH10 chipset.

As of a few kernels ago (maybe -3?) it no longer works (doesn't show as connected, can't pass any data).

Any ideas? It seems strange that relatively new hardware would not be supported.

---

### Post by chodo on 2008-10-08
From what I read the driver was deactivated because of this bug. It will be reactivated if the bug is fixed.

---

### Post by Enigmatic on 2008-10-08
Oh I see, so the card would still try to use the driver that is now blacklisted, though there would be no risk of doing so.

---

