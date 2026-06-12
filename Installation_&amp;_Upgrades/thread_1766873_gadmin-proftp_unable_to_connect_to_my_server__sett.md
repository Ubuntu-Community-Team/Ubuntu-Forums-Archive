---
title: "gadmin-proftp unable to connect to my server / settings"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by geidorei on 2011-05-24
Hi - ok im being thick here! Ahhhhh!

Right then - have setup proftpd via gadmin, all is well and is activated.

This is where im being stupid - what setting do i use in my ftp prog (filezilla)??

host: ive put my ip address (77.xx.xxx.xx)
user name and password

However, i have a number of computers on my network, obviously when i try to ftp into my server how does it know which one to connect to? or is this not required.

any help greatly appreciated - i need to get this working within the next few hours, or ill be in do-dos.

Karl

---

### Post by geidorei on 2011-05-25
just to let you know i found out what the issue was - port 21 wasnt open for some reason, opened on router but not on pc.

followed following info to sort, as i couldnt find anything on here for some reason...

[http://www.cyberciti.biz/faq/iptables-open-ftp-port-21/](http://www.cyberciti.biz/faq/iptables-open-ftp-port-21/)

---

