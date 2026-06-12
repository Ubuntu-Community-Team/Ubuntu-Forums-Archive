---
title: "Suspend not available on ppc (PowerBook G4)"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sds50 on 2009-04-13
I have been using the ppc version for a number of years on my powerbook G4. Suspend/resume has always worked straight out of the box.

On a fresh install of Jaunty, I am now unable to suspend at all. The option to suspend is not present in the user-switcher applet or power management applet/preferences, although hibernate is.

Executing 'sudo /usr/lib/hal/hal-system-power-pmu sleep" gives

power-pmu : PMU_IOC_SLEEP failed

In addition stracing this gives (amongst other output) 
open("/dev/pmu", O_RDWR|O_LARGEFILE)    = 3
ioctl(3, PMU_IOC_SLEEP, 0)              = -1 ENODEV (No such device)
close(3)                                = 0
write(2, "power-pmu : PMU_IOC_SLEEP failed\n"..., 33power-pmu : PMU_IOC_SLEEP failed

ENODEV (no such device)) leads me to think that support for this has dropped out somewhere. In addition, the available hibernate option does not work.

Does anyone have any suggestions as to how I could get this working again, or whether I need to be filing a bug report for a regression over Intrepid?

---

