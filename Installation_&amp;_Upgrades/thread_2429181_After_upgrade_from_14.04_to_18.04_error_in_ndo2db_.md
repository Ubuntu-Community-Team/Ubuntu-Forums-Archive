---
title: "After upgrade from 14.04 to 18.04 error in ndo2db (nagios)"
date: 2019-10-14
forum: Installation &amp; Upgrades
---

### Post by pepecarlos on 2019-10-14
[FONT=arial]Hi,

I have a error very strange in my nagios installation, after upgrade of operative system from Ubuntu 14.04 to 16.04, appear in syslog the message:
Error: queue recv error. but only when exit the ssh session.

my sysctl.conf has the next configuration:
```
kernel.msgmnb = 262144000
kernel.msgmax = 262144000
kernel.shmmax = 4294967295
kernel.shmall = 268435456
kernel.msgmni = 512000
```
the output for the "ipcs -q" command when error happen is the next:
```
----- Message Queues --------
key        msqid      owner      perms      used-bytes   messages
0x26000002 2359296    nagios     600        7825408      7642
```
when is ok is the next:
------ Message Queues --------
```
key        msqid      owner      perms      used-bytes   messages
0x26000002 2359296    nagios     600        0              0
```
And the messages in syslog are the next when I perform a logoff ssh from system:
```
Sep  9 17:15:01 nagios_server systemd[1]: Stopping User Manager for UID 1000...
Sep  9 17:15:01 nagios_server systemd[2568]: Reached target Shutdown.
Sep  9 17:15:01 nagios_server systemd[2568]: Stopped target Default.
Sep  9 17:15:01 nagios_server systemd[2568]: Stopped target Basic System.
Sep  9 17:15:01 nagios_server systemd[2568]: Stopped target Paths.
Sep  9 17:15:01 nagios_server systemd[2568]: Stopped target Timers.
Sep  9 17:15:01 nagios_server systemd[2568]: Stopped target Sockets.
Sep  9 17:15:01 nagios_server systemd[2568]: Starting Exit the Session...
Sep  9 17:15:01 nagios_server systemd[2568]: Received SIGRTMIN+24 from PID 2855 (kill).
Sep  9 17:15:01 nagios_server systemd[1]: Stopped User Manager for UID 1000.
Sep  9 17:15:01 nagios_server systemd[1]: Removed slice User Slice of nagios.
Sep  9 17:15:01 nagios_server ndo2db: Error: queue recv error.
Sep  9 17:15:03 nagios_server ndo2db: message repeated 102984 times: [ Error: queue recv error.]
```
I tested the same configuration in clean installation and the error does not appear, only happens when upgrade ubuntu from 14.04 to 16.04 or 18.04.

In Nagios forum does not found the solution.

Somebody knows what could happen?



Thanks.[/FONT]

---

### Post by mörgæs on 2019-10-15
Hi, welcome to the fora.

> **pepecarlos said:**
> 
I tested the same configuration in clean installation and the error does not appear, only happens when upgrade ubuntu from 14.04 to 16.04 or 18.04.


I think you have the answer here. Buntu installs are fragile when it comes to upgrades so most people suggest a clean install every second or fourth year when running the LTS track.

---

### Post by pepecarlos on 2019-10-16
Thanks mörgæs  for you reply, but I think that the solution should be more simple that perform a clean installation, surely the problem is in any configuration that perform a logoff of the user, myabe a supended mode or another "thing" similiar.

Someone have another suggestion to solve the problem?

Thanks

---

### Post by Autodave on 2019-10-16
+1 with mörgæs here.  Upgrades often cause these types of problems and can be next to impossible to figure out and repair.  I learned a long time ago to only do clean upgrades.

---

### Post by slickymaster on 2019-10-16
*Thread moved to **Installation & Upgrades**.*

---

### Post by pepecarlos on 2019-10-21
The clean install is very expensive for me due the different components that I use to monitoring my platform. 


I continue thinking that sure exists an explanation to this behavior. Someone have a solution for this?


Thanks.

---

