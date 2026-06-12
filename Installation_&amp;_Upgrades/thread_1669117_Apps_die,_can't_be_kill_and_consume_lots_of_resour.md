---
title: "Apps die, can't be kill and consume lots of resource."
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by wyleu on 2011-01-17
I apologize if this is posted in the wrong place.

I have recently upgraded from Ubuntu Studio 10.04 to 10.10.

Several apps seem to crash, ( firefox-bin, thunderbird-bin, gnome-system-monitor, gnome-system-log is a current cross section)

There is a report that the application is not responding, and the process cannot be killed (kill pid, kill -9 pid, both as user and sudo) AND consumes considerable system resource;-

top
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
 5094 chris     20   0  164m  21m  18m R 41.2  3.6  21:28.88 gnome-system-mo    
 5240 chris     20   0  179m  14m  11m R 41.2  2.4   3:59.22 gnome-system-lo 

The only option is a reboot.

Where should I start looking for possible errors both on this forum and within the various logs on the system?

chris@dellap:~$ uname -a
Linux dellap 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009 i686 GNU/Linux
chris@dellap:~$

---

