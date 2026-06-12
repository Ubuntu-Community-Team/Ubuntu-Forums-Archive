---
title: "Trying to Get DNS2GO startup script to Work"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by tbauer on 2007-11-19
So, I have researched this for a few hours.  Here is the net I am at right now:

I have created a script (dns2go) in the /etc/init.d/ directory ... did a chmod +x to make it an exe ... then did an update-rc.d dns2go start 71 0 2 3 4 5 6 . to get it to run regardless of run state.

I works when I run it manually (type dns2go in the /etc/init.d/ directory) ... but when i do a restart ... no dice ... note ... my definition of 'works' is that in the dns2go application manager the sites flip into 'up' state.  I fished around in logs and can't find any indication if the service (dns2go) failed and if so why.

Thoughts on what I should do next?

Tim :confused:

---

