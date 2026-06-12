---
title: "Problems with DNS when using an ActionTec DSL router"
date: 2005-05-09
forum: Installation &amp; Upgrades
---

### Post by cbunn on 2005-05-09
I have noticed that my /etc/resolv.conf file is incorrectly updated when I reboot the system on a network with the  DHCP service is provided by an ActionTec DSL router (from QWEST). This problem does not occur when the workstation is on another network that uses a Trendware router and Broadext (something) DSL modem. 

The system startup inserts an address of 192.168.0.1 as the first line in the /etc/resolv.conf file. The second line is a valid DNS server. If I swap the order of the two lines the DNS seems to work. When I am using Firefox it seems to take a longer than usual time to resolve the site name and for the initial transfer of the web page to proceed. 

Has anyone had a similar experience and found a solution.

---

### Post by GreatSunJester on 2005-05-09
Might be an issue unique to the actiontec.. I am having the same problem.

I thought this post [http://www.ubuntuforums.org/showthread.php?t=32707](http://www.ubuntuforums.org/showthread.php?t=32707) was going to lead me to the solution.  It did not.
I used sudo kcontrol (note: I am using kubuntu, and kcontrol) and tried to specify my network settings --- network stopped responding totally untill I returned to DHCP.

As an aside, pinging a server at my ISP with the ubuntu default settings returned an average of 145ms.  When I go in and edit the DNS it drops to 50ms.
Annoying but survivable.

---

### Post by cbunn on 2005-05-10
I have found reference to this problem in the bug reporting area: Bugzilla Bug 5868, unfortunately it does not see m like anyone is moving forward on it. I think I'll look for a firmware upgrade to the ActionTec or perhaps setup a cheap router between my workstation and the ActionTec and see if it behaves any differently.

---

### Post by GreatSunJester on 2005-05-10
[http://www.spazmatic.net/broadband/actiontec/](http://www.spazmatic.net/broadband/actiontec/)

Pick your router and you can find the newest firmware.

Oh -- I have a GT701 and installed the 3.60.1.0.5.5 firmware a while back.  I have this DNS problem so I doubt a firmware upgrade will fix it.
I think the actiontec is trying to be a DNS server, but is not REALLY a DNS server.

---

### Post by GreatSunJester on 2005-05-10
Had a thought (RARE!).  Logged into my XP machine at home and checked my LAN settings... it is set for DHCP.  Looked further and the first DNS server showing is 192.168.0.1 -- so we now know this is not a ubuntu problem, but IS an actiontec thing.

---

### Post by diamond on 2005-11-26
Glad I'm not the only one with this problem. I discovered it about 6 months ago and called everyone I could think of (Qwest, my ISP, Actiontec) for a solution. Nobody had one.

This appears to be an inherent bug in the Actiontec router. I'm shopping around now to find another brand that is compatible with my DSL service.

---

### Post by sadsac on 2005-12-15
Hey! I just found this thread because, of course, I'm having the same problem using the crappy Actiontec/Qwest GT-701WG.

DNS lookup was running slow as sludge... looking up google.com took like 20-30 seconds, and then it had to do it all over again after the page loaded and I clicked another link (on the same google domain). Yikes!

Why it works fine under XP, I have no idea...

I think the Actiontec is fubaring the LAN IP address (192.168.0.1) with the DNS.

Anyway, after reading the thread mentioned earlier in this thread, I manually edited /etc/resolv.conf with the two correct DNS server addresses, as shown in the Actiontec configuration utility, under "Status". Then I set the permissions on /etc/resolv.conf to read only.

Now, DNS works normally. Even though the Actiontec configuration is set to dynamically assign DNS, I notice the addresses stay constant. If you change between other wireless access points, you'll probably need to enable write permissions on /etc/resolv.conf before doing so.

---

### Post by dbreese on 2005-12-23
[http://ubuntuforums.org/showthread.php?p=598352](http://ubuntuforums.org/showthread.php?p=598352)

Just ran across this thread.  Posted my solution above.  Should clear up the issue.  You'll need to modify the BAD_IP to be 192.168.0.1, or whatever you want.

Hope this helps,
Dustin

---

