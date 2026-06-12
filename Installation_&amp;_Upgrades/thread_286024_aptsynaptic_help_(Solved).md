---
title: "apt/synaptic help (Solved)"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by neocon2005 on 2006-10-27
I just upgraded from dapper to edgy. Most programs work fine. I have one major problem though. When I try to install any program via command like, for eg:
sudo apt-get install gnome-splashscreen-manager

I get the following error message (after it has downloaded the packages):
dpkg: syntax error: unknown user `amavis' in statoverride file 
E: Sub-process /usr/bin/dpkg returned an error code (2)

Any help would be greatly appreciated. Thanks in advance.

---

### Post by aysiu on 2006-10-27
Read [this](http://www.linuxforums.org/forum/ubuntu-help/67252-automatic-udates-not-working.html).

---

### Post by neocon2005 on 2006-10-27
Thank you very much aysiu. I deleted the lines with the offending reference to amavis in /var/lib/dpkg/statoverride and everything is hunky-dory now.

I feel great to belong to the awesome Ubuntu community. Keep up the good work folks. The forum defines the true spirit of Ubuntu - I am what I am because we are what we are!

---

