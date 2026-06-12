---
title: "ubuntu install, dies on initial reboot"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by deuce868 on 2006-06-16
Installed Ubuntu on a Dell 370N desktop with a 320gb SATA disk. Install went fine. Ejected disk and did a reboot. On reboot it gets to:
Starting periodoc command scheduler... [ok]
Running local boot scripts (/etc/rc.local)	[ok]

It just hangs there. When I go to the second console and log in I can tail /var/log/syslog. The last item there is:
(CRON) INFO (Running @reboot jobs)

It's dead after that. I can't seem to find out what reboot job it is hanging at. I have some files in the /var/log/installer directory. I can a load of things in the /var/log/installer/syslog file such as 
prebaseconfig: info: running /usr/lib/prebaseconfig.d/94save-log Anyone have any ideas as to where I'm going wrong here?

Thanks for the help.

---

