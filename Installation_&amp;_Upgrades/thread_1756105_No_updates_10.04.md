---
title: "No updates 10.04?"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by rm06 on 2011-05-11
My file server was running 9.10 on which support ended with the latest release so I upgraded to 10.04 which should last me until I have some time to rebuild it properly. This has been running now for about a week and a half. 

I check for updates daily (aptitude update && aptitude safe-upgrade via ssh session) and so far I don't recall a single one. Is there something else I need to update such as the sources.list? I have Chromium installed which used to take daily updates - I'm just wondering if I missed something or need to enable anything additional.

Thanks!

---

### Post by tommcd on 2011-05-12
The LTS versions of Ubuntu are conservative and only receive security updates. It does not seem unusual that there will be fewer updates the further you get into the LTS release cycle.
To see if there are any updates that you may be missing, try running: ```
sudo apt-get update
sudo apt-get dist-upgrade
``` 
Or if you prefer aptitude:
```
sudo aptitude update
sudo aptitude full-upgrade
```
I always use apt-get in Ubuntu in order to maintain consistency with update manager and synaptic.

---

