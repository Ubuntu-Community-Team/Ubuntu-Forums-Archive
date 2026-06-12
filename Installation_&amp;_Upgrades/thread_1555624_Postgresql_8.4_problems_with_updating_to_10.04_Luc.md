---
title: "Postgresql 8.4 problems with updating to 10.04 Lucid"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by stuartcnz on 2010-08-18
I recently upgrade from 9.10 Karmic to 10.04 Lucid. During the installation it had a problem with Postgresql 8.4 and said it couldn't finish the upgrade, and would restore the original system. At that point it just hung. 
Eventually I restarted the computer and it booted but without a desk top, just full screen terminal, so I tried installing the desktop, but it stumbled on Postgre 8.4. 

Eventually, with the installation disk and a few shut downs and restarts, I managed to get the system going again, mostly as 10.04 Lucid. I do still have the same issues when I try to run update manager.

This is what it displays:

```
Setting up postgresql-8.4 (8.4.4-0ubuntu10.04) ...
 * Starting PostgreSQL 8.4 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2010-08-19 01:24:57 NZST FATAL:  could not create shared memory segment: Invalid argument
2010-08-19 01:24:57 NZST DETAIL:  Failed system call was shmget(key=5432001, size=36880384, 03600).
2010-08-19 01:24:57 NZST HINT:  This error usually means that PostgreSQL's request for a shared memory segment exceeded your kernel's SHMMAX parameter.  You can either reduce the request size or reconfigure the kernel with larger SHMMAX.  To reduce the request size (currently 36880384 bytes), reduce PostgreSQL's shared_buffers parameter (currently 4096) and/or its max_connections parameter (currently 103).
	If the request size is already small, it's possible that it is less than your kernel's SHMMIN parameter, in which case raising the request size or reconfiguring SHMMIN is called for.
	The PostgreSQL documentation contains more information about shared memory configuration.
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.4, action "start" failed.
dpkg: error processing postgresql-8.4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-8.4

```

I would like to sort this out if some one could help.

---

