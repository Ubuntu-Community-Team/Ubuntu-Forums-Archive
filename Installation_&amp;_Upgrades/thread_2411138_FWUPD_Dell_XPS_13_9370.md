---
title: "FWUPD Dell XPS 13 9370"
date: 2019-01-25
forum: Installation &amp; Upgrades
---

### Post by amilopowers on 2019-01-25
Hello

I have a Dell XPS 13 9370 with NVME SSD and I am running Ubuntu 18.10, GNOME 3.30.1.

I am running Firmware 1.6.3 and want to update to the recently released 1.7.3. Unfortunately fwupd doesn't recognize the BIOS.

```
amilopowers@amilopowers-XPS-13-9370:~$ fwupdmgr get-devices
PM981 NVMe Samsung 512GB
  DeviceId:             f954c7acdf5fab61aeaca1cd71d29ea5ade6992f
  Guid:                 47335265-a509-51f7-841e-1c94911af66b
  Guid:                 8fd4ca73-d0ae-52e8-8977-461435c6f4cf
  Summary:              NVM Express Solid State Drive
  Plugin:               nvme
  Flags:                internal|updatable|require-ac|registered|needs-reboot
  Vendor:               Samsung Electronics Co Ltd
  VendorId:             NVME:0x144D
  Version:              EXA73D1Q
  Icon:                 drive-harddisk
  Created:              2019-01-25

XPS 13 9370 Thunderbolt Controller
  DeviceId:             3d3ebbb6365f66fc939e8235dcb387b2d3050a1b
  Guid:                 4eeb9d07-a96c-56d6-92d3-4a23ee7a6e4a
  Summary:              Unmatched performance for high-speed I/O
  Plugin:               thunderbolt
  Flags:                internal|updatable|supported|registered
  Vendor:               Dell
  VendorId:             TBT:0x00D4
  Version:              33.00
  Icon:                 computer
  Created:              2019-01-25



```

```

amilopowers@amilopowers-XPS-13-9370:~$ fwupdmgr --version
client version:    1.1.2
daemon version:    1.1.2
compile-time dependency versions
    appstream-glib:    0.7.12
    gusb:    0.2.11
    efivar:    34

```


Thanks in advance for your kind help.

---

