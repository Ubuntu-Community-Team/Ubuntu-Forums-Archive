---
title: "rc.local problems"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by TimmyJ on 2007-04-23
I just installed the feisty and I'm having trouble getting my /etc/rc.local script to run on boot. My university has a problem with its network where I need to add the following line to my /etc/rc.local file:

echo 1 > /proc/sys/net/ipv4/neigh/eth1/locktime

I've added this and done a 'chmod u+x /etc/rc.local' to make sure that the file can be run but yet after bootup if I do a 'cat /proc/sys/net/ipv4/neigh/eth1/locktime' it still is coming back as 100 and I can't access my school's network.

I also tried editing my /etc/sysctl.conf but after bootup the locktime was still 100. So for some reason I feel like none of these scripts are being run. So the next thing I tried was using the sysctl command and changing the locktime after I had logged in. This kind of worked. I pasted the command I used below

sudo sysctl -w net.ipv4.neigh.eth1.locktime=1

That command ran fine but then upon inspection of the net.ipv4.neigh.eth1.locktime variable again it was set to 0, not 1. I'm not sure why this happened but fortunately for me this was good enough to get my network up and running. The problem now is that the locktime now changes back to 100 (from the 0 it gets set to) randomly throughout the day and I have to re-run the above command. Anyone know what could be wrong with my system or how I can fix it?

---

### Post by TimmyJ on 2007-04-27
bump.

---

