---
title: "Cannot boot after upgrade to Hardy"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by crash369 on 2008-07-17
I downloaded and burned Hardy 8.04 32bit install CD on the day Hardy came out.  My system refused to boot from the liveCD.  One of those SATA issues.  I tried some of the more common "fixes": irqpoll, no-acpi-blabla, etc. at boot... none of that worked.  It was frustrating, so I just left it alone.

Last week, maybe because I thought 8.04.**1** would somehow fix everything, or maybe because I got tired of looking at the "upgrade available" message, or maybe because the stars aligned just right for me to have a retarded moment, I went ahead with the apt upgrade of my system from 7.10 (which was working sort of fine!) to 8.04.1. Mistake! :(

The upgrade went fine.  On first reboot, I got the busybox.  Second reboot actually got me to GDM login page, but when I logged in, I got the ever familiar "HAL: failed" messages.  I have learned that to fix this issue in 7.10, I had to reboot, wait about 5 minutes at the login screen, and THEN log in.  I rebooted for the third time...

Now every reboot results the progress bar loading half-way, then dumping me to a screen with the following messages:

(I've cut out some of the ones that had [OK] next to them)
(The messages are approximate only, since I had to write them down on a postit)

```
AppArmor - usr.sbin.mysqld force complain mode
...
Config net interface [OK]
Setting sensor limits 
init: rc3 main process killed by TERM signal
Stopping GNOME display manager gdm
Checkig battery state
```

It stops there... weird since, this is a desktop without a battery.  I do not get a shell, but I can switch to TTY1, which will let me login and start gdm.

The problem is that if I do that, none of the services that were supposed to be started by rc3 (dbus, ssh, apache, mysql, cupsys, etc.) are started.

Please help.  I've tried searching for a solution, but I have yet to find anyone with a similar problem.

P.S. - One more possibly related thing... Once in GNOME, if I go to System->Admin->Services and click on [Unlock], the system does not recognize my password...

---

