---
title: "Server 7.04 with Firebird SQL DB"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by juanbe on 2007-05-28
I'm a hard user of Ubuntu Server, and now I have installed a new 7.04 Version with the Repository package of firebird2-super-server, because in this case I needed this database, intead of Mysql.
The apt-get install worked fine, but there is a missing point in it. The 3050 port that need's to be opened for accesin firebird, its not open, and I'm in trouble trying to open it.
I thought that if I could see trough the nmap command, that the port for MySql was opened, and afterwards take a look at the iptables -L the rule for it, and so understand how to do what I needed to do.
But yes I can see the Mysql port open with the nmap, but it's not present in any rule of iptables.
Can somebody help, telling how can the port 3050 can be opened for the use of firebird ?
Best regards.

---

### Post by mariuz on 2007-06-05
what is the result for netstat -lap  ?
it should contain something like this 

              
tcp        0      0 *:gds_db                *:*                     LISTEN     -

also show me the 

iptables -L -n 

or telnet localhost 3050

---

