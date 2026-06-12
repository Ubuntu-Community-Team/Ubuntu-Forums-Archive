---
title: "mt-daapd running but iTunes can see it from Windows"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by cmfarley19 on 2008-08-29
I am running Kubuntu Gutsy.
I installed mt-daapd today via adept.  It is running as is avahi-daemon.  I can view the server via the web interface from my windows machine on the same network.  When I run iTunes on the same machine, however, I never see the shared server.  I have "Look for shared music" enabled in iTunes.  

I have been banging my head all day on this.

My Windows machine is on the network wirelessly vi a D-Link 524 router.

Anybody have any thoughts on this?

Chris

---

### Post by Ateo on 2008-08-31
Did you modify /etc/mt-daapd.conf to suite your needs? If not, you'll need to. Then restart the server.

---

### Post by jeskin on 2009-09-29
I'm having the exact same problem.  I can see the shared library from a Mac OS computer on the same network, but not from a Windows computer.  Any ideas on how to setup the .conf properly?

---

