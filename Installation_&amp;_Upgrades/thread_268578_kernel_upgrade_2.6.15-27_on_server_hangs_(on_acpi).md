---
title: "kernel upgrade 2.6.15-27 on server hangs (on acpi)"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by bioborg on 2006-09-30
Kernel 2.6.15-25-server works fine, when I upgrade to 2.6.15-27, it hangs.
When I installed from the 6.06.1 disk, it hung on 2.6.15-26

right after
Uncompressing the kernel

there was a blinking cursor, the screen flashed, then the cursor was solid.  nothing.  I rebooted into recovery mode, then it showed more stuff before it hung, the last thing was something like: [475692-590000] Acpi- Thermal Something 47c
then it hung.
So, I got rid of the new kernels, and everything seems fine.  But I would think there should be some security reasons why I may want to upgrade sometime.  What's going on here?

---

### Post by LittleBot on 2006-10-14
I'm running into the same issue.  Have you had any other information about this?  Anything besides downgrading to solve the issue?

---

