---
title: "How do I load openchrome in Ubuntu 10.10?"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by .haNk on 2010-10-22
It seems like support for my Via video card (chip? it's onboard...) has nosedived since 10.x. I think the module I want to load is openchrome, but I'm not sure how to do this. It doesn't exist in /lib/modules and I don't have an xorg.conf file.

The package "xserver-xorg-video-openchrome" is already installed. Any ideas?


lshw:
=============
           *-display UNCLAIMED
                description: VGA compatible controller
                product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=32 mingnt=2
                resources: memory:f0000000-f3ffffff memory:f4000000-f4ffffff memory:f5000000-f500ffff
=============

---

### Post by .haNk on 2010-10-23
bump

Anyone?

---

### Post by Nicholas Coltinne on 2011-01-30
Também tenho o mesmo problema e ja tentei de tudo, mas nada resolvel.

I also have the same problem and I tried everything, but nothing to solve it.

---

### Post by Alesandro on 2011-06-23
The driver is enabled by default when xserver starts. See in /var/log/Xorg.0.log after login.

You can generate a xorg.conf using:
```
Xorg -configure
```then copy it to /etc/X11.

---

