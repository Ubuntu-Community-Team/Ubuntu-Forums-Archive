---
title: "DNS resolution slow in 9.10?"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2010-01-12
Are DNS name lookups slow for you in 9.10?  Seems slow to me, but I've not paid that much attension to it.  But after reading the launchpad reports for this bug that hit me today:

[https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/431217](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/431217)

Seems something may be amiss with name resolution.  


My Windows box uses the same DHCP server as my 9.10 box does (thus get the same DNS settings) and it has fast name lookup, Firefox on 9.10 seems way faster than Firefox on Windows once the URL address is resolved, but the DNS lookups seem painfully slow. I'm using different versions of Firefox, so its an apples to oranges comparrison but something just doesn't feel right here.

--wally.


Edit: for example, it took over 20 seconds for the "looking up ubuntuforums.org" message to leave the Firefox status line when I posted this, then loading this thread was effectively instataneous.

---

### Post by Dennis N on 2010-01-12
The slow DNS lookup should be helped by disabling ipv6 in Firefox. Here's how:
Type in Firefox's address bar:
```
about:config
```
Click "I'll be careful" then look for the line starting with:
```
network.dns.disableIPv6
```
Double click on the line and the value should change from "false" to "true" at the end. Done.

---

### Post by dddanmar on 2010-01-12
I generally have the same problem with ipv6 and Ubuntu, nearly every install now.

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by wkulecz on 2010-01-13
It seems one of the 37 updates that got installed yesterday seems to have improved, if not fixed the issue. 

Without some serious work its tough to evaluate these issues with DNS caching etc. usually making a first access to a site noticably slower if no other user on your network has been there recently.

Its was very slow repeated access to the same sites that caused be to think something was amiss, especially since my Windows and Ubuntu 8.04 system were not seeing any problems.

As to IP4 vs. IP6 may I be so bold as to have the developers let the networking layer try IP6 and if it doesn't work disable it automatically until the next reboot.

I understand wanting to move to IP6 but it is disservice to interfere with IP4 networks in the push to get IP6 more widely used.  

I understand the even bigger need to leverage the existing network infrastructure ivestment in today's economy, so something more than "new and improved" is needed to justify the expense.  Being a bad IP4 citizen will get Ubuntu banned before it gets the powers than be around here to spend money upgrading to IP6.

--wally.

---

