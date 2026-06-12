---
title: "Web server, ssh daemon not running"
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by agger on 2010-03-31
Suddenly, meaning in the last few days, the apache server and the SSH daemon on my laptop are not running after login on my laptop.

Does anyone know of a solution? It seems the daemon scripts in /etc/init.d/ are not run. This used to work fine until a couple of days ago.

Some months ago there was a similar problem, due to the latest version of upstart, which will not start these services if the network interface is not connected during boot (which it isn't, since I'm using a wireless network interface which connects when the user logs in).

The solution was to downgrade upstart from 0.6.3-10 to 0.6.3-11.

Now it seems that even though I thought I locked to 3-10, 3-11 was installed during an upgrade, so I'm having to downgrade it yet again to have the daemons started. Does anyone know if there's a LASTING solution to this problem in Ubuntu 9.10?

Also, does someone know if this problem is also present with the version of upstart in Lucid?

TIA for any response :-)

---

### Post by agger on 2010-03-31
> **agger said:**
> 

Now it seems that even though I thought I locked to 3-10, 3-11 was installed during an upgrade, so I'm having to downgrade it yet again to have the daemons started. Does anyone know if there's a LASTING solution to this problem in Ubuntu 9.10?



Sorry if my tone sounds slightly frustrated, but as I'm using the web server and SSH daemon all the time for sharing stuff around the house, it's a bit unnerving when these services are suddenly not run automatically.

My understanding is that the new version of upstart does this when there's no network connection during boot, but I have no idea WHY it does that - it seems illogical, as apache and SSH will run fine over the loopback interface and I actually do this all the time to test new web pages etc. Can anyone enlighten me?

And once again, thanks in advance :-)

---

