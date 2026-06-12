---
title: "snap store"
date: 2022-09-23
forum: Installation &amp; Upgrades
---

### Post by gordie692 on 2022-09-23
after I installed 20.04 I updated the system rebooted went software center updated that all but snap store keeps saying pending never had this before

---

### Post by ian-weisser on 2022-09-23
Ubuntu Software (snap-store) cannot update itself. Like all snap applications, snaps-store gets updated by snapd when the application is not running.

But closing the Ubuntu Software window is not enough to actually Quit snap-store, hence the notification.

Try:
```

snap-store --quit
sudo snap refresh

```

Now you can re-open Ubuntu Software (if you want).

---

### Post by gordie692 on 2022-09-23
Thanks Ian all good now I have had this before Ubuntu has always great all I run is Ubuntu hate W10

---

### Post by TheFu on 2022-09-24
Please use the 'thread tools' button near the top of the page and mark this thread as "SOLVED" so people don't waste time and so people looking for answers know it has been solved and could help them too.

---

### Post by cigtoxdoc on 2022-10-05
After I execute the commands given above, it immediately tells me that I have 12 days left to fix the problem.

---

### Post by ian-weisser on 2022-10-06
> **cigtoxdoc said:**
> After I execute the commands given above, it immediately tells me that I have 12 days left to fix the problem.

Run "sudo snap refresh snap-store"
That will return another notification pop-up with the PID of the blocking process.
Kill that process.
Then run "sudo snap refresh"

If that doesn't fix it, then please provide the complete, exact output.

---

### Post by cigtoxdoc on 2022-10-06
Thank you.  It worked.

---

