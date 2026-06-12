---
title: "Ubuntu 8.04 does not boot on my Sony vaio"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by Olnex on 2008-06-12
The live cd does not boot, it always gives me:
ACPI: EC: acpi_ec_wait timeout, status = 0, expected_event = 1
EC: read timeout, command = 128
If I use battery, it boots, then I can plug in the power.

this is a bug: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137)

The solution is to remove quiet option.

however, after I remove the quiet option, it gives me another error:
[17.896085] ACPI Error(something-0537): Method parse /execution
    failed I\_SB_.PCIO.LPCB.EC__._REG](Node f7c4af18), AE_TIME
[17.896783] pnp: PnP ACPI init
... something here ...
[18.450851] ACPI: bus type pnp registered

Then the system hangs, any keys can not help, I can only hold the power button to force the machine shutdown and reboot.

A few weeks ago, I installed it and got this problem, but it occurs only sometimes, however, now, it seems this problem occurs every time I boot.

I haven't tried to disable ACPI

---

### Post by Partyboi2 on 2008-06-12
I came across [[COLOR=Blue]this[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137") bug report, seems to effect the sony vaio users, I only skimmed through the report but looks like recompiling your kernel and adding the patch that was attached to the bug report could work.

---

