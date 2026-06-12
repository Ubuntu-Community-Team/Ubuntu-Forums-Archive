---
title: "libhal_acquire_global_interface_lock"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by Drone4four on 2008-06-23
Ubiquity won't start.  Here is the command with sudo:
```

ubuntu@ubuntu:~$ sudo ubiquity
error: libhal_acquire_global_interface_lock: org.freedesktop.Hal.Device.InterfaceAlreadyLocked: The interface org.freedesktop.Hal.Device.Storage is already exclusively locked either by someone else or it's already locked by yourself
ubuntu@ubuntu:~$ 

```

Entering portions of the above error messages into the Google search did not produce useful results.  

Where do I go from here?

---

### Post by Drone4four on 2008-06-23
Solved: Ubiquity was loaded, hiding beneath a series of full screen terminals.  Ubuntu is installing as I write this forum thread. =D

---

