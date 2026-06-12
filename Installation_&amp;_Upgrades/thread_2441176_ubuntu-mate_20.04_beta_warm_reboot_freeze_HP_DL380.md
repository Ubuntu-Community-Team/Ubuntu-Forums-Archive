---
title: "ubuntu-mate 20.04 beta warm reboot freeze HP DL380 G5 rcu_sched Sending NMI backtrace"
date: 2020-04-20
forum: Installation &amp; Upgrades
---

### Post by walterav on 2020-04-20
Cold booting the ubuntu-mate 20.04 beta amd64 desktop (USB iso or /hddinstall) on dated HP DL380 G5 Bios p56 dual CPU E5450 only works the first time, rebooting will let the system freeze during early boot with following error messages on console:

```
rcu: INFO : rcu_sched detected stalls on CPUs/tasks:
Sending NMI from CPU 0 to CPUs 1:
NMI Backtrace for CPU 1 skipped: idling at acpi_idle_do_entry+0x19/0x40
```

No ECC RAM errors in the event log and RAM is tested fine 32GB total, also ubuntu 19.10 and earlier (re)boot fine. 

By adding "tsc=unstable" as a kernel paramter to "/etc/default/grub" it was solved, I'm not sure if this workaround has other side affects. Its possibly a regression since the kernel 5.3 from ubuntu 19.10 was working fine.

---

