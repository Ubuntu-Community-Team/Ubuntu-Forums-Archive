---
title: "Upgrading postgres on x86 ubuntu 8.04"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by Cowloon on 2008-11-09
I get this error:

2008-11-09 20:04:02 PST FATAL:  could not create shared memory segment: Invalid argument
2008-11-09 20:04:02 PST DETAIL:  Failed system call was shmget(key=5433001, size=38207488, 03600).
2008-11-09 20:04:02 PST HINT:  This error usually means that PostgreSQL's request for a shared memory segment exceeded your kernel's SHMMAX parameter.  You can either reduce the request size or reconfigure the kernel with larger SHMMAX.  To reduce the request size (currently 38207488 bytes), reduce PostgreSQL's shared_buffers parameter (currently 4096) and/or its max_connections parameter (currently 103).
	If the request size is already small, it's possible that it is less than your kernel's SHMMIN parameter, in which case raising the request size or reconfiguring SHMMIN is called for.

Should I recompile the kernel, or is there something else to do?

---

### Post by pdwerryhouse on 2008-11-10
You don't need to recompile the kernel to change shmmax or shmmin

Just put:

```
kernel.shmmax = *somevalue*
kernel.shmmin = *somevalue*
```

...into /etc/sysctl.conf

and then run:

```
sysctl -p
```

---

### Post by Cowloon on 2008-11-10
Thanks! That worked. Or I first ran sysctl on the command line, made sure that the upgrade worked and then added the value to sysctl.conf.

---

