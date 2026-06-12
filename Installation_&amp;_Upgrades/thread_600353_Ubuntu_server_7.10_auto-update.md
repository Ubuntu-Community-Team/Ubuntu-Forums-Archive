---
title: "Ubuntu server 7.10 auto-update"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by ABX on 2007-11-02
How can I setup my ubuntu server to perform automatic updates?

---

### Post by peachy on 2007-11-02
you *could* add the following entry to root's crontab

```
apt-get update && apt-get --yes upgrade
```

But then you are blindly updating every package on your server as and when it becomes available

---

### Post by ABX on 2007-11-02
Yeah, this is what I just did 30 minutes ago. :)

But my backup job is scheduled 5 hours before this. :)

---

