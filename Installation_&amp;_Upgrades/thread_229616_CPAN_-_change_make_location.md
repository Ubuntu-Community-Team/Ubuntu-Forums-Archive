---
title: "CPAN - change make location"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2006-08-04
Before I realized the make was not installed, I ran sudo perl -MCPAN -e shell
and then when prompted for make location, I entered a directory. Big mistake. I made a symbolic link (after installing "build-essential") from the directory ( ln -s make /usr/bin/make) - still "install XML::Parser" not able to make.  Can I change the make location in cpan or how can I remove it all and start over?  :rolleyes: OOPS

---

