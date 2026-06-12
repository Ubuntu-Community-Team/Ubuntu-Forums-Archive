---
title: "Error running apt-get from crontab"
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by leslie4 on 2015-01-21
When I run "apt-get -y upgrade" as root at the command prompt, it works fine, but when I run the same command from root's crontab it fails and leaves this message in the apt-get history: ```
Error: Sub-process /usr/bin/dpkg returned an error code (2)
```  Any ideas why one works but not the other?  I'm running 14.04.1 LTS (3.13.0-32-generic #57-Ubuntu), if that helps. Thanks in advance to all who respond.

---

### Post by TheFu on 2015-01-21
cron runs without ANY environment - ok, just an extremely minimal env. You must setup anything desired/needed before calling programs.  I don't know what those are for apt-get. Sorry.  There is an automatic security updates option, if that is what you want somewhere.

I much prefer to manually perform updates across the 30 boxes here and log the output, so if anything strange happens, the log is there to figure it out.  Been doing this weekly for about 6 yrs. Can't recall having any major issues, ever.

---

### Post by leslie4 on 2015-01-28
> **TheFu said:**
> cron runs without ANY environment - ok, just an extremely minimal env. You must setup anything desired/needed before calling programs. That was the problem.  I added a path to my crontab entry, and it worked fine: ```
0 4 * * *    PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin' /usr/bin/apt-get -y upgrade
``` Thanks for the help.

---

### Post by ian-weisser on 2015-01-28
FYI, apt already includes a daily 'update' in /etc/cron.daily/apt
It's trivial to add 'upgrade' using /etc/apt/apt.conf.d/50unattended-upgrades instead of a separate cron job. 

That file tracks by repository - simply uncomment (or add) the repositories you want to auto-upgrade.
That's how Ubuntu offers auto-updates for Security, for example.

---

### Post by TheFu on 2015-01-28
> **leslie4 said:**
> That was the problem.  I added a path to my crontab entry, and it worked fine: ```
0 4 * * *    PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin' /usr/bin/apt-get -y upgrade
``` Thanks for the help.

Or you could have just followed recommended practice and used the full path to the exec in the command (or script). /usr/bin/apt-get

---

