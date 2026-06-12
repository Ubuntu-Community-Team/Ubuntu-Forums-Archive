---
title: "updating pfring fails freezes on &quot;Cannot get driver information&quot;"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by lubomir.fedor on 2013-10-29
On my Ubuntu 12.04.3 LTS I want to update pfring package (by ntop) provided by pfring_5.6.2-6898_amd64.deb to pfring_5.6.2-6910_amd64. However, during the installation (as well as during the subsequent re-installation or attempts to remove it) the process freezes on ```
Cannot get driver information: No such device
``` and I'm forced to kill it with ctrl+c.
Same happens if I try to run ```
dpkg --force-remove-reinstreq -P pfring
```
So now I'm stuck and can neither install nor remove the package. The error message seems to point towards a problem with NICs. I have two, marked as eth2 and eth5 respectively. ethtool -i on both shows correct output. However, it might have been that during the first install of pfring some time ago one of the interfaces had a different name (eth4 perhaps, but I can't remember for sure). Could that be the problem? How can I fix it? And if there is no easy solution, how can I mark the package as removed without actually removing it so I could try to install the new version by overwriting the old one?

SOLVED:
The problem was indeed in the different NIC -- remove process hanged on stop pf_ring through its init.d script with eth0 instead of eth2.

---

