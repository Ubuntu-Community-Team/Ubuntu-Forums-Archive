---
title: "Time-out errors after Gutsy upgrade"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by christophermoore on 2007-10-20
I just upgraded from Feisty to Gutsy and I'm having some connection time-out issues.

What works:
firefox
pinging any IP address
utorrent
gmail notifier

What doesn't work:
pidgin
apt-get

Pidgin has time-out errors for both Google Talk and MSN accounts. Apt-get has time-out errors for the repositories but I can ping them without a problem.

I'm at a loss... If anyone has any suggestions, or if you want me to test something to see whether it works or not, please tell me!

---

### Post by watchitman on 2007-10-20
This worked for me (from [http://ubuntuforums.org/showthread.php?t=581181](http://ubuntuforums.org/showthread.php?t=581181) ):

1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
4. Reboot Ubuntu.

I've had more problems with networking in this release than any Linux distro I've used since the bad-old-days of winmodems. Atm, I can't access the repositories, I just get errors. Good luck.

---

### Post by Arenlor on 2007-10-20
Try updating again, seems to have fixed itself just a bit ago, but Pidgin is not all that reliable, I've been using it since before Gutsy, and yeah MSN and Google both time out, a lot.

---

### Post by christophermoore on 2007-10-20
Unfortunately the IPv6 change didn't resolve anything.

Regarding the apt-get problem, something really weird is happening. It's trying to connect to servers with the IP 1.0.0.0. Why??!? The first time I pinged the domain au.archive.ubuntu, it resolved as 1.0.0.0, but moments later it resolevd as mirror.optus.net (211.29.132.173). Does this suggest a DNS issue? According to the "Network Settings" dialog, my current DNS servers are 10.1.1.1 (router) and 203.0.178.191 (my ISP's DNS).

As an aside, I tried changing from "server in Australia" to "main server" in the "Software Sources" dialog, but it had the same time-out error.

> chris@chris-desktop:~$ sudo apt-get update
0% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]
chris@chris-desktop:~$ ping au.archive.ubuntu.com
PING au.archive.ubuntu.com (1.0.0.0) 56(84) bytes of data.

--- au.archive.ubuntu.com ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7010ms

chris@chris-desktop:~$ ping au.archive.ubuntu.com
PING mirror.optus.net (211.29.132.173) 56(84) bytes of data.
64 bytes from au.archive.ubuntu.com (211.29.132.173): icmp_seq=1 ttl=58 time=174 ms
64 bytes from au.archive.ubuntu.com (211.29.132.173): icmp_seq=2 ttl=58 time=167 ms
64 bytes from au.archive.ubuntu.com (211.29.132.173): icmp_seq=3 ttl=58 time=70.4 ms
64 bytes from au.archive.ubuntu.com (211.29.132.173): icmp_seq=4 ttl=58 time=35.8 ms
64 bytes from au.archive.ubuntu.com (211.29.132.173): icmp_seq=5 ttl=58 time=101 ms

--- mirror.optus.net ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3999ms
rtt min/avg/max/mdev = 35.819/110.053/174.526/54.095 ms
chris@chris-desktop:~$ sudo apt-get update
0% [Waiting for headers] [Connecting to security.ubuntu.com (1.0.0.0)]                                 
chris@chris-desktop:~$ ping security.ubuntu.com
PING security.ubuntu.com (1.0.0.0) 56(84) bytes of data.

--- security.ubuntu.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2008ms

chris@chris-desktop:~$ ping security.ubuntu.com
PING security.ubuntu.com (1.0.0.0) 56(84) bytes of data.

--- security.ubuntu.com ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1009ms

chris@chris-desktop:~$ ping security.ubuntu.com
PING security.ubuntu.com (1.0.0.0) 56(84) bytes of data.

--- security.ubuntu.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms


---

### Post by Arenlor on 2007-10-20
Please share the contents of your /etc/hosts file.

---

### Post by christophermoore on 2007-10-20
Ah, here it is. I'm guessing that I should comment out the last six lines?

> 127.0.0.1	localhost
127.0.1.1	chris-desktop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by christophermoore on 2007-10-20
Hmm that didn't work - apt-get and pidgin are still broken.

---

### Post by Arenlor on 2007-10-20
No, I was actually just looking for something like 1.0.0.0 *.ubuntu.com in there. So it's not your hosts files, which is good. It seems to be with your DNS then

---

### Post by steviemc on 2007-10-20
Hi,

I just found these links which seem to have resolved apt-get and pidgin issues...do you have a DLink router?

[http://faler.wordpress.com/2007/10/14/ubuntu-linux-710-gutsy-gibbon-on-a-sony-vaio-sz4-xwn/]("http://faler.wordpress.com/2007/10/14/ubuntu-linux-710-gutsy-gibbon-on-a-sony-vaio-sz4-xwn/")

[https://www.opendns.com/start?device=ubuntu]("https://www.opendns.com/start?device=ubuntu")

Cheers

---

### Post by christophermoore on 2007-10-20
Yes, I do have a Dlink router. That fix - removing the router from the DNS list and replacing it with openDNS servers -  worked for me. Thanks!

---

