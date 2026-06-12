---
title: "CPU Frequencies Broken"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by clarge2 on 2010-05-02
I recently upgraded from 8.10 to 10.4 and have noticed a problem which I thought was fixed is recurring (original post: [3 GHz Xeon runs at 900 MHz]("http://ubuntuforums.org/showthread.php?t=1082873")). This is the result of cpufreq-info ```
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 600 MHz - 900 MHz
  available frequency steps: 900 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 900 MHz and 900 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 900 MHz.
  cpufreq stats: 900 MHz:92.17%, 600 MHz:7.83%  (290)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 600 MHz - 900 MHz
  available frequency steps: 900 MHz, 600 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 900 MHz and 900 MHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 900 MHz.
  cpufreq stats: 900 MHz:92.12%, 600 MHz:7.88%  (266)

```
I would really appreciate some assistance in getting a permanent fix for the problem.

---

### Post by clarge2 on 2010-05-02
I shut down the machine after the last post because it was frustrating me that I couldn't fix it. I just rebooted it and here's the most recent cpufreq-info
```
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 1.60 GHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 1.60 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.40 GHz and 2.40 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.40 GHz.
  cpufreq stats: 2.40 GHz:99.65%, 1.60 GHz:0.35%  (4)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 1.60 GHz - 2.40 GHz
  available frequency steps: 2.40 GHz, 1.60 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.40 GHz and 2.40 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 2.40 GHz.
  cpufreq stats: 2.40 GHz:99.64%, 1.60 GHz:0.36%  (2)
```
Any ideas why shutting down would allow the change? Or why 3.0 GHz is still not an option?

---

### Post by clarge2 on 2010-05-05
Bump

---

### Post by dernob on 2010-05-05
Our MacPro (2x Dualcore-Xeon 2Ghz) is stuck at 2Ghz and doesn't support cpu frequency scaling anymore since Update from 8.04. Maybe it is a similar problem.  When I'm back at work I will send in the cpufreq-info output.

AMD's new 6-Core CPUs have similar problems, see [this patch]("http://thread.gmane.org/gmane.linux.kernel/969032/focus=969035") and [this article]("http://www.heise.de/open/artikel/Performance-Schwaeche-bei-AMDs-Phenom-II-X6-unter-Linux-992514.html") (german, did not found something english).

---

### Post by clarge2 on 2010-05-07
It seems like heat has something to do with the disparity. I'm going to test that theory some more this weekend, but it seems like when I shut the system down for an extended period of time, the CPU frequencies revert to a more appropriate speed.

---

