---
title: "What exactly to delete in the boot file to complete uninstallation?"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by An Exile on 2010-03-27
Uninstalled wubi (though I enjoyed Ubuntu I want to do a clean install instead of the wubi/windows piggy-back). However, I still get an option to choose ubuntu when rebooting. I know that there's something I need to delete in the boot.ini file, but all I read is "delete mentions of ubuntu" or "delete the ubuntu line".

I hope I'm understandably wary of just waltzing into the boot file and deleting something like this, so what **exactly** do I delete from the boot.ini file to complete the uninstallation?

This is what I have in the boot file:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

```

So all I delete is the "C:\wubildr" line? Or does all that do is remove the mention of ubuntu from the startup menu but I still need to choose XP as the OS I want to boot into during startup?

---

### Post by stlsaint on 2010-03-27
maybe this will help. [Wubi]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20uninstall%20Wubi?").

---

### Post by adam814 on 2010-03-28
Just the last line will do it.  If you've already uninstalled Ubuntu through Windows the entry won't boot anyway.

---

