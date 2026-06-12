---
title: "A broken package in adept (dpkg) installation queue"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by agrabah on 2007-05-11
I installed a faulty .deb package, and i didn't install correctly (the postinstall script didn't run). It didn't show up among the installed packages, but everytime I try to install something via adept (or apt-get), it automatically tries to configure it, and crashes again. I tried to uninstall it manually (by running the pre-uninstall script), and it seemed to have been uninstalled. No dice. Now a "postinst" script is pending (which apt-get and adept try to run, but it crashes; oddly enough when I give:

```
dpkg --configure -a 
```

there seems to be no packages pending for install.

The package does not show in the status file in /var/lib/dpkg. How can I delete the queue of pending packages manually, or just make this package go away? 

btw. I use Kubuntu Feisty.

Thanks,

 Tine

---

