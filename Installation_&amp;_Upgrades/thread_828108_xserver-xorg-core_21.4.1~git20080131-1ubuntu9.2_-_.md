---
title: "xserver-xorg-core 2:1.4.1~git20080131-1ubuntu9.2 - Can no longer start X."
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by darkangel on 2008-06-13
After installing the above security update, i could no longer start x, i had to force a downgrade to version 9 from 9.2 from the command line.

My system is pretty much stock except hardy-proposed being enabled.
I have an Nvidia graphics card, if it makes any difference. Couldn't find any errors, just kept booting to a terminal.

-- Update --
OK, Think I have the error from daemon.log:

Jun 13 16:47:59 mark-desktop gdm[5325]: CRITICAL: gdm_config_value_get_bool: assertion `value->type == GDM_CONFIG_VALUE_BOOL' failed

---

### Post by avtolle on 2008-06-13
I haven't downloaded that update yet, but I suppose that you will need to reinstall your nVidia driver.

---

### Post by darkangel on 2008-06-13
That's an idea. But assuming this affects people with nvidia cards (or possibly the 6200 only), this going to cause much gnashing of teeth.

---

### Post by luisdavila on 2008-06-13
i have nvidia geforce 6100 and after security-update without problems... i have the nvidia drivers in ubuntu-repositories with kubuntu hardy

---

### Post by darkangel on 2008-06-13
How bizzare! I've installed it again, and it's working fine.

---

### Post by avtolle on 2008-06-13
> **darkangel said:**
> How bizzare! I've installed it again, and it's working fine.
I'll keep this in mind if I run into trouble. Thanks for the update.

---

