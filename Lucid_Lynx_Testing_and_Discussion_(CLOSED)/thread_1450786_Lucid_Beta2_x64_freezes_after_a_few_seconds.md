---
title: "Lucid Beta2 x64 freezes after a few seconds"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by comandrei on 2010-04-09
I just installed Lucid beta2 X64 on one of my machines (a 5-year old Sempron 3000+ with 1,5 Gb of RAM on a Gigabyte GA-K8NS rev2).

After lucid boots, I log in , manage to start a few programs and all of the sudden, it freezes.
I started linux in recovery mode, I blacklisted vga16fb,( in /etc/modprobe.d/blacklist-framebuffer.conf and in the kernel boot line), blacklisted the nouveau driver (I think it was the driver).Same result.

In recovery mode all is good, nouveau driver is loaded (i get a 1680 x 1050 console!) and no freezes.
I have no idea why this happens, but I think it could be related to X, or nouveau. ( I have a working beta2 on my laptop which has an Intel chipset and onboard videocard).

---

### Post by cariboo on 2010-04-09
Can you post your /var/log/Xorg.0.log, so we can see what errors you are getting, if any.

---

