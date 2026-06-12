---
title: "Ubuntu 22.04.4: Lenovo T480s trouble with kernel 6.5.0-25"
date: 2024-03-12
forum: Installation &amp; Upgrades
---

### Post by xcel102 on 2024-03-12
Hi everyone, I'm a regular Linux user at work but not a developer or  sysadmin, and need some help troubleshooting a laptop at home.

After  experiencing Windows 11 on the work laptop, I decided when Windows  10 reaches EOL, I'll switch my main computer at home to Linux. So a  week or 2 ago I started evaluating Kubuntu 22.04.4 on a spare laptop.  Things were fine until this weekend, when it offered some updates that  included upgrading the kernel from 6.5.0-21 to **6.5.0-25**.  After the upgrade (and reboot), either the boot will take a long time  or things are non-responsive after logging into the desktop. It's  consistent so the computer isn't usable with the new kernel.

I  switched back to the older kernel, and things work fine. But 6.5.0-25 is  consistently broken. I did some more characterization:

[LIST=1]
[*]Kernel 6.5.0-25 causes the problem on both Kubuntu and Ubuntu 22.04.4 on this machine.
[*]Secure Boot doesn't matter.
[*]Reinstalling from scratch doesn't help.
[*]Encrypted LVM doesn't matter.
[*]Other updates besides the kernel upgrade don't seem to contribute: I did one install with no updates during the installation. After booting up, I upgraded only the items checked in the attached screenshot, and the trouble is introduced.
[/LIST]

I did try things on another laptop, and the issue isn't present there. So this is specific to one laptop model.

The laptop with the problem is a **Lenovo T480s**:
[LIST]
[*]Intel Core i5-8350U
[*]Mesa Intel UHD Graphics 620 (KBL GT2)
[*]8GB RAM
[*]Storage is a 512GB NVMe I bought on Amazon (Fikwot FN500 512GB NVMe SSD 3D NAND 1.3 PCIe Gen3 x 4 M.2 2280)
[/LIST]

The laptop without the problem is a Lenovo T430:
[LIST]
[*]Intel Core i5-3360M
[*]Mesa Intel HD Graphics 4000 (IVB GT2)
[*]8GB RAM
[*]256GB SSD
[/LIST]

Any guidance for root causing and resolving this is appreciated!

---

