---
title: "Problem with 2.6.24-18 (ip6)"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by juanto on 2008-06-10
I have just upgraded from 6.06 to 8.04. I hava had several issues... but finally I have get to start the system.

Currently the issue is when the system boots... the system stops several minutes in a point and to continue I press CTRL+X.

Looking the log:

--- cut ---

Jun 10 17:28:36 sancho kernel: [  892.352334] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Jun 10 17:28:36 sancho kernel: [  892.352380] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Jun 10 17:39:23 sancho kernel: [  687.229299] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jun 10 17:39:23 sancho exiting on signal 15
Jun 10 17:43:29 sancho syslogd 1.5.0#1ubuntu1: restart.
Jun 10 17:43:29 sancho kernel: Inspecting /boot/System.map-2.6.24-18-386
Jun 10 17:43:29 sancho kernel: Loaded 27280 symbols from /boot/System.map-2.6.24-18-386.
Jun 10 17:43:29 sancho kernel: Symbols match kernel version 2.6.24.
Jun 10 17:43:29 sancho kernel: Loaded 22133 symbols from 115 modules.
Jun 10 17:43:29 sancho kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 10 17:43:29 sancho kernel: [    0.000000] Linux version 2.6.24-18-386 (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 Wed May 28 19:30:01 UTC 2008 (Ubuntu 2.6.24-18.32-386)
Jun 10 17:43:29 sancho kernel: [    0.000000] BIOS-provided physical RAM map:
--- cut ---

The problem is in the line: 

Jun 10 17:39:23 sancho kernel: [  687.229299] ip6_tables: (C) 2000-2006 Netfilter Core Team

If I execute the 2.6.15-51 kernel, this problem doesn't appear.

How can I remove this ip6 entry of the kernel?

Thanks & Best Regards,

Juanto.

---

