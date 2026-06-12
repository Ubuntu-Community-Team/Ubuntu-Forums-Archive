---
title: "Javaldx Bug in Open Office"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NormanFLinux on 2009-09-28
Open Office 3.1.1 won't boot under Karmic. It will boot in the Terminal when sudo is invoked.

Running it non-privileged invokes a javaldx error and then the splash screen shuts down.

I have Sun Java JRE installed. It looks like a permissions problem in which OOO thinks it can run only in root. Does any one have any idea of how to make it run other than with sudo?

---

