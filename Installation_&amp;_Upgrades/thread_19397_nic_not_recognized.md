---
title: "nic not recognized"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by CHEFJENN on 2005-03-11
i just installed ubuntu onto a hyperdata laptop with a MS 10/100 pcmcia NIC.  linux doesn't see it... is there a driver for this or am i out of luck?

---

### Post by alastair on 2005-03-11
[QUOTE=CHEFJENN]i just installed ubuntu onto a hyperdata laptop with a MS 10/100 pcmcia NIC.  linux doesn't see it... is there a driver for this or am i out of luck?[/QUOTE]
 Don't know. What's an "MS 10/100 pcmcia NIC"?

The best idea is to take a look at the system log :

/var/log/syslog

and see if there is anything (messages/errors) related to PCMCIA or network.

---

### Post by lordofkhemenu on 2005-03-11
Being a pcmcia nic and MS...I'm willing to bet it's probably a rebranded card of some kind...get the details on it..it'll be more help.
Solution might be as simple as ndiswrapper, but until there's more specs (chipset, especially) I'm just shooting from the hip...

---

