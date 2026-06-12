---
title: "get nvidia driver back after trying another kernel"
date: 2012-05-04
forum: Installation &amp; Upgrades
---

### Post by drhex on 2012-05-04
The following has happened:
[LIST=1]
[*]I install ubuntu 12.04 & proprietary nvidia driver
[*]That works, but has some issues after waking up from suspend
[*]I [submit a bugreport]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/994087") about those issues.
[*]Someone asks me to try again with a bleeding-edge kernel, so I do
[*]installing the nvidia driver with the new kernel fails
[*]I reboot with the standard kernel 
[*]It no longer has an nvidia driver, so I try to install it
[*]That fails too, and the logfile implies that it is still trying to add the nvidia driver to the bleeding edge kernel
[/LIST]
So, how do I get the nvidia driver back into the standard kernel  (trying via system settings/additional drivers) ?

---

### Post by kc1di on 2012-05-04
```
sudo apt-get purge new kernel
```
then reinstall nvidia via additional drivers.

---

