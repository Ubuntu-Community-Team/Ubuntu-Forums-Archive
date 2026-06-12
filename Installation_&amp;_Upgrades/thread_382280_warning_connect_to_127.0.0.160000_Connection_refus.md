---
title: "warning: connect to 127.0.0.1:60000: Connection refused"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by hothgremlin on 2007-03-11
Dear community!

I am trying to configure a damned virtual mta since 10 hours now, using several tutorials, etc... for debian, gentoo and ubuntu...

now, after all this time, it seems everything is running.. i can send mails from localhost to virtual domains, etc.. but when i try to send a mail from outside the server, it always says:

"warning: connect to 127.0.0.1:60000: Connection refused"

WHAT SHALL I DO???? AAAAAAAAHHHHHHHHHHHHHHHHHHHHH

please help!

with best regards,
hg

---

### Post by John Nilsson on 2007-10-23
Old thread. But as I just had this problem after the Upgrade to Gutsy someone else might need the answer.

The problem is probably that postgrey is not running. I'd managed to deinstallit during the upgrade.

---

### Post by lobo_cobra on 2007-10-27
it was the solution for me. Postgrey was not running. Therefore I got this message. I still wonder why postgrey did not work. But its solved now.

Thanks

---

### Post by John Nilsson on 2007-10-27
Well, it's not solved yet. There is a [bug]("https://bugs.launchpad.net/ubuntu/+source/db4.4/+bug/135038") in the gutsy version of **libdb4.4** that makes postgrey crash every night.

Until a fix is released I've "solved" the problem by installing **monit** using the following configuration:

```

set daemon  60

check process postgrey with pidfile /var/run/postgrey.pid
    start program = "/etc/init.d/postgrey start"
    stop program  = "/etc/init.d/postgrey stop"

```

monit will then make sure that postgrey is restarted when it crashes.

---

