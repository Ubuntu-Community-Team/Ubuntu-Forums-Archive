---
title: "hello all, i am facing a problem while poweroff or restart of the ubuntu"
date: 2020-06-21
forum: Installation &amp; Upgrades
---

### Post by raghuramabl on 2020-06-21
when i do power off or restart in Ubuntu 20.04 i am stuck in a screen and after some times some code 
starts running continuously but doesn't power off why does this kind of thing happens
i am dual booted Ubuntu with windows but i am not getting this type of problem

i thought maybe may be i have done error while installing Ubuntu but no i did the same thing in my laptop it is 
doing well

---

### Post by VMC on 2020-06-21
There is  good explnation on this very subject, but I can't find it now. Just a couple of months.
In the meantime I use this and no longer have that long wait:
```
sudo sed -i 's/\#DefaultTimeoutStartSec=90s/DefaultTimeoutStartSec=10s/' /etc/systemd/system.conf
sudo sed -i 's/\#DefaultTimeoutStopSec=90s/DefaultTimeoutStopSec=10s/' /etc/systemd/system.conf
```

Here's a bug report on the subject:
[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1457400)

---

