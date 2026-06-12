---
title: "Cannot find localhost"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by ben22 on 2008-03-05
Hello,

I installed Apache2, but when entering "localhost" or 127.0.1.1 it cannot find a page while loading for ages.

I also added "ServerName localhost" to both the apache2.conf and httpd.conf, restarted apache, but still not working.

In the /etc/apache2/sites-avaiilable directory "default" file around line 18 or 19 I removed the # at the beginning of the line and and restarted apache, localhost is still not accessible.

[LIST=1]
[*]how can I determine and solve the problem? Please note I am a newbie, so precise command line instructions would be nice.
[/LIST]

THANK YOU
Ben

---

### Post by Pumalite on 2008-03-05
Post:
ip addr

---

### Post by ben22 on 2008-03-05
> **Pumalite said:**
> Post:
ip addr


ben@ben-desktop:~$ ip addr
1: lo: <LOOPBACK> mtu 16436 qdisc noop 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:13:8f:29:c7:a8 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.102/24 brd 192.168.0.255 scope global eth0
    inet6 fe80::213:8fff:fe29:c7a8/64 scope link 
       valid_lft forever preferred_lft forever

---

### Post by Pumalite on 2008-03-05
You have an ip, but if you have a router, it doesn't show up

---

### Post by ben22 on 2008-03-05
This is the error log:

[Thu Feb 21 08:22:22 2008] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations
[Thu Feb 21 08:22:55 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Thu Feb 21 08:22:55 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Feb 21 08:23:05 2008] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations
[Thu Feb 21 08:24:37 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Thu Feb 21 08:24:37 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Feb 21 08:25:41 2008] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations
[Thu Feb 21 08:45:00 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Thu Feb 21 08:45:00 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Feb 21 08:45:10 2008] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations
[Thu Feb 21 09:28:27 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Thu Feb 21 09:28:27 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Feb 21 09:28:37 2008] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations
[Thu Feb 21 09:35:51 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Thu Feb 21 09:35:51 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Feb 21 09:36:01 2008] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations
[Thu Feb 21 09:41:19 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Thu Feb 21 09:41:19 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Feb 21 09:41:29 2008] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations
[Thu Feb 21 09:46:54 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Thu Feb 21 09:46:54 2008] [notice] caught SIGWINCH, shutting down gracefully
[Thu Feb 21 09:47:05 2008] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations
[Thu Feb 21 11:44:30 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80
[Thu Feb 21 11:44:30 2008] [notice] caught SIGWINCH, shutting down gracefully
[Wed Mar 05 10:38:35 2008] [notice] Apache/2.2.4 (Ubuntu) configured -- resuming normal operations
[Wed Mar 05 10:43:45 2008] [notice] Graceful restart requested, doing restart
[Wed Mar 05 10:43:45 2008] [warn] (22)Invalid argument: connect to listener on 0.0.0.0:80

---

### Post by ben22 on 2008-03-05
> **Pumalite said:**
> You have an ip, but if you have a router, it doesn't show up

yes, the pc is connected to a router. but what does that have to do with not being able to access apache via "localhost"?

---

### Post by aJayRoo on 2008-03-05
Isn't the loopback IP address usually 127.0.0.1 rather than 127.0.1.1? Just wondering...

---

### Post by ben22 on 2008-03-05
> **aJayRoo said:**
> Isn't the loopback IP address usually 127.0.0.1 rather than 127.0.1.1? Just wondering...

tried that ip as well

---

