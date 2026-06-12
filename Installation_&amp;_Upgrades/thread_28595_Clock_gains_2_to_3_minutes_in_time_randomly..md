---
title: "Clock gains 2 to 3 minutes in time randomly."
date: 2005-04-20
forum: Installation &amp; Upgrades
---

### Post by spacemunkey on 2005-04-20
When I first installed ubuntu I had the UTC variable set to yes in /etc/default/rcS. Since then i've changed the UTC to no. Also i've changed the server in /etc/default/ntpdate from ntp.ubuntulinux.org to time-a.nist.gov (more reliable for me). I've started to notice a 2 to 3 minute creep forward im the system clock ever since I installed 5.04. I did not experience this phoenomena with 4.10. Any ideas as to what might be causing this gradual increase in the system clock time and how to best resolve and fix it? 

Hardware: Shuttle SN41G2 (nforce2; athlon; 1 gb ram)

---

### Post by diebels on 2005-04-20
Bad bios battery? Run ntpdate more often? Put it in /etc/cron.hourly

---

### Post by spacemunkey on 2005-04-20
Don't think it's the bios battery because up until the day i switched to 5.04 it was keeping time perfectly.

---

