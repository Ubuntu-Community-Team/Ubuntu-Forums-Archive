---
title: "Install on Dell Vostro 360 - Dual screen won't work"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by derekdreery on 2013-02-06
Hi

I'm installing ubuntu on my Dell Vostro 360, and with the following boot options, I can get into a HD system

```
GRUB_CMDLINE_LINUX_DEFAULT="drm_kms_helper.poll=0 acpi_osi=Linux acpi_backlight=vendor"
```however, I am using dual monitors, and when the second monitor is plugged in, the first monitor turns off (after booting from grub, both screens are on during grub).

My current way of dealing with this is to unplug the second monitor during boot, and then plug it in once the desktop is loaded, at which point it is recognised and I can use the dual screens.

Is there a way of avoiding this?

Thanks

---

### Post by derekdreery on 2013-02-08
bump

---

