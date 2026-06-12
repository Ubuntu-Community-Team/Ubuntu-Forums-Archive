---
title: "Package problems after upgrading"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by teeler on 2006-07-18
I just upgraded my last machine to dapper only to have the weirdest problems ever.

during the upgrade, two packages (lighttpd and dovecot) required that I ask whether or not to keep the configurations and i just hit the default (N was the default which i gather from reading the description meant "keep")

Anyway it destroyed my dovecot and lighty instances, so i kept the conf's i had, tried to apt-get remove both the packages and they still didn't work.

So i apt-get removed them again and removed any trace of the package (including their configurations in /etc and their startup scripts in /etc/init.d).

Then i re-installed again and now neither package is creating init scripts OR configuration directories. I looked through man dpkg to try to find something (dpkg-reconfigure ?) but nothing works.

Help? please? ;)

---

### Post by teeler on 2006-07-19
Oooook then, fixed it myself.

Tell me if i get this wrong,
it seems that apt (or dpkg) keeps state information about if configs are installed or not. After trying apt-get --purge remove several times and realizing that it wasn't going to magically work, I opened dselect, marked the packages i wanted complete removal of with a "_", and removed them.

THEN they were gone. It's like apt thought the configs were already installed but actually werent - so i had to force it to flush everything out, then when I re-installed lighty and dovecot I got everything back. 

Then i only had to reconfigure dovecot because the configuration completely changed....

But! Its all better now. 
Hope this helps someone else.

---

