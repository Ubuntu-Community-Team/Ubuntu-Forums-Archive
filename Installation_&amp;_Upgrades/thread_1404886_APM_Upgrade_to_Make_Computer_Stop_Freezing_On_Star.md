---
title: "APM Upgrade to Make Computer Stop Freezing On Startup"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by italianoman421 on 2010-02-11
Two weeks ago my computer started freezing on start up when plugged in. It was suggested to upgrade the APM. What is this and is it not updated through the package update? If not how do I upgrade it?

Thanks

---

### Post by northrup on 2010-02-11
APM (Advanced Power Management) is part of the hardware; specifically, it was introduced by Intel to regulate power consumption on IBM-based personal computers.  This technology is obsolete now, and is completely replaced by ACPI (Windows dropped APM support in Vista).

An upgrade to APM would presumably through a BIOS upgrade.  I don't suggest you actually go through re-flashing your BIOS unless you REALLY know what you're doing; one mistake, and you run the risk of bricking your motherboard.

You can shut off APM in the BIOS (usually); that would probably stop the freezing.  I have problems with ACPI machines running Ubuntu that freeze after waking up, or that will wake up then suddenly go back to sleep permanently until reboot.

---

