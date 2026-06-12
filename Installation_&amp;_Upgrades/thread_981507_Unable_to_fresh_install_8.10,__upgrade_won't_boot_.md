---
title: "Unable to fresh install 8.10,  upgrade won't boot new kernel 2.6.27-7"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by sethj2 on 2008-11-13
Unable to install 8.10 kernel 2.6.27.

Tried dist upgrade on 8.4 which was successful, but was unable to boot kernel 2.6.27-7 upon install, when booting in recovery it failed on the line "[ 21.789267] cs: IO port probe 0x3e0-0x4ff :"
Old kernel 2.6.24-21 booted just fine.

Tried a clean install with the regular live install CD, and while it booted, the installation process would not go past the partition step.

I then tried the alternate install CD, which froze after selecting "Install." I tried removing "quiet" from the install line, and it failed on "[4.743805] cd: IO port probe 0x3e0-0x4ff :"
With acpi=off it reported "PNPBIOS fault.... caused a fatal error.... dev_node_info : unexpected status 0x37"

Any ideas?

---

