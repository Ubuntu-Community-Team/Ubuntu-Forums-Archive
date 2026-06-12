---
title: "Upgrade issues 6.06.1 =&gt; 8.04.1"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by chrispoole on 2008-07-10
I have an older laptop (P4, 2Ghz, 256MB RAM, SiS chipset graphics), that I'd like to get Ubuntu onto.

Installers for 8.04.1 didn't work (RAM issue? Even alternative CD).

So tried 6.06.1 alt CD. Worked a charm!

Networking didn't work properly (it recognised my router's DHCP server, and I could ping google etc., but firefox wouldn't load any sites and Synaptic wouldn't refresh package info.).

So put in 8.04.1 alt CD. Message popped up to run package manager. So clicked that, then clicked "mark all updates", then applied them. Took a while, and told me it needed to stop services like rsync, cron etc. to update.

Everything passed except it couldn't update gnome-desktop because of gnome-server (sorry, can't remember exactly what).

But in short, on reboot the login prompt doesn't appear, it shows shell prompt a few times, refreshes screen then tells me the X Server doesn't want to work, and asks if I want to see more info about it. Clicking no takes me back to shell prompt where I can login with admin username and password, but then what?

I'm new to Ubuntu, not sure what to do next.

---

### Post by Pumalite on 2008-07-10
8.04 needs 340 MB of RAM to run.

---

