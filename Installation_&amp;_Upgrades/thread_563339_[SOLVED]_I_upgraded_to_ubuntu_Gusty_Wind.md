---
title: "[SOLVED] I upgraded to ubuntu: Gusty Wind"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by wil313 on 2007-09-29
And now when I go to update I get the message:

E: tzdata: subprocess post-installation script returned error exit status 10
E: util-linux: dependency problems - leaving unconfigured

---

### Post by Pumalite on 2007-09-29
Save data and do a clean install.

---

### Post by wil313 on 2007-09-29
Ugh, you mean completely re install Ubuntu?

---

### Post by Pumalite on 2007-09-29
No less.

---

### Post by wil313 on 2007-09-30
**[SIZE="4"][COLOR="Red"]Please Note:[/COLOR][/SIZE]**

I re-installed Edgy, then upgraded and had the same problem with Tzdata, if you have this problem there is **_NO_** need to re-install, just follow this simple step:

Go to synaptic package manager, find tzdata and COMPLETELY remove it. Then reinstall tzdata when it has finished, then run update manager. Then you are good to go.

Thanks

---

### Post by Pumalite on 2007-09-30
Thank you for posting the solution, I will bookmark it.

---

