---
title: "unattended-upgrades start time"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by ygoe on 2011-05-05
Hi,

I have installed unattended-upgrades on Ubuntu 10.4. It runs every morning at 7:38 +/- 2 minutes. I'd like to have it run earlier, like between 4 and 5 o'clock. I've found that unattended-upgrades is run by the apt script which is in cron.daily. Cron.daily is configured to run at 4:10, but I always get e-mails (and log entries) at the later time. Why doesn't cron.daily start at the time configured in /etc/crontab?

Here's the crontab line:

10 4    * * *    root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

There is no line that runs something at 7:xx.

Here's the syslog filtered by facility cron and message with "daily":

Zeit    Facility    Prio    Programm    Meldung
2011-05-05 04:10:01.467979    Cron    Info    CRON    (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
2011-05-05 07:30:01.249343    Cron    Notice    anacron    Will run job `cron.daily' in 5 min.
2011-05-05 07:35:01.250203    Cron    Notice    anacron    Job `cron.daily' started
2011-05-05 07:35:01.254917    Cron    Notice    anacron    Updated timestamp for job `cron.daily' to 2011-05-05
2011-05-05 08:05:58.543745    Cron    Notice    anacron    Job `cron.daily' terminated

---

### Post by ygoe on 2011-05-12
Here's the solution:
[http://askubuntu.com/questions/36971/at-what-time-does-cron-execute-daily-scripts](http://askubuntu.com/questions/36971/at-what-time-does-cron-execute-daily-scripts)

The daily cron configuration is a bit complicated. The actual time was set in a different file. Now it works as configured/expected.

---

### Post by auftable on 2011-11-17
I just found this thread and am adding for everyone, who finds this post later, that there is a sleep function in unattended-upgrades that seems to add randomly up to 30 minutes delay so that the server aren't used extensively at the same time.

---

