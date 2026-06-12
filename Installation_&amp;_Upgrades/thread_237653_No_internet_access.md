---
title: "No internet access"
date: 2006-08-16
forum: Installation &amp; Upgrades
---

### Post by simonparnell on 2006-08-16
Fresh install of Ubuntu

Two hard drives. First - windows XP OS - works fine.  Mozilla firefox connects to internet.  

Second - Ubuntu.  No internet access.  Can get a ping from the router no problem.  

Any ideas?

Bearing in mind I was tempted to switch froom Windows to Ubuntu as I was told it would be "easy".  So if I am now going to have to go through endless jargon to fix the problem I will ditch it and go back to what works. Despite the criticisms of windows it did detect settings and have me online once the lenghtly install was complete.

I hate lining Bill Gates' pockets so would appreciate any idiot proof help.

Thanks.

Simon

---

### Post by mgor on 2006-08-16
it's kind of guessing how your network setup are so we can help you. but ok, i'll give it ago.

you have a DSL connection from some ISP, so you have internet -> modem -> router -> home network -> workstation with ubuntu? and you can ping the router using it's IP but you can't access anything on the internet using hostnames?

first off would be trying to ping a remote server using it's ip adress, try 66.249.85.99 which is one of www.google.com's IP addresses. if that works, check the contents of /etc/resolv.conf which contains IP addresses to nameservers to lookup hostnames. it should look something like,
```
search example.com
nameserver 10.0.0.1
nameserver 10.0.0.2
```
does it contain the same nameservers that 'ipconfig /all' reports in windows?

okey, still not working. run 'traceroute` to that same remote IP address to see where it actually fails. 

good luck.

---

