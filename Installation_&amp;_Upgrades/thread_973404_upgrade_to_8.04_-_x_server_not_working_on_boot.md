---
title: "upgrade to 8.04 - x server not working on boot"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by dianep on 2008-11-06
Hi there,

Sorry to start a new thread but I couldn't find a similar problem
in the other posts.

Up until Tuesday I was running 7.04.  I upgraded to 7.10 using the
update manager and that worked fine.  I immediately upgraded to
8.04 LTS using the update manager.  I thought this would be easier
than a clean install I don't have anywhere to backup 50 Gs of data
(at least no where handy at the mo). 

Anyways, on restart, the system hangs right before the login window
should come up. I can kill the xserver and just use command line
to logon, but there is no way to pull the xserver back up, so that
I can use the Desktop. The little wheel just keeps spinning.
Any suggestions?  Anyone know what broke?

Thanks in advance,
diane

---

### Post by m2.g5ru6y7s on 2008-11-06
What happens when you try the following commands in the shell:

sudo /etc/init.d/gdm restart

???

---

