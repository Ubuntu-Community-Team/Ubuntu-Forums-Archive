---
title: "Dual boot win7 and ubuntu problem booting windows"
date: 2016-05-15
forum: Installation &amp; Upgrades
---

### Post by lanceman2 on 2016-05-15
Hi, I have a laptop with win7 64bit and I installed ubuntu 16.04 as dual boot. Usually when I boot into windows it errors out as shown in the attached image. Has anyone seen this before? If I let it sit for about 30 seconds then restart I can then get to a windows screen saying it errored out and from there I can boot into windows.

[ATTACH=CONFIG]269100[/ATTACH]

---

### Post by oldfred on 2016-05-16
I do not know if this will show anything out of place or not.
Is system BIOS or UEFI?
Grub really only boots working Windows.

 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by lanceman2 on 2016-05-16
I figured it out. I set the line GRUB_GFXMODE=1366x768 for my laptop. I'm learning this as I go. :D

---

