---
title: "graphics driver issues. - Ubuntu 10.10"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by zoxopirezox on 2011-08-07
alright, so i cant install my graphics drivers. Everytime i do, i get a black screen of nothing on restart. I'm running ubuntu 10.10. here are my graphics cards.

jared@jared-HP-Pavilion-dv6-Notebook-PC:~$ lshw -C video
WARNING: you should run this program as super-user.
PCI (sysfs) 
*-display 
description: VGA compatible controller
product: Redwood [Radeon HD 5600 Series]
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: vga_controller bus_master cap_list rom
configuration: driver=radeon latency=0
resources: irq:46 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:4000(size=256) memory:c4440000-c445ffff
*-display
description: VGA compatible controller
product: Core Processor Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:45 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5050(size=8)

any ideas?

(When i go to install hardware it gives me a driver, but im guessing its an improper driver.)

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

do i install an inter-graded mother board driver, or a regular one? I just want to utilize my gig of Vram.

---

### Post by MAFoElffen on 2011-08-07
> **zoxopirezox said:**
> alright, so i cant install my graphics drivers. Everytime i do, i get a black screen of nothing on restart. I'm running ubuntu 10.10. here are my graphics cards.
```

jared@jared-HP-Pavilion-dv6-Notebook-PC:~$ lshw -C video
WARNING: you should run this program as super-user.
PCI (sysfs) 
*-display 
description: VGA compatible controller
product: Redwood [Radeon HD 5600 Series]
vendor: ATI Technologies Inc
physical id: 0
bus info: pci@0000:01:00.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: vga_controller bus_master cap_list rom
configuration: driver=radeon latency=0
resources: irq:46 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:4000(size=256) memory:c4440000-c445ffff
*-display
description: VGA compatible controller
product: Core Processor Integrated Graphics Controller
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:45 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5050(size=8)
```any ideas?

(When i go to install hardware it gives me a driver, but im guessing its an improper driver.)
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

do i install an inter-graded mother board driver, or a regular one? I just want to utilize my gig of Vram.
Yes...  First look over this post in my sticky:
[http://ubuntuforums.org/showpost.php?p=10950714&postcount=334](http://ubuntuforums.org/showpost.php?p=10950714&postcount=334)

You know you have switched graphics on a hybred video chipset right (ATI/ATI)?  So getting the correct driver version for you is really important... and that is a major understatement.  Also the "how" it is installed is also important.  That post I refereed to is up-to-date on current info as of a today.

Tell me how it goes.

---

