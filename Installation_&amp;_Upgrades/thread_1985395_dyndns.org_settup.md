---
title: "dyndns.org settup"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2012-05-23
Since I need to setup dynamic dns only every couple of years, I forgot something, ...


I registered a free dynamic DNS service, which resolved the name to my current IP address:

mysite.gotdns.org 	Host 	114.xxx.xxx.249 

I can ping it, ... so it seems it works!

With the change of the hard disk I installed 12.02.

I can reach with [http://localhost/my-stuff](http://localhost/my-stuff) and [https://localhost/my-secure-stuff](https://localhost/my-secure-stuff) all my web sites again.


However I get:

Unable to connect
  Firefox can't establish a connection to the server at mysite.gotdns.org.

if I use [http://mysite.gotdns.org](http://mysite.gotdns.org)   and  [https://mysite.gotdns.org](https://mysite.gotdns.org)


What do I miss?

---

### Post by haqking on 2012-05-23
> **ELMIT said:**
> Since I need to setup dynamic dns only every couple of years, I forgot something, ...


I registered a free dynamic DNS service, which resolved the name to my current IP address:

mysite.gotdns.org     Host     114.xxx.xxx.249 

I can ping it, ... so it seems it works!

With the change of the hard disk I installed 12.02.

I can reach with [http://localhost/my-stuff](http://localhost/my-stuff) and [https://localhost/my-secure-stuff](https://localhost/my-secure-stuff) all my web sites again.


However I get:

Unable to connect
  Firefox can't establish a connection to the server at mysite.gotdns.org.

if I use [http://mysite.gotdns.org](http://mysite.gotdns.org)   and  [https://mysite.gotdns.org](https://mysite.gotdns.org)


What do I miss?


You cant usually from your LAN go out and come back in again if you know what i mean.

Could you ever view your website from internally ?

use localhost or IP internally and make sure from another location or from phone maybe that you can see the site and it that means it is working.

---

### Post by ELMIT on 2012-05-23
I am sure I could use interchangeable mysite.gotdns.org and localhost.


I tried now to use my mobile phone to connect without LAN, and I also get Website not available, ...


How about firewall?

---

### Post by haqking on 2012-05-23
> **ELMIT said:**
> I am sure I could use interchangeable mysite.gotdns.org and localhost.


I tried now to use my mobile phone to connect without LAN, and I also get Website not available, ...


How about firewall?

well it could be but i presumed you already had this working to allow port 80 traffic in.

Unless you changed the internal IP and port forwarding.

---

### Post by ELMIT on 2012-05-23
I installed a new 12.04 system. I cannot remember where to open the ports. Give me a hint, please ;-)

---

### Post by jadtech on 2012-05-23
I thing the Ip address of you router in  browser should  work  so you can open ports ..

its been a while sinceI have set up a server  how ever i believe you have to make sure  it to is using port 80 sometimes they are not like I said been a long time ..

---

### Post by ELMIT on 2012-05-25
The router has not changed, ...
It must be a setting in Ubuntu 12.04

I tried to telnet to the hosts with the ports 80 443 and get "No route to host" while when I take a wrong port like 79 444 then I get "Connection refused"

This suggests me that the port / firewall settings seems ok and apache has to be tweaked somewhere to accept connection via "localhost" and from an interface.

---

### Post by ELMIT on 2012-05-25
Router was setup to forward all incoming service requests to 192.168.0.99 while DHCP was setup from *.100 ~ *.199

By setting up the new desktop I forgot to give the desktop a fix IP address and it got the IP *.102 from DHCPd

=> No service from outside could reach *.102, since it was directed to *.99

Thanks for your hints!

---

### Post by haqking on 2012-05-26
> **ELMIT said:**
> Router was setup to forward all incoming service requests to 192.168.0.99 while DHCP was setup from *.100 ~ *.199

By setting up the new desktop I forgot to give the desktop a fix IP address and it got the IP *.102 from DHCPd

=> No service from outside could reach *.102, since it was directed to *.99

Thanks for your hints!

Sorry didnt get back to you, yeah thought it might be port forwarding/IP issue.

Glad you got it sorted.

peace

---

