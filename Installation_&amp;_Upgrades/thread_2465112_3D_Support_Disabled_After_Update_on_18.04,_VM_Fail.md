---
title: "3D Support Disabled After Update on 18.04, VM Fails to Open"
date: 2021-07-22
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2021-07-22
Saw updates today (22 July 2021) for Nvidia and Xorg and thought nothing of it. Accepted the updates and no reboot required.

Opened VirtualBox and it failed to open Session for Virtual Machine - with this message;

> 
This VM was configured to use 3D acceleration. However, the 3D support of the host is not working properly and the VM cannot be started. To fix this problem, either fix the host 3D support (update the host graphics driver?) or disable 3D acceleration in the VM settings (VERR_NOT_AVAILABLE).


Pretty sure I need 3D acceleration due to the fact I am running Charting Software. The FIX required is update graphics driver which Ubuntu 18.04 just did!

Now What ??? Must get my Charting Software on VM back up and running. Perhaps this is a Bug I should report?!?!? As the screensaver won't run either!

Thanks!

---

### Post by deadflowr on 2021-07-22
Even though it did not require a reboot, did you do one anyway?

---

### Post by MAFoElffen on 2021-07-22
A few things... Agreed with deadflwr: If NVidia, even if not a Kernel Update, yes you would need a reboot for it to finish the update.

- You didn't mention which NVidia hardware you had, nor the driver you were on, and what it updated to. Are you using an Ubuntu Alternate Driver (proprietary, NVidia) or *Nouveau*?
```
sudo lshw -C video
```
- You didn't mention what flavor of VirtualBox you were using, from the Ubuntu Repo's or straight from Oracle.

---

### Post by Rick St. George on 2021-07-22
Software & Updates reports;

Using NVIDIA driver metapackage from nvidia-driver-390 (proprietary, tested)

Also,

```

 sudo lshw -C video
 
  *-display                 
       description: VGA compatible controller
       product: GF119 [GeForce GT 610]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:42 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:d000(size=128) memory:c0000-dffff


```

As for VirtualBox ... believe straight from Oracle via Deb. installed years ago!

But after Reboot - Rechecked the box for 3D and 2D Acceleration under Display, and VM started up OK!
So, No Problem after all. Case Closed. Above is for Reference then only.

Thanks Guys!

;-)

---

### Post by MAFoElffen on 2021-07-22
Good, please mark this a solved then...

---

