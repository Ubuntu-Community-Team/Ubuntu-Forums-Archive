---
title: "nvidia problem"
date: 2018-07-27
forum: Installation &amp; Upgrades
---

### Post by thomas_j_marshall2 on 2018-07-27
I have on-board radeon graphics and a recent update left me with a  very low resolution, couldn't use the radeon set up at all so I bought  and installed a nvidia card.  Initially Ubuntu was running x-org so I  installed the nvidia proprietary and it crashed Ubuntu.  It worked to a  certain version but an update made it unusable.  In my new installation  now I am on x-org but at login the mouse freezes and entering password  using tab is soooo slow.  Once in everything is OK.  This happened on my  old install using both x-org and nvidia.  Not sure if this is connected but if I attempt to go into settings the screen goes black and then returns to login.  Any ideas?

---

### Post by thomas_j_marshall2 on 2018-07-27
Should have said: Ubuntu 18.04, Nvidia GeoForce GT 1030, Asus A88xm plus.

---

### Post by Bashing-om on 2018-07-27
thomas_j_marshall2; Hello -

In 18.04 with the Wayland desktop the proprietary nvidia driver is a work in progress.
Show us what we have now to work with:
```

sudo lshw -C display
dpkg -l | grep -i nvidia
lsmod | grep nvidia
lsmod | grep radeon
cat /var/log/gpu-manager.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

See what tale gets told
[INDENT][INDENT]and what we can do about it
[/INDENT][/INDENT]

---

### Post by thomas_j_marshall2 on 2018-07-28
*-display                 
       description: VGA compatible controller
       product: GP108
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:37 memory:fd000000-fdffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:c0000-dffff

---

