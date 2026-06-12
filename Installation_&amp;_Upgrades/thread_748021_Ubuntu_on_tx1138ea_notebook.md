---
title: "Ubuntu on tx1138ea notebook"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by sikong on 2008-04-07
PLease help me.....
I'm trying to install ubuntu on a tx1138ea notebook hp pavillion.
I am totally new to linux hoping to learn it through use (the best way).
Managed to get it on hard drive with swap partition but as its booting it fails on the third bar did nosplash option and it hangs at loading hardware drivers.
Any advice would be very much appreciated thanks simon

---

### Post by dstew on 2008-04-07
> Managed to get it on hard driveJust to be clear, you are booting (or trying to boot) the Ubuntu system that is installed on the hard drive, correct?

If it stalls at loading hardware drivers, it is likely that a driver is not working with the kernel and hardware. The systems most often at fault are the ACPI, the APIC, and the graphics display adapter.

You can use different boot options, like you did for nosplash, by pressing F6 at the opening screen. The first to try would be to boot in Safe Graphics mode. If that doesn't help, disable the ACPI with **acpi=off**. If that doesn't work, disable the APIC with **noapic nolapic**.

If none of this helps, post back. If you get it to boot, post back, and we can help you fix the problem permanently.

---

### Post by sikong on 2008-04-08
Thankyou thats done the job just ran as normal except I included noapic worked great. I could see myself getting into linux its easier then trawling through millions of probs like say vista and loads in a fraction of the time. Thanks:guitar:

---

