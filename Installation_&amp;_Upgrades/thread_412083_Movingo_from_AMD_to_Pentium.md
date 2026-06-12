---
title: "Movingo from AMD to Pentium"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by saltydog on 2007-04-17
I have just changed motherboard on my server from an AMD Sempron to a Pentium P4 (Asrock 775i65G). Everything is working fine, exept acpi temperature. I am no more able to check my CPU temp.
Running acpi -t I am getting:

No support for device type: thermal

More on this, from lsmod I have seen that the speedstep_centrino module is loaded, but I am running a P4-3Ghz-HT!

I am sure I have to change something in the configuration of the modules, but don't know what and how..

PS: running Dapper server, kernel 2.6.15-28-686

---

