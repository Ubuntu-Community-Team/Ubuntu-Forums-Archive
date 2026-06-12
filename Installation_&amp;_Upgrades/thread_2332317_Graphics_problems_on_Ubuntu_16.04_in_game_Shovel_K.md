---
title: "Graphics problems on Ubuntu 16.04 in game Shovel Knight"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by lenrok258 on 2016-07-30
[FONT=verdana]Hi, I've just upgraded Ubuntu from 14.04 to 16.04 and video game Shovel Knight doesn't work correctly. It worked flawlessly on 14.04.
[/FONT]
[FONT=verdana]All screens (starting with map screen) looks like covered with bunch of ants.[/FONT]
[FONT=verdana]
Video: [https://www.youtube.com/watch?v=8Qv_yieL1a4&feature=youtu.be](https://www.youtube.com/watch?v=8Qv_yieL1a4&feature=youtu.be)[/FONT]
[FONT=verdana]
Anyone had similar problems? If so what is the solution?[/FONT]
[FONT=verdana]
My laptop is a Lenvo T410s with [/FONT]build-in[FONT=verdana] Intel GPU.[/FONT]
[FONT=verdana][I]

sudo lshw -C video[/I] *-display*
*description: VGA compatible controller* *product: Core Processor Integrated Graphics Controller* *vendor: Intel Corporation* *physical id: 2* *bus info: pci@0000:00:02.0* *version: 02* *width: 64 bits* *clock: 33MHz* *capabilities: msi pm vga_controller bus_master cap_list rom* *configuration: driver=i915 latency=0* *resources: irq:25 memory:f2000000-f23fffff memory:d0000000-dfffffff ioport:1800(size=8)*[/FONT]

---

