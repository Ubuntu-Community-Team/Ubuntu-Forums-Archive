---
title: "Monitor Sync Rate"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by michellembrodeur on 2007-05-06
Does anyone know of software in either Linux or Windows that can read the monitor specs.
IE: Sync Rate   Horizontal and Vertical

To properly configure the monitor for Linux.

Friend has a Xplio or something like and I cannot even find out who manufacturer is. Lots of places sell them but nobody actually makes them.

Thanks for all the help.

---

### Post by benn333 on 2007-05-06
I'm currently trying to troubleshoot my own monitor res problem, and came across this. (Doesn't solve my own issue, but maybe it'll help you.)

sudo apt-get install xresprobe
sudo ddcprobe | grep monitorrange

---

### Post by michellembrodeur on 2007-05-06
> **benn333 said:**
> I'm currently trying to troubleshoot my own monitor res problem, and came across this. (Doesn't solve my own issue, but maybe it'll help you.)

sudo apt-get install xresprobe
sudo ddcprobe | grep monitorrange

I will try that today, thanks

---

