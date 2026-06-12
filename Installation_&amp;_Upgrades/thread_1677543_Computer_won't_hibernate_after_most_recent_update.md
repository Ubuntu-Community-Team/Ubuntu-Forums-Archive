---
title: "Computer won't hibernate after most recent update"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by John.b.Goode on 2011-01-28
Hello folks,
Ever since I ran the update, through update manager, that came out yesterday, I have not been able to hibernate. The hibernate light on my computer will blink, and then it will wake up again right away, and I will be presented with the unlock screen that I would normally see after waking up from hibernate. Any ideas?

BTW, I'm running Ubuntu 10.10 on a Thinkpad T400 with the Radeon 3400 series GPU using the proprietary driver.

Thanks in advance!

---

### Post by carlohamalainen on 2011-01-30
Same here with a Thinkpad R500, Ubuntu 10.10 64bit, default video drivers.

```

ii  acpi-support                                     0.137                                             scripts for handling many ACPI events
ii  acpid                                            1.0.10-5ubuntu4                                   Advanced Configuration and Power Interface event daemon
ii  gnome-power-manager                              2.32.0-0ubuntu1                                   power management tool for the GNOME desktop

$ uname -a
Linux r500 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

```

I will try to add some debug info later today.

---

### Post by carlohamalainen on 2011-02-23
> **carlohamalainen said:**
> Same here with a Thinkpad R500, Ubuntu 10.10 64bit, default video drivers.


This looks like a problem with 2.6.35-25. With a completely up to date Maverick install running 2.6.35-24, hibernate works fine.

---

