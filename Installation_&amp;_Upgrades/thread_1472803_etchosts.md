---
title: "/etc/hosts"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by cspence on 2010-05-04
I'm posting this both as for a question and in case it helps someone, since I may have solved this problem.

I upgraded from karmic to 10.04, and had trouble with my home directory. My machine is on my company's network, which uses nis and automounting for home directories. Even though my home directory is actually on my machine's disk, the admins set up everything uniformly, so my home directory is automounted, even on the exporting computer. When I upgraded, it stopped automounting my home directory, so I couldn't get to it in the expected way. I could get to it from other machines.

There were lines in /var/log/daemon.log like
[INDENT]May  3 10:33:46 cholla mountd[7018]: refused mount request from 127.0.1.1 for /export/home/cds (/export/home/cds): unmatched host[/INDENT]

The problem seem to be a line in /etc/hosts, which says

[INDENT]127.0.1.1  cholla[/INDENT]

I assume this wasn't there before upgrading. I commented this out and rebooted, and everything seems to work fine. But should I expect to have broken something?

---

