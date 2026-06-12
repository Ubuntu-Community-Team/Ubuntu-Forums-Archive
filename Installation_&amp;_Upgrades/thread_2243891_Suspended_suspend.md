---
title: "Suspended suspend"
date: 2014-09-11
forum: Installation &amp; Upgrades
---

### Post by John F on 2014-09-11
I am running Ubuntu on a 2006 Macbook (ever since it stopped accepting the latest Mac OS upgrades).  I have just upgraded to Ubuntu 14.04 which runs just fine except for one annoyance.  Every time it enters suspend mode either manually or on a preset, it locks up and I have to force a reboot.  Is there a way around this?  All I can do now is to shut down fully after every session.

---

### Post by egeezer on 2014-09-12
As far as I know, 14.04 uses uswsusp as the Suspend.  The way I got it to work reliably was to install
```
sudo apt-get install acpi-support uswsusp
```
Hope that helps!

---

