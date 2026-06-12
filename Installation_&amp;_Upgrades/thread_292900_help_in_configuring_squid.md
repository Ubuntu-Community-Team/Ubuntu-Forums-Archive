---
title: "help in configuring squid"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by fkeith on 2006-11-04
To all the Ubuntu linux gurus out there
need help in configuring squid.I recently just got a copy of ubuntu and hve installed it.I hve a windows 98 network with all other machines browsing through a router connected to a switch.I am trying to get the other machines to browse from the proxy machine and prevent access to certain sites using ACL's.The thing is i am not able to configure the squid.conf correctly.As the windows machines are not able to browse the net.I get the message of the squid proxy version running.My network is 192.168.1.1-192.168.1.49 with 192.168.1.49 as my proxy server.Also i also need the windows 98 machines to download their mails using pop3 port 110 and send mails using port no 25 through the linux proxy server and connect to mailserver on an external ip 210.211.X.X and then access their mails.can some one help me with a sample configuration file.

regards

](*,) fkeith

---

### Post by Abhi Kalyan on 2007-01-28
alright bro here goes:
1. you will need nat for internet sharing
2. squid for proxing
3. dansguardian for content filtering
---------------------------------------------------
$ sudo bash
----------------------------------------------------
"set your server's ip to static"
#ifconfig ethX ip
where 
"ethX" is the name of the ethernet card connecting the lan to your server
"ip" is the ip address that you want assigned to it.
-----------------------------------------
configure the NAT as follows
#iptables -t nat -A POSTROUTING -o ethY -j MASQUERADE
"ethY" is the name of the ethernet card connecting the server to the internet
---------------------------------------
type the following in yout terminal
#echo 1 > /proc/sys/net/ipv4/ip_forward
-----------------------------------------
#apt-get install dnsmasq ipmasq
#/etc/init.d/dnsmasq restart
#dpkg-reconfigure ipmasq
{keep sayig okay till you come to a screen whihc asks you when the service has to be started, Choose "After network interfaces"}
--------------------------------------------------------------------
#iptables -t nat -A POSTROUTING -o ethY -j MASQUERADE
#echo 1 > /proc/sys/net/ipv4/ip_forward
-----------------------------------------------
edit [ /etc/sysctl.conf ]
uncomment the line containing -
net/ipv4/ip_forward=1
"Note: if this line not present please type it in."
-----------------------------------------------
reboot for nat activation.
Keep pinging to the ip connected to the LAN while the booting process is under way.
you will see what happenes.
-----------------------------------------------------------------------------
install squid
install dansguardian
--------------------------------------------------
reconfigure dans afetr installation
make sure that the port it listens to is 8080 while the squid runs on 3128.
Please serach for these two naes there are beautifull howtos available.
Thsi whole of the above was by some one, I hav no idea about it, but it worked for me hope it works for you.
Do post in the results.

---

