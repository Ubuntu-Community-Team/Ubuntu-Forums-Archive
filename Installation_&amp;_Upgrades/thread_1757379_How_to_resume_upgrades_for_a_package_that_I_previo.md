---
title: "How to resume upgrades for a package that I previously downgraded..."
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by mgleahy on 2011-05-13
Hello,

I recently did an upgrade on a VPS from 10.04 LTS to 10.10.  It worked fine, though I boldly upgraded the 'held-back' package for upstart.  Eventually, this turned out to raise some serious complications with several services that would no longer start (including cron, rsyslog, and dovecot).

I tried downgrading upstart and other various packages using the following command (without success):

sudo apt-get install upstart=[version]

I noticed today, after having upgraded the VPS to 11.04, there was a new upstart package, which was 'held-back'.  So I upgraded to it with:

sudo apt-get install upstart=0.9.7-1

Fortunately, this seems to have resolved the problems with the services being able to restart on the server.  So...my question now is, how do I get apt/Ubuntu to resume upgrading this package normally?  Ideally, I don't want to have to manually install specific versions each time there's a new update.

Thanks in advance for any suggestions.

---

