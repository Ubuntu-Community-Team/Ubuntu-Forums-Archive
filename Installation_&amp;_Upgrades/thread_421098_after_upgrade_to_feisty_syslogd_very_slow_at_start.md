---
title: "after upgrade to feisty: syslogd very slow at startup"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by zasf on 2007-04-24
Hi, I upgrade to feisty from edgy, everthing seemed to be ok except a few glitches ([more in this post]("http://ubuntuforums.org/showthread.php?t=403540")), but now I have another problem: syslogd at startup is very very slow.. it takes 20 sec to start, it doesn't show any problems since it says "OK", but then the system is very slow for the next 10 min, if I open any apps they take forever to show up. After 10 minutes, the comp works as expected.. how can I solve this? Where should I look? Any ideas?

Thanks,
Matteo

---

### Post by zasf on 2007-04-24
I installed syslog-ng wich replaced syslogd and klogd, it seems to work ok now.

---

