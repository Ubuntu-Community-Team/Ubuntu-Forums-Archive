---
title: "snap upgrade cant upgrade in ubuntu software centre"
date: 2024-09-30
forum: Installation &amp; Upgrades
---

### Post by zzsimonb2 on 2024-09-30
Good afternoon,

Ubuntu snap store can't upgrade itself from ubuntu software centre.
As its open it just barfs at the prospect.. Please see screenshot.

# System Details Report
---

## Report details
- **Date generated:**                              2024-09-30 15:58:10

## Hardware Information:
- **Hardware Model:**                              ZOOSTORM 9872-0187A
- **Memory:**                                      8.0 GiB
- **Processor:**                                   Intel® Core™ i3-4170 × 4
- **Graphics:**                                    Intel® HD Graphics 4400 (HSW GT2)
- **Disk Capacity:**                               2.0 TB

## Software Information:
- **Firmware Version:**                            F4a UM
- **OS Name:**                                     Ubuntu 24.04.1 LTS
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               46
- **Windowing System:**                            Wayland
- **Kernel Version:**                              Linux 6.8.0-45-generic

Kind regards
Simon

---

### Post by ActionParsnip on 2024-09-30
Try:
```

sudo killall snap-store
sudo snap refresh snap-store
```

Source:
[https://askubuntu.com/questions/1411104/unable-to-update-snap-store-cannot-refresh-snap-store-snap-snap-store-ha](https://askubuntu.com/questions/1411104/unable-to-update-snap-store-cannot-refresh-snap-store-snap-snap-store-ha)

---

