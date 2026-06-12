---
title: "apt-get / aptitude, waiting for headers..."
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by anystupidname on 2008-09-09
This has been an ongoing problem for a long time but I've just ignored it as much as possible.

There is something about the network here at work that impedes apt-get's ability to function well. Anywhere else, I never see these problems and it happens with any mirror. When installing Debian or Ubuntu (Debian more so than Ubuntu, don't ask me why), the install routine will halt for long periods of time and sometimes say an install step failed and I try again one or more times and it eventually finishes. Same problem after the install when I'm adding applications via synaptic or aptitude on command line. It pauses forever sometimes at [waiting for headers...] I tried talking to IT here (I have no control over the network) and they can't figure it out nor are they very keen on trying to modify the several firewalls the connection goes through to get out to the net. This happens on 2 different networks both of which are routed and firewalled very differently.

Any suggestions would be much appreciated.

I don't have the option of going through a proxy and don't currently have an SSH server that I could use externally (assuming I could figure out how to tunnel apt-get through SSH)

---

