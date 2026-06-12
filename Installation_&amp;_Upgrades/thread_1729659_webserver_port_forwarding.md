---
title: "webserver port forwarding"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by tkviking on 2011-04-15
Hi readers,

I have some trouble to get port forwarding to work for webserver.  I have small success in getting port forwarding to work for port 22 though.  So I think my trouble is probably in the way I define apache and shorewall which is freeware for firewall.

I make changes to the following files :-

/etc/apache2/ports.conf
The lines with are changed as follows :-
   NameVirtualHost *:XXXX
   Listen 192.168.1.YYY:XXXX

    where XXXX is the port number I used to replace 80.

/etc/shorewall/interfaces with lines changed as follows :-

loc eth0   detect dhcp,tcpflags,logmartians, mosmurfs

eth0 is connected to my Ubuntu server.

/etc/shorewall/zones remains in default setting

fw firewall
net ipv4

/etc/shorewall/policy  with changes as follows :

net   $FW   ACCEPT   info
$FW   net   ACCEPT   
net   all   DROP     info

/etc/shorewall/rules  with changes as follows :

ACCEPT   net    loc:192.168.1.YYY:XXXX   tcp   
ACCEPT   $FW    net            icmp    

Any suggestions or help are very much appreciated.  This is one big headache I really hope I can solve with your help.

Thanks for reading my post.

TK

---

