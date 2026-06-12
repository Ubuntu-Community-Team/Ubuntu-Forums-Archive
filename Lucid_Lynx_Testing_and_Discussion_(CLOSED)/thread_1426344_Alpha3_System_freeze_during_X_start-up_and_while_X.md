---
title: "Alpha3: System freeze during X start-up and while X is running, but only on battery."
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lobello on 2010-03-10
Dear developer group,

my freshly installed and fully updated 10.04 alpha 3 works perfectly fine on my ThinkPad X100e whenever I am on AC power, however, it immediately freezes entirely whenever on battery and X is running.

What I tried already:
[LIST]
[*]tail -f /var/log/syslog: just stops on the freeze, no new line appears, not useful.
[*]acpi=off in grub: no change
[*]disabled various things on start-up in /etc/rc2.d but no change
[/LIST]

Finally, I disabled GDM on start-up and, voila, it worked, no more crashes, but of course also no X anymore. After logging in on the console, the system crashes again on "start gdm".

Any ideas? Right now I'm using the laptop on AC power, so everythings perfectly fine - but it would be nice to be able to use it as an actual portable computer as well ;)

Thank you!!!


lobello

---

