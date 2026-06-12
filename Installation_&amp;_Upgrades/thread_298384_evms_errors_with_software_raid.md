---
title: "evms errors with software raid"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by greghives on 2006-11-12
Hi,

I wonder if anyone else has noticed the following errors in 
/var/log/evms-engine.log

Using : Linux version 2.6.15-26-amd64-server (buildd@king) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP Thu Aug 3 03:32:26 UTC 2006 with software raid.

(with evms debug turned on )

Nov 12 20:50:27 myhost.mydomain _8_ Engine: ensure_dev_node: Make dev node for "/dev/evms/.nodes/ram0".
Nov 12 20:50:27 myhost.mydomain _8_ Engine: ensure_dev_node: Device node /dev/evms/.nodes/ram0 is for major 1, minor 0.
Nov 12 20:50:27 myhost.mydomain _8_ Engine: shutdown_thread: sem_wait returned -1.
Nov 12 20:50:27 myhost.mydomain _7_ Engine: ensure_dev_node: Exit.  Return value is 0.
Nov 12 20:50:27 myhost.mydomain _8_ Engine: shutdown_thread: errno is 4: Interrupted system call
Nov 12 20:50:27 myhost.mydomain _8_ Engine: shutdown_thread: Wait for SIGUSR1 shutdown signal.
Nov 12 20:50:27 myhost.mydomain _3_ Engine: engine_open_object: Open of /dev/evms/.nodes/ram0 failed with error code 22: Invalid argument
Nov 12 20:50:27 myhost.mydomain _7_ Engine: engine_open_object: Exit.  Return value is -22.

It looks like an attempt is being made to lse /dev/evms/.nodes/ram0 which does not exist.

My system is running fine but I would like to know why these errors are occurring.

Thanks,
Greg

---

