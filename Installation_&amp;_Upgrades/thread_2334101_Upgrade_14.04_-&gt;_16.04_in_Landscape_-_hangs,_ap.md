---
title: "Upgrade 14.04 -&gt; 16.04 in Landscape - hangs, apt-term.log prompt for config"
date: 2016-08-16
forum: Installation &amp; Upgrades
---

### Post by talz13 on 2016-08-16
I started an upgrade from 14.04 to 16.04 last night from Landscape, and this morning I see that it still hadn't completed.  After looking around in the logs, I found /var/log/dist-upgrade/apt-term.log, which shows the last step that ran is waiting for input on a prompt to keep or replace configuration file '/etc/default/rcS'.  Since this upgrade wasn't started from a shell or under screen, it doesn't look like there's any way for me to attach to it and provide the input it is waiting for.

What's the best course of action here?  Kill the upgrade process and try to recover with dpkg commands?  Reboot?  I'd rather not have the install completely hosed, but it can always be rebuilt if necessary (nightly backups).

---

