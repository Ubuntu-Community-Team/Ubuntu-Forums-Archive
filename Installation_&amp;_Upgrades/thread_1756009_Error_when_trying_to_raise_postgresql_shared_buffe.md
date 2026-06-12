---
title: "Error when trying to raise postgresql shared_buffers"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by nboutelier on 2011-05-11
Ive been searching everywhere for an answer to this without luck.
 
Im trying to raise my shared_buffers in postgresql to the recommended 25% of available ram (out of my 4GB). Even after setting kernel.shmmax=1073741824 in sysctl.conf im I still get this error when shared buffers are set to 512MB. Any suggestions?
 
* Restarting PostgreSQL 9.0 database server
* The PostgreSQL server failed to start. Please check the log output:
2011-05-10 18:06:33 PDT FATAL: could not create shared memory segment: No space left on device
2011-05-10 18:06:33 PDT DETAIL: Failed system call was shmget(key=5432001, size=560832512, 03600).
2011-05-10 18:06:33 PDT HINT: This error does *not* mean that you have run out of disk space. It occurs either if all available shared memory IDs have been taken, in which case you need to raise the SHMMNI parameter in your kernel, or because the system's overall limit for shared memory has been reached. If you cannot increase the shared memory limit, reduce PostgreSQL's shared memory request (currently 560832512 bytes), by reducing its shared_buffers parameter (currently 64000) and/or its max_connections parameter (currently 260).
The PostgreSQL documentation contains more information about shared memory configuration.
[fail]

---

