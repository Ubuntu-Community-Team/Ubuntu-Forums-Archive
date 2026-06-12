---
title: "cron requires manual start after 10.04 upgrade"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by gtmarks on 2010-06-24
After upgrading Ubuntu from 9.10 to 10.04, the cron daemon no longer runs automatically upon starting up the machine; I need to enter "sudo service cron start" to get it running.  Is there a way to get it to start up by itself?

---

### Post by anglican on 2010-06-25
> **gtmarks said:**
> After upgrading Ubuntu from 9.10 to 10.04, the cron daemon no longer runs automatically upon starting up the machine; I need to enter "sudo service cron start" to get it running.  Is there a way to get it to start up by itself?
What is in your file /etc/init/cron.conf? It should look like:
```
# cron - regular background program processing daemon
#
# cron is a standard UNIX program that runs user-specified programs at
# periodic scheduled times

description     "regular background program processing daemon"

start on runlevel [2345]
stop on runlevel [!2345]

expect fork
respawn

exec cron
```H

---

### Post by gtmarks on 2010-06-28
Thank you for your reply.  My /etc/init/cron.conf file is exactly what you described.  (It is owned by root and has 644 permissions.)

---

### Post by gtmarks on 2010-07-02
I have an ad hoc solution to the problem, in case this helps anyone else.  At the end of the file $HOME/.bashrc add these lines:

```

if ! ps ax | grep -v grep | grep "cron" > /dev/null
   then
      echo ""
      echo "The cron daemon is not running, requires manual startup."
      echo ""
      sudo service cron start
fi
```

One would expect the cron daemon to start upon logging in, but at least this gets it manually started as soon as one opens a terminal.

---

