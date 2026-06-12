---
title: "Restoring broken ubuntu system?"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by Cherish76 on 2008-09-30
Hi,

I was installing gtk and by mistake I removed GLIB and now ubuntu doesn't start Xserver, the network connections are lost. I have tried reinstalling the GLIB but still the problem exists. So how to restore the system? I can log in to the system in console mode and all data is intact.

Many thanks,
-Ram

---

### Post by Sef on 2008-09-30
Try this code:

```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

### Post by Cherish76 on 2008-10-01
Hi,

Thanks for the reply. I tried running that command but the update failed and eventually the installing the ubuntu-desktop. I see the network connection is lost as ifconfig is outputting only the loopback details. Hence the apt-get update is not able to resolve the website from which it should fetch the data.

Now the new question is how to restore the network interface/connection?

Many thanks,
-Ram

---

### Post by Cherish76 on 2008-10-01
I resolved the network issue and then tried updating and installing the ubuntu-desktop. Everything works fine now...thanks a lot for your help.

Cheers,
-Ram

---

