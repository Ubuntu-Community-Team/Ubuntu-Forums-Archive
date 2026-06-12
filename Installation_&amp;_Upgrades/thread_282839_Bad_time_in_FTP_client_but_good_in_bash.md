---
title: "Bad time in FTP client but good in bash"
date: 2006-10-23
forum: Installation &amp; Upgrades
---

### Post by bld on 2006-10-23
Hi,
I have Ubuntu 6.06 installed on server and it's something wrong with the time settings.
I'm in the DST +0200 UTC time zone and when I connect with SSH the bash command 'date' shows good time. When I connect with FTP client I see that all files dates are in UTC time (tested with the same results on different FTP clients)

/etc/default/rcS has UTC=no entry.
Ubuntu is the only system on the server.
FTP runs with proftpd.

How to make the dates in FTP connections correct ?

Best,
Przemek

---

