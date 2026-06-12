---
title: "RAID broken after kernel upgrade"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by dankar on 2007-09-02
When booting my ubuntu 2.6.20-16-server recently upgraded using with latest kernel upgrade I get "mdadm: No devices listed in conf file were found". 

I checked mdadm.conf according to README.upgrading-2.5.3 with no success in finding the device.

/proc/mdstat says:
```
Personalities : [raid1]
md0 : active raid1 sda[0] sdb[1]
      244198464 blocks [2/2] [UU]

unused devices: <none>
```

Any suggestions?

/Daniel

---

