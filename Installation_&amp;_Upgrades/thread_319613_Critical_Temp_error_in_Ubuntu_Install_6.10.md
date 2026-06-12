---
title: "Critical Temp error in Ubuntu Install 6.10"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by oxygen on 2006-12-15
Hey,

When I try and install Ubuntu on my system (with an MSI 945GZM3 mobo) I get a critical temperature error then the machine shuts down. It reports the temp as -248 degrees celsius (which is obviously wrong) shortly before turning off.

Now Fedora Core 6 has the same line appear in the startup log - however it installs and runs fine. Windows XP works fine too.

My assumption here is that ACPI is reporting the wrong temperature - or linux is reading it wrong (and Fedora doesn't care, where as Ubuntu does).

Does anyone know a work around to stop this check? I don't need temperature info so maybe there is a boot option I can disable?

Thanks!

---

### Post by taurus on 2006-12-15
Maybe you need to look in the BIOS and perhaps disable the temp reading from mobo!

---

### Post by oxygen on 2006-12-15
Well I managed to get it to work by adding

```
acpi=off
```

to the boot command.

---

