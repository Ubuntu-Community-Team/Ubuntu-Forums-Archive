---
title: "Configure Ubuntu 7.04 server to shutdown scheduled"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by Partyboi2 on 2008-04-13
To have your server shutdown at 23.00  use cron. In a terminal give yourself root session.
```
sudo -s
``` then open up cron file
```
crontab -e
``` then add
```
23 * * *    /sbin/shutdown -h now
``` then to save press Ctrl+o, then enter and then finally  ctrl+x to exit.

---

