---
title: "Upgrade ubuntu 19.04 to 19.10 stops"
date: 2019-10-26
forum: Installation &amp; Upgrades
---

### Post by kronocar on 2019-10-26
Hello
I've tried to upgrade ubuntu 19.04 to ubuntu 19.10 but it has stopped at about 80%. 
Last information in the console is:

snapd.failure.service is a disabled or static unit, not starting it.
snapd.snap-repair.service is a disabled or static unit, not starting it.

previously it has been an error with chromium (snap)
What can I do now? May I reboot safely?
Thank you
Carlos

1 - I've interrupted  upgrading with ctl+C and restart upgrade tool but it gives error because there is another process using dpkg.
2 - I've killed  all processes which use dpkg
3 - I run: sudo apt-get install -f but the result is I must run dpkg --configure -a to solve the problem. I do and the result is:

     Configurando snapd (2.41+19.10.1) ...
     snapd.failure.service is a disabled or a static unit, not starting it.
     snapd.snap-repair.service is a disabled or a static unit, not starting it.

4 - It stops for a while (minutes) and it continues when I try to copy the content o the console. I click on the first character and ctrl+caps+right arrow  (I don't know why)
     when it finnaly ends says there are errors:

        - snapd
        - chromium-browser-lion
        - gnome-software-plugin-snap

5 - I run sudo apt-get install -f    it tries to install and update chromium but the result is, again:

     Configurando snapd (2.41+19.10.1) ...
     snapd.failure.service is a disabled or a static unit, not starting it.
     snapd.snap-repair.service is a disabled or a static unit, not starting it.

6 - I kill again all processes wich uses dpkg

7 - Run software update tool but it stops again "configuring snapd"

8 - I stop it and it propose a partial upgrade with the same result:

Configurando snapd (2.41+19.10.1) ...
     snapd.failure.service is a disabled or a static unit, not starting it.
     snapd.snap-repair.service is a disabled or a static unit, not starting it.

It's like a loop..... I don't know what else can I do

Thank you

---

