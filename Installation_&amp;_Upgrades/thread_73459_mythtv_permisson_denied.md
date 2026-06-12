---
title: "mythtv permisson denied"
date: 2005-10-09
forum: Installation &amp; Upgrades
---

### Post by newb on 2005-10-09
when trying to run /etc/cron.daily/mythtv-backend i get the below error

```
root@mythtv:~ # /etc/cron.daily/mythtv-backend
Session management error: Could not open network socket
You need to configure the http cache.
Do you want to do it now? [yes,no (default=yes)]
You need to decide where the cache should be stored.
The cache must be stored in its own directory.
The directory should NOT be cleared when you reboot.
The default is /home/mythtv/.xmltv/cache

Where should the cache be stored?
Leave empty to use the default location:
/home/mythtv/.xmltv/cache does not exist.
Do you want me to create it? [yes,no (default=yes)]
mkdir /home/mythtv/.xmltv/cache: Permission denied at /usr/bin/tv_grab_se_swedb line 433
Error in 1:1: unexpected end of file
Failed to fetch some program info

```

---

### Post by TristanMike on 2005-10-09
If you feel it safe, you can try adding a "sudo" in front of it.

---

