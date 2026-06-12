---
title: "Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2020-09-10
forum: Installation &amp; Upgrades
---

### Post by dorpm on 2020-09-10
Hi,
on my box I have a cronjob for updates:
```
/usr/bin/apt update && /usr/bin/apt -y upgrade
```
But /var/log/apt/history.log tells me that dpkg reports an issue:
```
Start-Date: 2020-09-09  22:00:17
Commandline: /usr/bin/apt -y upgrade
Upgrade: smartmontools:amd64 (6.5+svn4324-1, 6.5+svn4324-1ubuntu0.1)
Error: Sub-process /usr/bin/dpkg returned an error code (2)
End-Date: 2020-09-09  22:00:17
```
Nevertheless when I start the same command on the console for some reason the same command works:
```
Start-Date: 2020-09-09  22:12:53Commandline: apt upgrade
Requested-By: flori (1000)
Upgrade: smartmontools:amd64 (6.5+svn4324-1, 6.5+svn4324-1ubuntu0.1)
End-Date: 2020-09-09  22:12:55
```
Any idea?

---

### Post by TheFu on 2020-09-12
**apt** shouldn't be used in scripts.  It even says that.  
> WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
I'd suspect the problem is caused because cron doesn't provide a full environment and the 'apt' tool prefers it.

You can always use **apt-get** instead, but I wouldn't automate these things.  I've had apt/apt-get/aptitude used in automatic tasks create systems that don't boot and I didn't see the errors before making it worse a few days later by rebooting.  Once, apt-get removed my DBMS automatically, because a different package decided a competing DBMS was needed.  Took me a few hrs to figure out what happened. 

Use **apt-get** instead, but not though a crontab.  Maybe, if you must, on an internet-facing, dangerous, server like one running wordpress, setup security patching daily, but not all patches.

---

