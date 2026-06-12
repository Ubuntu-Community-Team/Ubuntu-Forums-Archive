---
title: "Installed Ibex, getting constant system lockups"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by woolyninja on 2008-11-01
Every time I try to run Ibex - about 5 - 10 minutes after logging in the system completely locks up requiring a hard boot.  I've checked the /var/log/syslog and the .xsession-errors log but neither seem to show any errors.

Does anyone have any suggestions on the best way to troubleshoot this?  If not I'll probably end up going back to Hardy for now.

And if it helps, I also had to add ifconfig eth0 down in the stop) section of alsa-utils to allow the computer to shutdown correctly (same problem as a few other people on the board are having).

---

### Post by hyperdude111 on 2008-11-01
Try fixing all dependencies with
_________________________
Sudo apt-get update
Sudo apt-get update -f
_________________________

When i had hardy I kept getting lockups so i unninstalled pointless bloat like gdesklets and the freezing was less common.

I also found that running a package manager at the same time as songbird caused a lockup.

Good luck fixing it.

---

### Post by woolyninja on 2008-11-01
I'll try that, though I should add that this is a clean install - so I'm guessing it's a hardware related issue.

---

### Post by PardusLynx on 2008-11-01
I upgraded to 8.10 and had problems with graphic card and compiz. Then I made a clean install and had the exact system lock up problem as woolyninja is having. I changed back to 8.04 now. I hope a solution comes.

---

### Post by woolyninja on 2008-11-01
It's starting to look like the freezing may be a compiz issue?  I set the Visual Effects to None and so far no more crashes?  I'll keep this thread updated to see how it goes all day.

---

