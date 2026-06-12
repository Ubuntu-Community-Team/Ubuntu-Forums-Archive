---
title: "Ubuntu proceeds with shutdowns even if you plug in your AC adapter"
date: 2009-05-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-05-16
If Ubuntu throws me a "low battery - 5 minutes left" warning and I plug in my AC adapter within the next 30 seconds or so, Ubuntu will insist on shutting down when the 5 minutes have passed.

My AC adapter functions fine, so I suspect that Ubuntu's power management is acting up again.

---

### Post by 23meg on 2009-05-16
The following may help you pinpoint the issue:

[https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)
[https://wiki.ubuntu.com/DebuggingGNOMEPowerManager](https://wiki.ubuntu.com/DebuggingGNOMEPowerManager)
[https://wiki.ubuntu.com/DebuggingHal](https://wiki.ubuntu.com/DebuggingHal)

Also remember to do a search for existing bugs on the bug tracker.

---

