---
title: "Autoinstall on 22.04: early-command to turn off predictable interface naming?"
date: 2024-04-16
forum: Installation &amp; Upgrades
---

### Post by ent-systems on 2024-04-16
I have a working autoinstall user-data file that takes care of a bunch of our requirements on NUC's we install in large numbers. 

I was using the following late-command to set the hostname to the MAC of the primary network interface:

late-commands:
  - echo $(cat /sys/class/net/eno1/address | sed 's/://g') > /target/etc/hostname

Unfortunately, when we need to install on different NUC brands/models, sometimes the interface is not eno1 due to the "predictable" interface naming convention. Irony. 

Could I use an early-command to turn off the predictable interface naming convention so that it gets a consistent interface name on every machine so I can use the above command to set the hostname?

Thanks for any help offered!

---

### Post by ent-systems on 2024-04-16
For anyone trying to do what I was looking to do, the solution I found is a wildcard in the echo command: 

late-commands:
  - echo $(cat /sys/class/net/en*/address | sed 's/://g') > /target/etc/hostname

So any interface starting with "en" works. Tested on 3 different NUC models, all successful.

---

