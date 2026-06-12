---
title: "Ubuntu 16.04: unattended-upgrades replaced my modified apt-daily.timer"
date: 2016-06-13
forum: Installation &amp; Upgrades
---

### Post by y-jon-4 on 2016-06-13
I modified /lib/systemd/system/apt-daily.timer to restrict unattended-upgrades to "The Wee Hours" in my local time zone, on a server running UTC.  It appears as if an upgrade package to apt itself or its utilities replaced apt-daily.timer on June 2.

Is there a better way to do this?  Or should I report this as a bug to Ubuntu?

Here is what I changed:
```
[Timer]
OnCalendar=*-*-* 10:00
RandomizedDelaySec=45min
AccuracySec=5min
Persistent=false
```

---

### Post by antonio-nacanare on 2016-06-18
Hello y-jon-4
The files under /lib/systemd/ will be updated when the packages are upgraded.
If you want to customize a service, you need to create a file under /etc/systemd

In your case you need to save your edits as /etc/systemd/system/apt-daily.timer

Hope this helps

Antonio

---

### Post by y-jon-4 on 2016-06-18
Fabulous!  Just what I needed to know.

Thank you so much, Antonio!

---

