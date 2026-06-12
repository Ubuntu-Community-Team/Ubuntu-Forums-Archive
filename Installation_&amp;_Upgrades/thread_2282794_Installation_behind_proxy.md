---
title: "Installation behind proxy"
date: 2015-06-17
forum: Installation &amp; Upgrades
---

### Post by ohms377 on 2015-06-17
I followed some suggestions on installing from CD behind a proxy, in summary:

1) using the trial option
2) setting up apt.conf.d to include proxy settings Acquire::http::proxy "..."
3) exporting http_proxy to the same
4) testing that I can apt-get update --- no problem
5) using ubiquity to finish the installation

The installation is stuck at trying to synchronize to ubuntu's ntp servers.

Why is this step in the installation necessary?  Ntp will fail because it needs to be set up to use port 123 which is blocked by our firewall.

Is there a way around this problem -- is there some way to make the installation skip this step?

Thanks.

---

### Post by TheFu on 2015-06-17
I think the best way is to perform an install without any networking.
Then come back and setup the APT proxy and setup ntpd to point to an internal NTP server from the local network.  Having the correct time is absolutely mandatory for security in a networked environment.

---

### Post by ohms377 on 2015-06-17
I would have done that, but Ubuntu is no longer distributing the multi dvd option that allows installation without any networking.
It seems that the installation is dependent on having networking -- am I overlooking something?

---

### Post by Lars Noodén on 2015-06-17
One way that might work could be to modify the preseed.  I haven't done that in ages and ages but it is supposedly doable with 14.04.  There you might be able to skip or modify the NTP setup.  Here is an example of using it for unattended installation: [http://askubuntu.com/questions/122505/how-do-i-create-a-completely-unattended-install-of-ubuntu](http://askubuntu.com/questions/122505/how-do-i-create-a-completely-unattended-install-of-ubuntu)

Edit: here is a more authoritative source : [https://help.ubuntu.com/14.04/installation-guide/i386/apbs04.html#preseed-time](https://help.ubuntu.com/14.04/installation-guide/i386/apbs04.html#preseed-time)

---

