---
title: "Stopping Oracle 10g daemon"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by jide on 2008-01-30
Hello,
I recently installed Oracle 10g in Gutsy. During the installation, I made it to start automatically during booting but now I want to start it manually. The question is how do I remove the Oracle deamon so that it does not start when Gutsy starts.

Thanks,
Jide

---

### Post by Waappu on 2008-02-04
Hi

if you install BUM, you can set so Xe not start automatic. But there is other way I'm sure. But with BUM you can control other startup things as well
```
sudo aptitude install bum
```

---

### Post by Waappu on 2008-02-04
Hi

Find other solution here
[http://www.debian-administration.org/articles/430](http://www.debian-administration.org/articles/430)

Disable autostart```
chmod -x /etc/init.d/oracle-xe
```
and enable ```
chmod +x /etc/init.d/oracle-xe
```

---

