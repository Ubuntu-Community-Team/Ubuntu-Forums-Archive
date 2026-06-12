---
title: "Installing Intel Graphics driver for Ubuntu Lucid"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by Xybrek on 2013-09-09
How do I install Intel Graphics driver for Ubuntu 10.04 LTS (Lucid):


    $ sudo lshw -C video
      *-display UNCLAIMED     
           description: VGA compatible controller
           product: Intel Corporation
           vendor: Intel Corporation
           physical id: 2
           bus info: pci@0000:00:02.0
           version: 09
           width: 64 bits
           clock: 33MHz
           capabilities: msi pm bus_master cap_list
           configuration: latency=0
           resources: memory:c0000000-c03fffff memory:b0000000-bfffffff(prefetchable) ioport:4000(size=64)


Model


    $ lspci | grep VGA
    00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)


Kernel


    $ uname -r
    2.6.32-51-generic-pae


I know my Ubuntu version is very old, but there are some reasons that I cannot upgrade, so is there still a solution for this?

My main goal is to increase the resolution of my laptop to 1280x800 which is the resolution I get when running Windows OS on it.

---

### Post by varunendra on 2013-09-09
Welcome to the Forums Xybrek !
> **Xybrek said:**
> I know my Ubuntu version is very old, but there are some reasons that I cannot upgrade, so is there still a solution for this?

May we know the reasons due to which you can't upgrade? Maybe solving those problems could be easier than working on an outdated system.

By the way, most Intel cards are supported by i915 driver, so please post back the outputs of :
```
lspci -nn | grep VGA
modinfo i915
```

---

