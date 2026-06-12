---
title: "Ubuntu 18.04 boots only with acpi=off (probably because of Nvidia hardware)"
date: 2019-01-20
forum: Installation &amp; Upgrades
---

### Post by SNaveenMathew on 2019-01-20
I have Nvidia gtx 1050 Ti hardware. I installed Ubuntu 18.04, but it hangs at a purple screen during normal startup.

After some research I found a fix: acpi=off in grub. Now I'm able to boot but this disabled my touchpad. Also acpi=off seems to be an unsafe setting. Now my laptop seems to overheat and the fan makes lot of noise.

I tried acpi=oldboot but it hangs at the same screen.

Does anyone know a fix for this issue?

EDIT: This issue was solved by starting with acpi=off, installing nvidia driver, blacklisting nouveau and removing acpi=off.

---

