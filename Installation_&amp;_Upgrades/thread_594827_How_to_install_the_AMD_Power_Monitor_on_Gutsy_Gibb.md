---
title: "How to install the AMD Power Monitor on Gutsy Gibbon?"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by li009 on 2007-10-28
I am not sure, whether Gutsy Gibbon has AMDs feature Cool'n'Quiet automatically activated. To find out I would like to install the AMD Power Monitor. Linux drivers for Suse and Red Hat are here: [http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html]("http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html")

But so far I could not find out, if as a user of Kubuntu one can get this tool going as well.

---

### Post by hencke on 2007-11-17
> **li009 said:**
> I am not sure, whether Gutsy Gibbon has AMDs feature Cool'n'Quiet automatically activated. To find out I would like to install the AMD Power Monitor. Linux drivers for Suse and Red Hat are here: [http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html]("http://www.amd.com/us-en/Processors/TechnicalResources/0,,30_182_871_13118,00.html")

But so far I could not find out, if as a user of Kubuntu one can get this tool going as well.

From the link you posted:

> 
**AMD Athlon™ 64 X2 Dual-Core Cpufreq Driver for Linux 2.10.00 - Allows the system to automatically adjust the CPU frequency, voltage and power combination that match the instantaneous user performance need.** Supports all AMD Turion™ 64 Mobile Technology, AMD Opteron™ Processors, and Athlon™ 64 Processors released through 2007. **Provides support for AMD PowerNow!™ technology and, where appropriate, AMD’s Cool-n-Quiet™ technology for Linux systems.** Works with all kernels, version 2.6.10 or later. Requires the on demand kernel module or the cpufreq-1.20, cpuspeed-1.20.1, or powersaved-0.8.19 or later user programs to support SMP and multi-core systems. **This driver is already included in the 2.6.18 or later kernels and does not need to be downloaded again.**

If you would like to make sure that your processor is scaling properly open KMenu ->System->KSysGuard

By default the frequency sensor won't be in the "System Load" -tab, but you can add sensors by navigating to the right sensor in the side pane on the right. Under "localhost" you should see something like "CPU0" and "CPU1" and under them "Clock frequency" drag this (these) into an empty sensor spot. If there aren't any, try removing an existing one or try navigating to Edit->Worksheet Properties and adding some sensor rows or columns.

In both gnome and kde it is possible to add an applet that monitors the the cpu frequency to the panels.

Whichever way you use to monitor your cpu frequency, you should be able to see as it goes up and down according to cpu load.

---

### Post by xinix on 2007-11-27
```
This driver is already included in the 2.6.18 or later kernels and does not need to be downloaded again.
```

Form this I would assume that Ubuntu should have this driver in the kernel since Gutsy's version is higher.  But I don't see any scaling going on with the dual core cpu.  I did see it with a single core setup.  Not sure if it is because Ubuntu doesn't install the apps the driver site recommends.

```
Requires the on demand kernel module or the cpufreq-1.20, cpuspeed-1.20.1, or powersaved-0.8.19 or later user programs to support SMP and multi-core systems
```

Installing these conflicts with the default apps.  I'll give them a try later.

---

