---
title: "Dapper with latest updates - weird ACPI"
date: 2006-05-22
forum: Installation &amp; Upgrades
---

### Post by pmantis on 2006-05-22
Hello,
   With Breezy, the lid switch caused the screen to lock, but runing out of batter power never caused a proper shutdown... just an instant poweroff, causing fsck to run on bootup.
   With Dapper, with all updates that I've tried... the shutdown on critical battery problem exists, the lid switch does nothing, and removing the power adapter locks the screen. However, acpi_listen properly produces:

# acpi_listen
button/lid LID 00000080 00000006
processor CPU0 00000080 00000000
battery BAT0 00000080 00000001
battery BAT0 00000080 00000001
processor CPU0 00000080 00000000
battery BAT0 00000080 00000001
battery BAT0 00000080 00000001
battery BAT0 00000080 00000001

I checked System-->Preferences-->Power Adapter, and it's set to shutdown when battery is critical, and blank screen when the lid is closed.
I have an HP Pavilian dv1439us

Please give suggestions for troubleshooting steps.

Thank you!

---

### Post by gregh on 2006-05-30
I can confirm this si a problem hith a HP dv5000, how can this be addressed?

Anyone have any guidance at all?

-Greg

---

