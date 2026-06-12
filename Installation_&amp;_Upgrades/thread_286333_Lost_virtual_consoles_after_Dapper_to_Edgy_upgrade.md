---
title: "Lost virtual consoles after Dapper to Edgy upgrade"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by bhaskar on 2006-10-27
After a Dapper to Edgy Kubuntu upgrade using a series of aptitude dist-upgrade after editing /etc/apt/sources.list to convert dapper to edgy (HP Compaq nw8240 laptop, ATI video, fglrx driver), I no longer have virtual consoles.  Graphical login at console 7 (Ctl-Alt-F7) works fine, but if I use Ctl-Alt-F1 through F6 to try to reach the virtual text consoles, I see a random graphic repeating pattern, but no character mode login prompt.  This functionality worked perfectly on dapper.

Thanx muchly in advance for any assistance.

-- Bhaskar

---

### Post by alb on 2007-01-23
Hi,
I just updated to Edgy, and I've got the same problem.
Have you solved it?

---

### Post by bhaskar on 2007-01-23
Somewhere along the way, the problem resolved itself, but I don't know when.  Just do sudo aptitude update / sudo aptitude upgrade to get current on patches.  Restart X / reboot with your fingers crossed.  Not a very satisfying answer, but it's the best I can give.  Sorry.

-- Bhaskar

---

