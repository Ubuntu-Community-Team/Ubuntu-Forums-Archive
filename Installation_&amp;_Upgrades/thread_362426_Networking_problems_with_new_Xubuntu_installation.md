---
title: "Networking problems with new Xubuntu installation"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by PBCrunch on 2007-02-15
I just installed Xubuntu on a Compaq Presario 5012US (P3 1GHz, 192MB RAM, i810 integrated grahpics) and the networking is frustrating me.  I can ping google.com inside a terminal window but I can't get anything to load in Firefox.  I can't even get Firefox to load the config page for my router.  Gaim doesn't work and neither does Synaptic.  Basically I can get to the internet on the command line but not in any X applications.

I already checked my firewall rules and found nothing.

Any ideas?

---

### Post by bapoumba on 2007-02-15
Which kind of connection do you have ?
And please post the output to **cat /etc/network/interfaces**.

---

### Post by PBCrunch on 2007-02-15
It is connected by ethernet to a network that has two Windows machines, an Ubuntu machine, two Xboxes, and a PS2.  All of the other devices can access the internet except the Xubuntu box.

I will get the other information after I get off work.

---

### Post by PBCrunch on 2007-02-16
I just installed a different network card and got it working.

---

