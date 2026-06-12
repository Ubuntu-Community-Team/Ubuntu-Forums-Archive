---
title: "disable log writing"
date: 2007-03-18
forum: Installation &amp; Upgrades
---

### Post by jaripetteri on 2007-03-18
How I disable ubuntu edgy to write all those log files its generating? I have laptop running only on Compact Flash and I'm trying to minimize writes on disk...

---

### Post by kidders on 2007-03-18
Hi there,

If you really wanted to disable your system logs, I suppose you could reconfigure /etc/syslog.conf so it didn't bother writing out any received messages. Doing that is _**absolutely not recommended**_ though.

If what you're interested in doing is reducing disk accesses, you should probably consider storing /var/log in RAM, rather than on flash memory. You could then reconfigure logrotate to write your logs to disk all in one go (on shutdown, for example). Another alternative would be to write log data to another computer's syslog, or perhaps a remote MySQL database.

One thing worth noting is that syslog won't necessarily give you 100% coverage of all your log files, since applications aren't *obliged* to use the facility. Samba is a common example of one that tends not to, unless you make it. Whatever solution you choose, you'll have to experiment a bit to make sure you're intercepting _all_ your logs.

I hope that helps.

---

### Post by Kateikyoushi on 2007-03-18
System > administration > services, there you can find two logging services like klogd and syslogd, that would be a good place to start.

---

