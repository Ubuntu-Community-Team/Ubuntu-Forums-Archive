---
title: "Natty on Lenovo S12, the bumpy road to unGnome."
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by keepitsimpleengr on 2011-08-04
Not being very fond of Natty's new unGnome interface, I decided to install it on my little laptop, where if I wanted I could demo it to others who might like it.

So I installed it.  After a few weeks, it would fail at boot, presenting only colorful garbage on the screen.  Same in recovery mode.  

Sigh.

Reinstall, booted a few times, died again.

Reinstall, never booted.

Repeats, about six, various tricks learned over the years.  One attempt failed to install bind9!, so even though I could connect to the Internet, I could only ping the DNS server.

Finally I reinstalled with no connection to the Internet. And got it to stay up long enough to apply the changes from Chris' Blog ([HTTP://fakkelbrigade.eu/chris/blog/2010/12/wireless-not-working-in-ubuntu-on-the-lenovo-ideapad-s12/](HTTP://fakkelbrigade.eu/chris/blog/2010/12/wireless-not-working-in-ubuntu-on-the-lenovo-ideapad-s12/)) &#8943; killing off the superfluous and evil acer_wmi module, and replacing the very snazzy but quirky Network Manager with the quaint but effective wicd, no system tray icon for the unGnome however.

So I have now a working and apparently stable Natty, except that it's taking over 5 minutes to boot.

Sigh.  

To try to figure out what this newest bump on the road was, I install bootchart.  The first boot after that install took thirty seconds, as well as the several afterwards.  

I am at a loss to explain it, but I'm not going to look a gift horse in the mouth.

---

### Post by keepitsimpleengr on 2011-10-29
Upgraded to 11.10 from 11.04 online. 

The upgrade installed Network Manager, which&#8943;although not "running"&#8943;managed to sabotage wicd by deleting the nameserver IP address.

Deleting network manager and manually updating /etc/resolv.conf adding the nameserver's IP address allowed me navigate into the cloud.

---

