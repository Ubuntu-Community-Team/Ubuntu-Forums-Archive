---
title: "libc6 2.3.6.6 dependency."
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by xolot1 on 2006-09-23
i just installed ubuntu 6.06.1 desktop edition to eventually be used with mythtv.  for this i needed mplayer. when i apt-get mplayer, i have an unsolvable dependency in libc6.
it requires libc6 (>=2.3.6.6) but 2.3.6-0ubuntu20 is installed
furthermore, an update to libc6 is not available in the repos

how would i go about solving this?

---

### Post by tommcd on 2006-09-23
There were some updates for ubuntu today. One of them was for mplayer. I'm just guessing, but perhaps if you did: 'sudo aptitude update' and then install any updates available; and then install mplayer ( and possibly libc6) this may solve your problem.
In synaptic I have:
mplayer 2.0.99+1, and libc62.3.6-0ubuntu20, and mplayer works fine. I do not have myth tv though.
sudo apt-cache showpkg mplayer shows libc62.2.3.4-1 as dependency.

---

