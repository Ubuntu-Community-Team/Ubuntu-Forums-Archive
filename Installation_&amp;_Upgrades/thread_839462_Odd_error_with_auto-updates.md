---
title: "Odd error with auto-updates?"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by gfunkdave on 2008-06-24
Hi all,

I have set an automatic update in root's crontab. Lately, almost every time my log shows the following. Do I need to worry about this, or is it just an artifact of being run as a cron job?

> 
***Beginning auto-update on Tue Jun 24 07:00:01 CDT 2008


debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin:



Thanks for shedding some light on things!

Incidentally, here's the command as appears in cron:

```

#update the system twice a day, at 6AM and 7PM. Log errors
00 06,19 * * * (PATH=/usr/sbin:/usr/bin:/sbin:/bin && intro="\n***Beginning auto-update on "`date`"\n\n" && echo -e $intro >> /var/log/auto_update.log && aptitude -y update && aptitude -y safe-upgrade) 2>> /var/log/auto_update.log

```

---

### Post by Sarmacid on 2008-07-30
I was getting this error when trying to update with a cron job executing my update script

```
debconf: unable to initialize frontend: Dialog
debconf: (TERM is not set, so the dialog frontend is not usable.)
debconf: falling back to frontend: Readline
debconf: unable to initialize frontend: Readline
debconf: (This frontend requires a controlling tty.)
debconf: falling back to frontend: Teletype
dpkg-preconfigure: unable to re-open stdin:
Fetched 9756kB in 45s (214kB/s)
dpkg: `ldconfig' not found on PATH.
dpkg: `start-stop-daemon' not found on PATH.
dpkg: `install-info' not found on PATH.
dpkg: `update-rc.d' not found on PATH.
dpkg: 4 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

To fix this I had to add the PATH line to my script

```
#!/bin/bash

PATH="$PATH:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin"

echo "* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *" >>
/root/logs/updatelog
date >> /root/logs/updatelog
echo "* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * *" >>
/root/logs/updatelog
echo "" >> /root/logs/updatelog
apt-get update #>> /root/logs/updatelog
apt-get -y upgrade >> /root/logs/updatelog 2>&1
echo "" >> /root/logs/updatelog

```

---

