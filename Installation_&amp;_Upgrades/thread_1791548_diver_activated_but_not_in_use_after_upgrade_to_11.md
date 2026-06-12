---
title: "diver activated but not in use after upgrade to 11.04"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2011-06-27
I've just upgraded from 10.10 to 10.04 and while the upgrade went smooth (Thanks), the nvidia driver is activated but not in use (please see attached screen shot). I have tried to remove and reinstall the driver, but after a reboot I get the same result.

Relevant lines of syslog would indicate its loaded ok.

-------------------------------
Jun 27 14:05:54 LeosLinux kernel: [   21.711789] nvidia: module license 'NVIDIA' taints kernel.
Jun 27 14:05:54 LeosLinux kernel: [   21.711792] Disabling lock debugging due to kernel taint
Jun 27 14:05:54 LeosLinux kernel: [   22.061084] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun 27 14:05:54 LeosLinux kernel: [   22.061092] nvidia 0000:01:00.0: setting latency timer to 64
Jun 27 14:05:54 LeosLinux kernel: [   22.061096] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Jun 27 14:05:54 LeosLinux kernel: [   22.061227] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
Jun 27 14:05:54 LeosLinux kernel: [   22.279897] FS-Cache: Loaded
Jun 27 14:05:54 LeosLinux kernel: [   22.344218] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jun 27 14:05:54 LeosLinux kernel: [   22.366992] FS-Cache: Netfs 'nfs' registered for caching

---------------------------------

Thanks

---

### Post by MAFoElffen on 2011-06-27
> **lister171254 said:**
> I've just upgraded from 10.10 to 10.04 and while the upgrade went smooth (Thanks), the nvidia driver is activated but not in use (please see attached screen shot). I have tried to remove and reinstall the driver, but after a reboot I get the same result.

Relevant lines of syslog would indicate its loaded ok.

Thanks
Check your /var/log/xorg.0.log to verify everything is loaded... If good, then ignore.  There is an open bug at launchpad where jockey-gtk shows the nvidia driver as installed but not activated when it actually is.
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/771788)
In that case, the problem is not with the nvidia driver, but with Jockey- Which they are working on.

---

### Post by lister171254 on 2011-06-27
Xorg0.log looks ok.

Thanks for the launchpad link. Looks more like a minor problem as the driver is loaded and active.

Thanks

---

