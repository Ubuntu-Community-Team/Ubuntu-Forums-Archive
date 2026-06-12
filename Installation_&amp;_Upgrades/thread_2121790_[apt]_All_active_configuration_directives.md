---
title: "[apt] All active configuration directives"
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by Rexilion on 2013-03-03
A few years ago, I used to have Debian. I used preseeding to do most of the heavy lifting during installations. Now I just install Ubuntu CLI (cli.seed) and then install all the packages listed in a specific file (packagelist). This allows me to have a barebone installation of just 3,2 GiG without the additional hassle of a preceed.cfg.

However, this is a PC meant for my parents. So now, I also need to tweak apt's behaviour with respect to updates. I already installed update-manager and aptdaemon and the program seems to work.

BUT, I wanted it to upgrade the packages without recommends. I did find a source on the internet for this:

[QUOTE=http://forums.debian.net/viewtopic.php?f=16&t=62112]APT::Install-Recommends "false";
APT::Install-Suggests "false";[/QUOTE]

I hope the update-manager honours this though. My question is: **I checked 'man apt.conf' for these directives, but they were not listed there. So where does one find one central document explaining all these directives? Is there such place? Google yields nil :(**

---

