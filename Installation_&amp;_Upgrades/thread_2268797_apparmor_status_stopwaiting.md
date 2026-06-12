---
title: "apparmor status stop/waiting"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by jamespamullan on 2015-03-11
I upgraded to 14.10 server from 14.04. When I enter** /etc/init.d/apparmor status**
the only output is** apparmor stop/waiting**

If I enter
**/etc/init.d/apparmor start**
the output is apparmor stop/waiting

and if I enter 
**/etc/init.d/apparmor stop**
stop: Unknown instance:

**aa-status**  gives the following output
apparmor module is loaded.
5 profiles are loaded.
5 profiles are in enforce mode.
   /sbin/dhclient
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/sbin/mysqld
   /usr/sbin/tcpdump
0 profiles are in complain mode.
2 processes have profiles defined.
2 processes are in enforce mode.
   /sbin/dhclient (1321) 
   /usr/sbin/mysqld (1661) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

How can I tell if apparmor is correctly started in ubuntu 14.10 ?

In 14.04 **/etc/init.d/apparmor status**  produced this output
apparmor module is loaded.
5 profiles are loaded.
5 profiles are in enforce mode.
   /sbin/dhclient
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/sbin/mysqld
   /usr/sbin/tcpdump
0 profiles are in complain mode.
1 processes have profiles defined.
1 processes are in enforce mode.
   /usr/sbin/mysqld (1186) 
0 processes are in complain mode.
0 processes are unconfined but have a profile defined

I would be grateful for some explanation.
jamesp

---

