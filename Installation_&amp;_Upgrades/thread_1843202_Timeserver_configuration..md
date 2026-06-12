---
title: "Timeserver configuration."
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by jillandjackk on 2011-09-13
Hi guru's

How could the timeserver configured so, that port 525/udp could be open and what could be the package for the installation of the timeserver of the port 525 to get be opened.

Regards,
jack and jill.

---

### Post by 2F4U on 2011-09-13
Not sure what you mean. Ports are usually opened or closed through a firewall on the machine.

---

### Post by jillandjackk on 2011-09-13
Hi,

Actually,we have requirement to configure timeserver so, Which package should be installed.If you see in the /etc/services file you will find the service like TIMED service which is a xinetd service and firewall is not activated.

Thanks for the reply.
jack.):P

---

### Post by dino99 on 2011-09-13
firewall: ufw
server time : ntp, ntpdate

---

