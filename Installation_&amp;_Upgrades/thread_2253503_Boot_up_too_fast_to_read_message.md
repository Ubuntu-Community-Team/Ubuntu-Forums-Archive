---
title: "Boot up too fast to read message"
date: 2014-11-20
forum: Installation &amp; Upgrades
---

### Post by britesc on 2014-11-20
Hi,

I have upgraded from 12.04 LTS to 14.04 LTS on a HP DV72105 and now there is a message on boot up about looking at [http://.](http://.)...
Only problem I am partially sighted and it is too fast for me read before it disappears.
If anyone else has had this message appear could they tell me what it says or even better how to pause boot up so I can read the message myself.

I have incidentally lost all network connectivity on that laptop so it may be related.

Thanks and kind regards,

jB :cool:

---

### Post by ajgreeny on 2014-11-20
The first two lines of my /var/log/syslog are:-
```
Nov 20 09:06:54 Xubuntu rsyslogd: [origin software="rsyslogd" swVersion="5.8.6" x-pid="1065" x-info=[COLOR=#ff0000]"http://www.rsyslog.com"[/COLOR]] rsyslogd was HUPed
Nov 20 09:07:28 Xubuntu anacron[1223]: Job `cron.daily' terminated
```
Could that be what you see as the system boots?  I do not see any text when booting, but that is the file to look in to see what might be shown on your machine.

---

