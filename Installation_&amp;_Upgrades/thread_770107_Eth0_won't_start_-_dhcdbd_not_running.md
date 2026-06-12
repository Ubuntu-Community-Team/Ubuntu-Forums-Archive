---
title: "Eth0 won't start - dhcdbd not running"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by tsaotablem on 2008-04-27
Hi,
I'm having trouble since upgrading from Gutsy to Hardy: no internet connectivity.  It looks like I'm unable to obtain an IP address.
In /var/log/syslog I see complaints about dhcdbd not running.  I'm not sure how to correct that?  In /var/log/messages there is also an error message related to dhcdbd saying it failed to autolaunch D-Bus session and on the same line it says X11 initialization failed.
I expect if I could restore my internet connection I could tidy up the rest of the little issues I'm having (broken openoffice.org packages that need fixin').
Any help is appreciated, and please be kind as I'm a noob.

Thanks!

---

### Post by Peter09 on 2008-04-27
Can you provide more information of the specification of your machine and internet connection?

PC

---

### Post by tsaotablem on 2008-04-27
It's old.. it's a P3-866, but it had no problem running Gutsy.
What kind of information would help regarding the internet connection?  I can tell you it's plugged into a cable modem via a router, but other machines on the router are having no issue so I know it's not that.

---

### Post by tsaotablem on 2008-04-28
Just in case someone does a search and comes across this, I fixed the net connection by tinkering with the settings (I think 'roaming' was enabled; as I recall I disabled that and flipped on the DHCP switch and I got reconnected).

I had 18 broken packages all related to OpenOffice, and after trying several times to repair them (Synaptic just closed itself whenever I tried to 'apply changes') I gave up and just removed them.  System seems to be fine now.. I guess?

---

### Post by bwilson on 2008-05-19
I had a somewhat b0rked upgrade from 6.10->7.04->7.10 on my MythTV box. At reboot mysql didn't start, so mythbackend was unhappy. After much (*much*) spelunking of logs and Google(TM) searching, I found this post. Sure enough, my eth0 was in roaming mode. A quick fix in Network Manager and viola! The box is happy again. mysql starts at boot and mythbackend is happy.

Thanks again.

---

