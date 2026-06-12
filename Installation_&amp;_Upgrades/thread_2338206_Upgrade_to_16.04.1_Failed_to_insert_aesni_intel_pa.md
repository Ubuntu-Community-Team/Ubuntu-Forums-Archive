---
title: "Upgrade to 16.04.1: Failed to insert aesni_intel padlock_aes - no such device"
date: 2016-09-25
forum: Installation &amp; Upgrades
---

### Post by andyhelloween on 2016-09-25
Hello everyone,

Yesterday I upgraded my Ubuntu Server from 14.04.1 to 16.04.1. The process completed with errors. After fixing most of them, I now have a stable system for all I can see.

But I noticed the following issue which I hope someone can point me in the right direction. Because I did the upgrade first in using a VM, all I can think is the issue relates to hardware.
[B]
Error 1: "Failed to insert 'aesni_intel': No such device"[/B]
**Error 2:** "**Failed to insert 'padlock_aes': No such device"**

Output of: systemctl status systemd-modules-load.service

```
&#9679; systemd-modules-load.service - Load Kernel Modules
   Loaded: loaded (/lib/systemd/system/systemd-modules-load.service; static; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2016-09-26 12:00:14 NZDT; 16min ago
     Docs: man:systemd-modules-load.service(8)
           man:modules-load.d(5)
  Process: 415 ExecStart=/lib/systemd/systemd-modules-load (code=exited, status=1/FAILURE)
 Main PID: 415 (code=exited, status=1/FAILURE)

Sep 26 12:00:13 hostname systemd[1]: Starting Load Kernel Modules...
Sep 26 12:00:13 hostname systemd-modules-load[415]: Module 'loop' is builtin
Sep 26 12:00:13 hostname systemd-modules-load[415]: Module 'loop' is builtin
Sep 26 12:00:14 hostname systemd-modules-load[415]: **Failed to insert 'aesni_intel': No such device**
Sep 26 12:00:14 hostname systemd[1]: **systemd-modules-load.service**: Main process exited, code=exited, status=1/FAILURE
Sep 26 12:00:14 hostname systemd[1]: Failed to start Load Kernel Modules.
Sep 26 12:00:14 hostname systemd[1]: systemd-modules-load.service: Unit entered failed state.
Sep 26 12:00:14 hostname systemd[1]: systemd-modules-load.service: Failed with result 'exit-code'.
```

Output of: journalctl -b _PID=415

```
-- Logs begin at Mon 2016-09-26 12:00:09 NZDT, end at Mon 2016-09-26 12:17:01 NZDT. --
Sep 26 12:00:13 hostname systemd-modules-load[415]: Module 'loop' is builtin
Sep 26 12:00:13 hostname systemd-modules-load[415]: Module 'loop' is builtin
Sep 26 12:00:14 hostname systemd-modules-load[415]: **Failed to insert 'aesni_intel': No such device**
Sep 26 12:00:14 hostname systemd-modules-load[415]: **Failed to insert 'padlock_aes': No such device**
```

AES would suggest encryption I guess?

Thanks for your time!

Cheers,
Andres.

---

### Post by andyhelloween on 2016-09-25
Found the issue. Processor does not support AES. :(

result of ```
grep -o aes /proc/cpuinfo
``` comes empty.

Hope this helps someone.

---

