---
title: "samba daemon won't start after dapper upgrade"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by OmniBlade on 2006-07-22
Ever since I upgraded to 6,06 from 5.10, the samba daemon won't start and when trying to reinstall the package I get the following error:

```

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu3.1) ...
 * Starting Samba daemons...                                             [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've checked the log file /var/log/samba/log.smbd and I get the follow entries when I have tried to start the daemon:

```

[2006/07/22 14:11:07, 0] smbd/server.c:main(805)
  smbd version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2006/07/22 14:11:07, 1] auth/auth_util.c:make_server_info_sam(876)
  User guest in passdb, but getpwnam() fails!
[2006/07/22 14:11:07, 0] smbd/server.c:main(829)
  ERROR: failed to setup guest info.

```

I did get a few errors on upgrade thanks to the pcmcia hang, but I don't recall if any were to do with samba at the time. I've searched in vain for a solution to this so any help would be appreciated.

---

