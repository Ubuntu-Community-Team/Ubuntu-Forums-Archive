---
title: "Intrepid - Intel wireless not working after kernel update"
date: 2008-07-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by faxmaster on 2008-07-22
Ubuntu updated from 2.6.26-3 to 2.6.26-4 and now my wireless card quit working.  It also no longer works when booting into x.26-3 from Grub.

This is from kern.log.0:
[INDENT]
Jul 21 00:58:18 ubuntulap kernel: [   12.516090] ieee80211: 802.11 data/management/control stack, git-1.1.13
Jul 21 00:58:18 ubuntulap kernel: [   12.516094] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jul 21 00:58:18 ubuntulap kernel: [   12.783026] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Jul 21 00:58:18 ubuntulap kernel: [   12.783031] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 21 00:58:18 ubuntulap kernel: [   12.783118] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 21 00:58:18 ubuntulap kernel: [   12.835265] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 21 00:58:18 ubuntulap kernel: [   12.835318] firmware: requesting ipw2200-bss.fw
Jul 21 00:58:18 ubuntulap kernel: [   13.260479] input: PC Speaker as /class/input/input5
Jul 21 00:58:18 ubuntulap kernel: [   13.857942] input: Video Bus as /class/input/input6
Jul 21 00:58:18 ubuntulap kernel: [   13.880064] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)[B]
Jul 21 00:58:18 ubuntulap kernel: [   15.564430] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
Jul 21 00:58:18 ubuntulap kernel: [   15.564436] ipw2200: Unable to load firmware: -2
Jul 21 00:58:18 ubuntulap kernel: [   15.564440] ipw2200: failed to register network device[/B][/INDENT]

This was working fine when I first installed (and perfectly on 8.04) but some update cause it to quit working.  How do I go about fixing my card?

Running a Toshiba m45-s265.  My wireless card is an Intel BG2200.

Thanks!

---

### Post by chili555 on 2008-07-22
Please open a terminal and do:```
uname -r
sudo updatedb
locate ipw2200-bss.fw
```updatedb will take a few moments; please be patient. Let's see if we can figure out where the firmware went.

---

### Post by syko21 on 2008-07-22
Can a mod please move this to the Development forum?

---

### Post by faxmaster on 2008-07-22
"uname -r" reports:  2.6.26-4-generic; running "locate ipw2200-bss.fw" returned nothing.

So I did "locate ipw2200" and got
[INDENT]
/lib/modules/2.6.26-3-generic/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/2.6.26-4-generic/kernel/drivers/net/wireless/ipw2200.ko
/lib/modules/last-good-boot/kernel/drivers/net/wireless/ipw2200.ko
/usr/src/linux-headers-2.6.26-3-generic/include/config/ipw2200
/usr/src/linux-headers-2.6.26-3-generic/include/config/ipw2200.h
/usr/src/linux-headers-2.6.26-3-generic/include/config/ipw2200/monitor.h
/usr/src/linux-headers-2.6.26-3-generic/include/config/ipw2200/promiscuous.h
/usr/src/linux-headers-2.6.26-3-generic/include/config/ipw2200/qos.h
/usr/src/linux-headers-2.6.26-3-generic/include/config/ipw2200/radiotap.h
/usr/src/linux-headers-2.6.26-4-generic/include/config/ipw2200
/usr/src/linux-headers-2.6.26-4-generic/include/config/ipw2200.h
/usr/src/linux-headers-2.6.26-4-generic/include/config/ipw2200/monitor.h
/usr/src/linux-headers-2.6.26-4-generic/include/config/ipw2200/promiscuous.h
/usr/src/linux-headers-2.6.26-4-generic/include/config/ipw2200/qos.h
/usr/src/linux-headers-2.6.26-4-generic/include/config/ipw2200/radiotap.h
[/INDENT]

I found these on Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/180544](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/180544)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210595](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210595)

---

### Post by Joeb454 on 2008-07-22
> **syko21 said:**
> Can a mod please move this to the Development forum?

Use the report button ;) Moved anyway - @ OP - intrepid is still alpha testing, things **WILL** break :)

---

### Post by psyke83 on 2008-07-22
Install the package "linux-restricted-modules-common" and reboot. This package was missing from the alternative CD, though it doesn't explain how your wireless was working before the kernel update. Anyway, this is the bug I filed for the issue I found: [https://bugs.launchpad.net/bugs/251018](https://bugs.launchpad.net/bugs/251018)

---

### Post by faxmaster on 2008-07-23
> **Joeb454 said:**
> Use the report button ;) Moved anyway - @ OP - intrepid is still alpha testing, things **WILL** break :)
Oh, I know :)


> **psyke83 said:**
> Install the package "linux-restricted-modules-common" and reboot. This package was missing from the alternative CD, though it doesn't explain how your wireless was working before the kernel update. Anyway, this is the bug I filed for the issue I found: [https://bugs.launchpad.net/bugs/251018](https://bugs.launchpad.net/bugs/251018)

That did it.  Wireless is working.  Thanks.

---

