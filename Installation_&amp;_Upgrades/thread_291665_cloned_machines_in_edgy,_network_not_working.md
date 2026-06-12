---
title: "cloned machines in edgy, network not working"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by misterv on 2006-11-02
I typically clone my linux lab using rsync (high school lab). I installed Edgy on one machine, works fine. When I clone computer, clone boots up but networking not working. I deleted /etc/iftab already.
When I try to start network /etc/init.d/network restart I get error messages telling me Network is unreachable and 
execve (/lib/dhcp3-client/call-dhclient-script . . permission denied
There is already a pid file /var/run/chclient.etho0.pid with pid 134993416
blah blah
send_packet: Network is down

This is a huge pain as I don't want to manually install and configure 30 machines, I have a great system that I want to keep using. Please help!

---

### Post by po0f on 2006-11-02
misterv,

Try "recloning" your system, but leave /var/run out of rsync's arguments.  You should probably leave out /dev, /proc, and /sys as well.  These directories will be properly repopulated on boot.  Or, on your repository or wherever you have your system rsync'ed to, go in and manually clean out /var/run.  These are just tiny files saying "Hey, don't start me again, I'm already running!"

---

### Post by misterv on 2006-11-03
Thanks for reply. I left out /var/run and /dev, /proc, and /sys and received same error message. Any other ideas?

---

### Post by misterv on 2006-11-07
Upon further investigation it seems the problem is with getting it to take an ip address from the dhcp server. If I assign a static address in /etc/network/interfaces it works fine. Can I use dhcp on a cloned system. Is some weird file need to be deleted on the image?

---

