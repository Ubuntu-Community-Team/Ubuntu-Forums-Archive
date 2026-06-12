---
title: "Automatic shutdown and updates"
date: 2018-03-29
forum: Installation &amp; Upgrades
---

### Post by stylus3530 on 2018-03-29
Hey

I would like to ensure that my PC is automatically switched off at 10.30 pm and installs the updates at 12.00. If something goes wrong during the installation of these updates, I also want to receive a message at my "Hotmail" address. 

Is there a script or tutorial somewhere that even a beginner like me understands?

Thanks in advance

STYLUS

---

### Post by TheFu on 2018-03-29
If you power off the computer at 22:30, how can it install anything at midnight?
Perhaps you want to install updates at 22:30 and power off at midnight instead?
If something goes wrong, you'll need a backup to restore. Best to do that PRIOR to the patching, IMHO.

As for sending email - that depends on many things - like your ISP, their method of mail handling, etc. Others have asked that same question and there are posted solutions in these forums.

I would suggest that patching daily isn't a good idea.  I patch weekly, at a time that I'll be able to correct any issues - or live with the system being down for hours, if necessary.  I use a script, since I need to patch 15-30 systems.  To automate stuff, use cron.  By default, cron sends email to the userid running the task upon completion.  If you redirect stdout to /dev/null, then only stderr will be left, which is the standard for all error messages on any Unix system.  That would be emailed to the userid automatically, assuming you've configured email on the system correctly.  I would like to point out that sending system admin emails over the public internet might not be the smartest thing - often failures will include sensitive data that wouldn't be good for others to see.

So ... [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) and [https://www.howtogeek.com/101288/how-to-schedule-tasks-on-linux-an-introduction-to-crontab-files/](https://www.howtogeek.com/101288/how-to-schedule-tasks-on-linux-an-introduction-to-crontab-files/)

The key with any scripted, automatic, cron job is to realize that cron doesn't provide much of an "environment".  This is different from a normal login which gets all sorts of environment variables set - like $HOME. Under cron, no HOME is set.  A minimal PATH is set as well.  So when creating a script that will be run via cron and not from an interactive login, it is required that you setup the environment that you want used.  It is also important to specify the full-path-to-each command, since trusting the PATH is poor security.

Beginning Scripting Guide: [https://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html)

Hope this helps.

---

