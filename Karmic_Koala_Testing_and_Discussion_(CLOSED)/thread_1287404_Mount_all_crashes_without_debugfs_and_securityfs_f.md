---
title: "Mount all crashes without debugfs and securityfs for custom kernels"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kristian on 2009-10-10
After my last upgrade I need to have debugfs as well as securityfs compiled into my kernel or else mountall dies. Anyone else that has observed this behaviour?

---

### Post by VMC on 2009-10-10
> **kristian said:**
> After my last upgrade I need to have debugfs as well as securityfs compiled into my kernel or else mountall dies. Anyone else that has observed this behaviour?

I filtered through the log viewer and couldn't see any messages relating to mountall. Where do you see this indication, on boot up?

---

### Post by kristian on 2009-10-10
When I boot up with a kernel lacking debugfs and securityfs the boot process stalls and spawn a emergency shell right after mountall outputs it's errors about not being able to mount /sys/kernel/debug and /sys/kernel/security.

---

