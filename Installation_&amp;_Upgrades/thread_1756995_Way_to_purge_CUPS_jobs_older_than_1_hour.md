---
title: "Way to purge CUPS jobs older than 1 hour?"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by jcpeden on 2011-05-12
Hey folks,

I've setup two printers through a system running Ubuntu server that are shared with 30-40 users on our school network.

If the printers run out of ink or paper, they stop printing. The lazier members of staff don't proceed to recharge the ink or paper so when somebody does, hours later, the old jobs start printing again which the teachers no longer need or want.

**I'd like to automatically have my system purge print jobs older than 1 hour. I'm running CUPS and sharing the printers through SAMBA. How do I do this?**


John

---

### Post by jcpeden on 2011-05-19
Surely someone else has had this problem before me?

---

### Post by mulletor on 2013-02-06
I'm probably a little late to this party, but I stumbled upon your post while looking for a solution for my CentOS setup:

find /var/spool/cups/ -iname '[cd]*' -mmin +60 -delete && service cups restart

**edited -mmin to reflect 60 minutes, I had it set for 24 hours

---

