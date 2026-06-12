---
title: "Poweredge r750 install failing at user information everytime"
date: 2022-12-06
forum: Installation &amp; Upgrades
---

### Post by mo-matic on 2022-12-06
Trying to build a poweredge r750 and come against an issue where unless the nics are disabled the OS won't install just crashes out at the user information.

The installation being used is server 22.04 LTS.

If i try to configure the disabled bond with an Ip address using netplan after the OS is installed then get the message that the one of the interfaces in the bond is not defined.

The poweredge r750 is the certified spec on the ubuntu website.

Have built a few of these in last couple of weeks without any issues.

Have downloaded the iso twice as thought might be corrupt.

The install iso is being done through the idrac.

Cheers

---

### Post by MAFoElffen on 2022-12-08
What is the output of 
```

ls /sys/class/net | sort

```

---

