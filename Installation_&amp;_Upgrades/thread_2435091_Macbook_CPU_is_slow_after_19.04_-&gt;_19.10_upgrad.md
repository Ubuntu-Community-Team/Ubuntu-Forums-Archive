---
title: "Macbook CPU is slow after 19.04 -&gt; 19.10 upgrade"
date: 2020-01-16
forum: Installation &amp; Upgrades
---

### Post by tasket on 2020-01-16
I've been running Ubuntu on a 2007 Core2Duo T7400 Macbook (not 'pro') for several years, and I have brought the system through upgrades beginning with 14.04LTS.

This upgrade introduces a problem with CPU frequency, however. CPU clock does not go above 997MHz under 100% load... it stays there all the time. The normal CPU frequency is 2.16GHz. This shows as a drastic performance degradation.

Thinking it could have been some kind of thermal throttling, I disabled the 'thermald' service. But there was no change. I also thought the new 5.3.x kernel could be misconfigured, but I still had the older 5.0.x kernel from Disco and booting with that makes no difference.. CPU is still slow.

Other details about this system: There is no main battery installed, so it doesn't have a "healthy battery" status. I heard there is a bug in Linux that pops up as a regression where a non-existent battery is interpreted as "low battery, must save power, slow down CPU". The power governor is set to default "ondemand" and the min+max frequency ranges under /sys/devices/system/cpu/cpuX/cpufreq look normal.

I've also read on various forums that the cpupower utility can't override this type of issue, so I'm not sure if I should bother trying it.

So I'm at my wits end troubleshooting this and could use some help. It looks like going back to 18.04 or installing Debian Buster may be my best bet if I don't find a solution for 19.10.

---

### Post by tasket on 2020-01-16
Another thing: 'scaling_driver' is set to "acpi-cpufreq" but `lsmod` doesn't list it as a loaded kernel module. If I `modprobe acpi-cpufreq` nothing really happens... result code is 0, no error but module isn't loaded. Also, `dmesg` has nothing mentioning "cpufreq".

---

