---
title: "Maverick very slow"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by jleach on 2011-01-23
I did a clean install of Maverick netbook edition yesterday.  I needed to have a dual boot of XP for work reasons (don't ask!), hence the reason to take my previous version of Maverick (upgraded from Lucid) off. All seemed well until today when after about 5 mins use the system becomes unusable.  It is almost as if a timed procedure is taking place.  Looking at system resources, the system resource app can take upto 96% of CPU which seems very odd. This is generally whilst only running Chrome and Thunderbird.  Looking at previous threads, there has been a problem with the kernal, but I am using the most recent, which I believe is the version least likely to cause problems.

Samsung NC 10
2Mb RAM


Any suggestions please.

Thanks

Jonathan

---

### Post by dino99 on 2011-01-23
this can be due to different reasons: use either "top" or "system manager" to find which id process or app is over using ram.

Then you can kill that process then restart it. If things are still bad, remove/purge then reinstall that app (with synaptic), sometimes deleting its hidden config file into /home (take care to saved important data inside, rename it for example, reinstalling or rebooting will recreate that hidden file)

Of course you need to consider to deactivate some cosmetic effects that like ram to much.

If you meet serious troubles, dont forget to watch at errors & warnings logged into .xsession-errors & into "system admin logviewer", they are often usefull to fix issues.

Some usefull commands to run into a terminal:
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

---

