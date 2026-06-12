---
title: "[SOLVED] Suspend to ram no longer works."
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by fahrenheit_210 on 2008-09-18
Suspend to ram has always worked on my Compal IFL90, be it with Gutsy, Hardy, or Intrepid, that is until a few updates ago.  After a batch of updates that included hal and acpi related packages, suspend stopped working.  Apparently Ubuntu believes my laptop does not support suspend to ram:

```
$ gnome-power-cmd.sh suspend
Suspending
Error org.freedesktop.PowerManagement.NoHardwareSupport: Suspend is not available on this computer
```

Any ideas as to what may have changed or things I could fiddle with that might help suspend to work?

---

### Post by pakraticus on 2008-09-18
I could be mistaken but I believe that the problem is that pm-utils checks for s2ram from uswsusp (/usr/lib/pm-utils/module.d/uswsusp)
uswsusp does not include s2ram on debian
/usr/share/doc/uswsusp/README.Debian:
Ubuntu specific notes
---------------------

The s2ram binary is not included in the Ubuntu package. Equivalent
functionality is provided by acpi-support.

-- Matthew Garrett <mj59@srcf.ucam.org>

So /usr/lib/hal/hal-system-power-pm-is-supported returns false to gnome-power-management.

The old pm-utils implementation would invoke hal-system-power-pmu sleep or just dump "mem" to /sys/power/state.

I'm going to try and create two new modules for pm-utils and give the brutish one a spin on my thinkpad and send a patch in with the bug report.

---

### Post by fahrenheit_210 on 2008-09-18
I believe you have pinpointed the problem.  Downgrading to the pm-utils_0.99.2-3ubuntu9 package from Hardy fixes suspend for now.

Thanks for the help!

---

### Post by Nullack on 2008-09-18
Would you please consider adding that to an existing bug report or if none exists doing a new one. By helping to fix it in Ubuntu, imagine how many other people your saving from having the same experience :)

---

### Post by pakraticus on 2008-09-19
Already submitted on launchpad with a patch.  Final summary of problem, SLEEP_MODE was getting set based on presence of s2disk instead of s2ram, but uswsusp module for pm-utils would invoke s2ram for sleep.

---

### Post by fahrenheit_210 on 2008-09-19
pakraticus has the fix in bug report [_#267141_]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/267141").

Marking as solved.

---

