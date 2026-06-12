---
title: "opendkim will not start"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by jcarson99 on 2013-02-21
Hi,

 I am running Ubuntu Server 12.04. LTS 64 bit.

When I try to start opendkim nothing happens. There is no error displayed on screen .

Anyone know why it won't start or how to fix it.

Thanks

---

### Post by jcarson99 on 2013-02-21
Looking through my mail.log I came across this...

> Feb 21 14:00:18 vm opendkim[29295]: OpenDKIM Filter v2.5.2 starting (args: -x /etc/opendkim.conf -u opendkim -P /var/run/opendkim/opendkim.pid -p local:/var/run/opendkim/opendkim.sock)
Feb 21 14:00:48 vm opendkim[29295]: OpenDKIM Filter: mi_stop=1
Feb 21 14:00:48 vm opendkim[29295]: OpenDKIM Filter v2.5.2 terminating with status 0, errno = 0


---

### Post by jcarson99 on 2013-02-21
Found the same thing in syslog

> FFeb 21 14:00:18 vm opendkim[29295]: OpenDKIM Filter v2.5.2 starting (args: -x /etc/opendkim.conf -u opendkim -P /var/run/opendkim/opendkim.pid -p local:/var/run/opendkim/opendkim.sock)
Feb 21 14:00:48 vm opendkim[29295]: OpenDKIM Filter: mi_stop=1
Feb 21 14:00:48 vm opendkim[29295]: OpenDKIM Filter v2.5.2 terminating with status 0, errno = 0


---

### Post by jcarson99 on 2013-02-21
Uninstalled then reinstalled. Not sure what was wrong but it's working now.

Here is the configuration I am using (/etc/opendkim.conf)...

> Syslog                  yes
SyslogSuccess           yes
Mode                    s
Canonicalization        relaxed/simple
Domain domain.com
Selector                mydkim
KeyFile                 /etc/opendkim/mydkim.private
Socket                  inet:8891@localhost
ReportAddress [EMAIL="user@domain.com"]user@domain.com[/EMAIL]
SendReports             yes
PidFile /var/run/opendkim/opendkim.pid


---

