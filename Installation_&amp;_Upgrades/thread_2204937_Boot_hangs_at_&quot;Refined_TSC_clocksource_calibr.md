---
title: "Boot hangs at &quot;Refined TSC clocksource calibration&quot; on Dell Precision T1650"
date: 2014-02-11
forum: Installation &amp; Upgrades
---

### Post by Martijn_van_der_Ve on 2014-02-11
Fresh install of Ubuntu 12.04: live USB boots and works perfectly fine, but booting (in recovery mode) after installer finishes consistently results in boot to hang at:

ACPI: Requesting acpi_cpufreq
Refined TSC clocksource calibration: <XX> MHz
Switching to clocksource tsc

I've tried all kinds of clocksource= boot options, all resulting in the same behaviour (jiffies, acpi_pm) or a kernel panic (hpet). acpi=off also results in kernel panic. notsc removes the latter two clocksource lines, but booting still hangs at the same place.

During installation,  I tried both "Install updates while installing" enabled and disabled. Tried with Ubuntu 12.04 and Ubuntu 13.10 with exactly the same results. Tried on two (identical) machines.

Hardware:

Dell Precision T1650
Intel Xeon CPU E3-1225 V2 @ 3.20GHz (current clock speed)
NVIDIA NVS 300
BIOS Version: A12 (Default settings; Legacy boot)

According to the ubuntu website, this should work just fine:
[http://www.ubuntu.com/certification/hardware/201201-10376/](http://www.ubuntu.com/certification/hardware/201201-10376/)
Related thread:
[http://ubuntuforums.org/showthread.php?t=1040026](http://ubuntuforums.org/showthread.php?t=1040026)

Any ideas?

---

### Post by Martijn_van_der_Ve on 2014-02-12
Anyone? There must be a solution for this if this particular hardware is listed as "working" on the official ubuntu website.

In case it is of any help, Boot repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) returns:
[http://paste.ubuntu.com/6919090/](http://paste.ubuntu.com/6919090/)

---

### Post by Martijn_van_der_Ve on 2014-02-12
OK Solved! Seems to be an UEFI issue.

For reference:
First of all, needed to boot LiveUSB in UEFI mode (boot menu -> choose one that says UEFI <your usb device>); you might need to use a recent disk creator. Then, do normal install, which will be in UEFI mode. When restarting, set the default boot mode to UEFI (here: F12). Ubuntu now starts normally.

---

