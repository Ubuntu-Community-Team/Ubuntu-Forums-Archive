---
title: "Crash on boot 50% of the time"
date: 2008-09-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Wise Ferret on 2008-09-25
I have 32-bit intrepid on lg-s1 laptop (x1600 radeon, et131x ethernet, intel 3945 wireless).
After upgrading from Hardy, 50% of my boot attempts fail. The progress is just stopped after displaying "Loading hardware drivers...", there is no disk activity and I have to reset manually. On the other 50% the sequence stops for a sec, I hear a cracking noise from the speakers and everything goes on normally.
How can I start solving it? What log file should I check here? I am not sure what file represents the log of a former, unsuccessful boot attempt. I am not even sure if this event is even logged.

---

### Post by aethralis on 2008-09-25
Please see the thread: [http://ubuntuforums.org/showthread.php?t=924142](http://ubuntuforums.org/showthread.php?t=924142) and bug [#263059]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263059/") it may be related...

---

### Post by Wise Ferret on 2008-09-25
Thank you, I think it is.

This is what I get after turning off quiet and splash flags in /boot/menu.lst (copied by hand...):

iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for linux, 1.2.26ks
iwl3945: Copyright (C) 2003-2008 Intel Corporation
iwl3945 0000 :05 :00 .0 PCI INT -> GSI 19 (level, low) -> IRQ 19
iwl3945: Detected Intel Wireless Wifi Link 3945ABG
cs: IO port probe 0x100-0x3af: clean
cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
cs: IO port probe 0x820-0x8ff: clean
cs: IO port probe 0xc00-0xcf7: clean
cs: IO port probe 0xa00-0xaff: clean
iwl3945: Tunable Channels: 13 802.11bg, 0 802.11a channels
iwl3945 0000 :05 :00 .0 PCI INT A disabled
iwl3945 0000 :05 :00 .0 PCI INT -> GSI 22 (level, low) -> IRQ 22
Setting the system clock ... OK

CRAAAASH!


(sometimes it happens before the system clock line)

This looks like a general iwl3495 driver problem with intrepid.

---

