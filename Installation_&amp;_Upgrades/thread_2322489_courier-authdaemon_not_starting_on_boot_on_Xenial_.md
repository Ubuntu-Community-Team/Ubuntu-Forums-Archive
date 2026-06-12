---
title: "courier-authdaemon not starting on boot on Xenial Xerus"
date: 2016-04-28
forum: Installation &amp; Upgrades
---

### Post by K3N8 on 2016-04-28
Hi,

I have installed courier-authdaemon but it is not starting on boot. I have to start it manually after boot in order te get it to work. Anybody else have the same issue?

Gr. Alexander

---

### Post by K3N8 on 2016-05-01
I've created a workaround.Edit /etc/rc.local:```
service courier-auth start
```

---

### Post by mörgæs on 2016-05-01
Good, then please mark the thread 'solved'.

---

### Post by K3N8 on 2016-05-01
> **mörgæs said:**
> Good, then please mark the thread 'solved'.

I would if it was solved, but it isn't.

---

### Post by EnkiduinNZ on 2016-05-06
> **K3N8 said:**
> I would if it was solved, but it isn't.

I found that the service courier-authdaemon is disabled for some reason. I enabled it but I've not rebooted so I don't know if it is fixed.

```
sudo systemctl enable courier-authdaemon
```

Cheers,

Cliff

---

### Post by TopicMapper333 on 2016-10-23
sudo systemctl enable courier-authdaemon

worked for me.  After rebooting, the daemon ran automagically.

---

