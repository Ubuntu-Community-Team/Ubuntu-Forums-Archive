---
title: "NVIDIA xorg.conf alternative"
date: 2020-05-24
forum: Installation &amp; Upgrades
---

### Post by curts on 2020-05-24
I stumbled upon this [NVIDIA config enhancement]("https://wiki.debian.org/NvidiaGraphicsDrivers/Configuration") yesterday and I believe it should be added to the Ubuntu 20.04 repo packages for installing the NVIDIA binary driver. In addition to creating both the directory and file, it should be documented in the release notes that user additions to the NVIDIA configuration should be made to this file, instead of replacing it with a custom '/etc/X11/xorg.conf' file as we have traditionally done.

[INDENT]The driver options below can be included for increased performance:

/etc/X11/xorg.conf.d/20-nvidia.conf

```
    Section "Device"
            Identifier "My GPU"
            Driver "nvidia"
            Option "NoLogo" "1"
            Option "RenderAccel" "1"
            Option "TripleBuffer" "true"
            Option "MigrationHeuristic" "greedy"
    EndSection
```[/INDENT]

---

