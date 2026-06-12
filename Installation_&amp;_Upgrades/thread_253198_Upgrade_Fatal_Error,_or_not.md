---
title: "Upgrade Fatal Error, or not?"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by Boelcke on 2006-09-07
I just (finally) upgraded my system from Breezy to Dapper.  I used the update button on the Update Manager, right over the Internet.  Everything seemed to go great, until right at the end, during the "cleanup" stage, when it apparently choked over one or two packages that it didn't like anymore.  It had just given me a message about no longer supporting certain packages (they'd be going to universe), I hit OK, and WHAM -- Fatal Error.

I have the /var/log/dist-upgrade.log file if needed.

The strange thing is, it does seem to have upgraded.  Gnome looks slightly different, when I first opened Firefox it said welcome to Dapper 6.06.

I went and upgraded the packages that seemed to choke it:
enigma (0.92-1) to 0.92.2-1ubuntu1
gnome-cups-manager (0.31-0ubuntu3) to 0.31-1.1ubuntu13
python-netcdf (2.4.9-2ubuntu1) to 2.4.9-3ubuntu2

And, so far, I seem to be running Dapper.  Do I have a messed-up system, or do you think I'm OK?

---

