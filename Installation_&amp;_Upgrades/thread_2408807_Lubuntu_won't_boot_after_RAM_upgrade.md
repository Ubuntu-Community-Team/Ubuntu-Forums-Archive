---
title: "Lubuntu won't boot after RAM upgrade"
date: 2018-12-23
forum: Installation &amp; Upgrades
---

### Post by eff64 on 2018-12-23
Hello,
I am the owner of an old Dell OptiPlex 755 desktop PC. I recently switched to Lubuntu 18.10 Cosmic LXQt 32bit(it was running *slowly *under Mint Sylvia before-which I kept in another partition)and all was well until I decided to add more RAM(had only 2GB before) with a 2GB stick.


 After the upgrade only Mint boots flawlessly and recognizes the whole 4GB while
Lubuntu's loading animation seems to run forever.
When trying to boot in recovery mode I get the following "error":```
[xxx.xxxxxx]ehci-pci 0000:00:1a.7:dma_direct_map_sg:overflow 0x000000011b4c1000+4096 of device mask ffffffff
```.

I tried four different boot options from "Advanced options" in GRUB(.14 "normal" and recovery mode, .13 "normal" and recovery mode) but none will work.
 When I remove the new RAM stick Lubuntu boots, when I replace the old with the new it boots too.

I'm stuck there, any help ?

Regards

---

### Post by oldos2er on 2018-12-24
Run memtest? Sounds like there could be a problem with the new RAM.

---

### Post by ubfan1 on 2018-12-24
Perhaps you need to force PAE, see [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)
but that may be old advice.

---

### Post by eff64 on 2018-12-26
Thanks, I'll try both suggestions.

---

### Post by eff64 on 2018-12-27
After running a quick memtest no errors were shown, forcepae solved it, or seemed to do so.Anyways I now enjoy 4GB on all distros, thanks :)

---

