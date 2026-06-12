---
title: "Resume scripts"
date: 2009-09-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zeimusu on 2009-09-20
In 9,04 there were scripts in /etc/acpi/resume.d/ that were run when the computer resumed from suspend. I managed to get my wacom table running after resume by editing them. That directory doesn't appear in 9,10. I've heard that power management has been changed, does anyone know if there is an equivalent.

What I really want to do is run the command "modprobe -r wacom && modprobe wacom" after resuming. I find that removing and re-inserting the wacom module will get the tablet working again - I've tested by hand in 9.10 and it does work, but I'd like to automate it.

-----
Solved:
The corresponding files are in /usr/lib/pm-utils/sleep.d/

---

