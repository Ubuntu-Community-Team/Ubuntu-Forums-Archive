---
title: "Dual boot AHCI controller unavailable"
date: 2019-03-07
forum: Installation &amp; Upgrades
---

### Post by donkus on 2019-03-07
Hello,

I'm trying to dual boot Ubuntu 18.04.2 LTS on my PC. When I select "Try Ubuntu without installing" or "Install Ubuntu" in the boot menu, I get a black screen with the following messages
```
[5.631799] bcma: Unsupported SPROM revision: 11
[5.631839] bcma: bus0: No SPROM available
[37.979242] ahci 0000:03:00.0: AHCI controller unavailable!
```

PC specs are:
Motherboard: ASRock Z87 Extreme4
CPU: Intel i5-4670K 3.40 GHz
GPU: GeForce GTX 770 2 GB
Boot drive: Samsung 860 evo 500 GB SSD
Installing Ubuntu off of a burned DVD if that matters

I tried toggling boot options like acpi=off, nolapic, and nomodeset with no luck. Is there anything else I should try?

---

### Post by donkus on 2019-03-07
Update: I disabled my GPU and wireless adapter. Now, when I try to install, I get a black screen for about a minute then the following message is displayed
```
[37.979242] ahci 0000:03:00.0: AHCI controller unavailable!
```

---

### Post by CatKiller on 2019-03-07
You need your hard drive to not be set to RAID in your BIOS. You'll need to install a thing in Windows before you do that, otherwise Windows won't work, apparently. While you're in Windows installing the thing, you'll also want to turn off Fast Boot.

---

### Post by donkus on 2019-03-08
Thanks for the reply! My hard drive is set to AHCI by default, and fast boot is off :/
Might have to resort to using a VM for the time being

---

