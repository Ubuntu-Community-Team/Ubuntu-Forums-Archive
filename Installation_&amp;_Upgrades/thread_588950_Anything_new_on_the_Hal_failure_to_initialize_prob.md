---
title: "Anything new on the Hal failure to initialize problem"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by kloudy on 2007-10-23
Does anyone have any new possibilites for the Hal failure to initalize at startup problems?

I hate to invest more time on Gutsy application installations if I may have to revert to Feisty. to get a working system again.

Thanks,
Levi

---

### Post by computer_user_au on 2007-10-31
As a temp fix, try command:
```
sudo /etc/init.d/dbus restart
```

The check out the fix in thread:
[http://ubuntuforums.org/showthread.php?t=583940&highlight=HAL]("http://ubuntuforums.org/showthread.php?t=583940&highlight=HAL")

Good luck.

---

### Post by computer_user_au on 2007-11-01
Also, check out:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931")

I manually did the following on my system:

```
sudo mv /etc/rc2.d/S50dbus /etc/rc2.d/S12dbus
```

rebooted and the system worked, no more "Failure to initialize HAL" error messages and my network connection is working well.

---

### Post by Flying caveman on 2007-11-10
```
sudo /etc/init.d/dbus restart
```

thanks that worked for me, I thought i was going to have to re-install.

I thought there was a little to much network activity and my cpu was running full speed, so i  started shuting things down in the system monitor.  

On the next reboot I had the hal failed to initialise, the option to suspende and resume were gone, and worst of all my sytem wouldn't let my do any admin stuff like configure my network card, or get into session manager(services).  

After I ran that command I could get into session manager and select dbus to start saved the session and rebooted everything is fine now.

---

