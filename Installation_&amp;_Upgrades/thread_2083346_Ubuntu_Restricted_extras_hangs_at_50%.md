---
title: "Ubuntu Restricted extras hangs at 50%"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by Houmie on 2012-11-12
HI,

Right after it asked me to accept Microsoft EULA, I did so and now it hangs for along time at 50%. I can't even cancel and retry again and neither can I install anything else. Since they wait in the pipeline for their turn.

What do you suggest please? I even killed the process and restart. It is still there at 50% pending...

Ubuntu 12.10

Thanks,

---

### Post by ibjsb4 on 2012-11-12
Is this the software center?  Try installing it in terminal, should at lease give you some errors to help troubleshoot.

---

### Post by philinux on 2012-11-12
> **Houmie said:**
> HI,

Right after it asked me to accept Microsoft EULA, I did so and now it hangs for along time at 50%. I can't even cancel and retry again and neither can I install anything else. Since they wait in the pipeline for their turn.

What do you suggest please? I even killed the process and restart. It is still there at 50% pending...

Ubuntu 12.10

Thanks,

open a terminal, ctrl + alt + t, copy and paste the command in and report back.

```
dpkg --configure -a
```

---

### Post by Houmie on 2012-11-13
> **philinux said:**
> open a terminal, ctrl + alt + t, copy and paste the command in and report back.

```
dpkg --configure -a
```

Thanks. After a second reboot, it had disappeared from the pending.
I didn't trust it though and uninstalled it. During the uninstall process it crashed and submitted a bug report, after another try it finally managed to uninstall.

Then I tried to install it again and it worked this time.

---

