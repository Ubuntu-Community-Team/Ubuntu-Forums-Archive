---
title: "Updates Not Working"
date: 2016-12-10
forum: Installation &amp; Upgrades
---

### Post by anon24 on 2016-12-10
I tried both: sudo apt-get update and also using the software updater. Neither works.

sudo apt-get update gets stuck here: 

```
0% [Connecting to us.archive.ubuntu.com (2001:67c:1562::16)] [Connecting to sec
```

Any idea what's going on? I have never had an issue like this. Today is the first day that it's happened.

---

### Post by Bashing-om on 2016-12-10
anon24; Hummmm ..........

Lost your internet connection ?

what results with terminal commands:
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com

```

[INDENT][INDENT]ya gotta have
[INDENT][INDENT][INDENT]that line of communications
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by anon24 on 2016-12-10
```
~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=46 time=32.9 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=46 time=34.2 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=46 time=39.2 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 32.993/35.488/39.201/2.681 ms
```
```
~$ ping -c3 ubuntu.com
PING ubuntu.com (xx.xxx.xx.xx) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (xx.xxx.xx.xx): icmp_seq=1 ttl=46 time=236 ms
64 bytes from ovinnik.canonical.com (xx.xxx.xx.xx): icmp_seq=2 ttl=46 time=151 ms
64 bytes from ovinnik.canonical.com (xx.xxx.xx.xx): icmp_seq=3 ttl=46 time=174 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 151.352/187.356/236.640/36.062 ms
```

---

### Post by deadflowr on 2016-12-10
See if running a force ipv4 works, since I see it's trying to connect to the server ala ipv6.
Try:
```
sudo apt-get -o Acquire::ForceIPv4=true update
sudo apt-get -o Acquire::ForceIPv4=true upgrade
```

from here:[http://askubuntu.com/questions/759524/problem-with-ipv6-sudo-apt-get-update-upgrade]("http://askubuntu.com/questions/759524/problem-with-ipv6-sudo-apt-get-update-upgrade")

If it works I would recommend running this on and off with the normal defaults in place (or as it is currently) before attempting to add the options to the /etc/apt/apt.conf.d/99force-ipv4 file.
So you can determine if this is a long standing issue or was simply a temporary glitch.
If that makes sense.

---

### Post by anon24 on 2016-12-17
So, I tried sudo apt-get update again... Here is what I got:

```
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

EDIT: Weirdly enough, I tried it again and it worked.

---

### Post by Mark Phelps on 2016-12-17
I've run into this very same problem and fixing it required two changes:
1) Disabling IPV6
2) Manually editing the repository config file

Regarding the first:
> Fix by manual editing:

Open terminal

Edit /etc/sysctl.conf to add these lines
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

run $ cat /proc/sys/net/ipv6/conf/all/disable_ipv6

If you get &#8220;1&#8221; it worked, otherwise enter &#8220;sudo sysctl -p&#8221; in terminal

You will then see the three net.ipv6 lines you added above

redo the cat command and you should get &#8220;1&#8221;

Regarding the second:

I had to edit the file /etc/apt/sources.list to edit out these lines:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security main restricted

BOTH of those lines were failing on the downloads.

So, I manually changed the URL after http:// to match the URLs of the other entries (in my case, cosmos.cites.illinois.edu/pub/ubuntu) and saved the file.

Then, when I reran the updates, they worked -- and have ever since.

---

### Post by anon24 on 2016-12-22
My question is: what caused this to be an issue all of the sudden? I've been using Ubuntu for a while now and never encountered this until I made this post.

---

### Post by ian-weisser on 2016-12-22
Could be many possible causes, most of which are network-related (congestion, change in topology) or server-related (congested, updating, under attack, down for maintenance).

---

