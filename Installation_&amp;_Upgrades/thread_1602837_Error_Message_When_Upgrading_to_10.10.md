---
title: "Error Message When Upgrading to 10.10"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by Skyline969 on 2010-10-21
I recent installed Ubuntu 10.04 in a dual-boot with Windows 7, and I wanted to upgrade to 10.10. However, every time I try to update, I get this error message:

> W:Failed to fetch [http://archive.canonical.com/dists/maverick/Release.gpg](http://archive.canonical.com/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

It happens when it's setting new repositories. The version of Ubuntu is amd64, FYI. What can I do to fix this, or should I just burn a copy of the alternate install CD for 10.10 and install it that way (my last resort, as I only have one blank CD left and can't afford more)?

Thanks in advance.

---

### Post by efflandt on 2010-10-22
What do you get when in a terminal you do: [B]host archive.canonical.com
[/B]
It sounds you have a DNS or proxy issue.  If you are required to use a proxy for web access you might set that in System > Preferences > Network Proxy so it works for everything including upgrades and updates.

---

### Post by Skyline969 on 2010-10-22
> **efflandt said:**
> What do you get when in a terminal you do: [B]host archive.canonical.com
[/B]
It sounds you have a DNS or proxy issue.  If you are required to use a proxy for web access you might set that in System > Preferences > Network Proxy so it works for everything including upgrades and updates.

Oddly enough, I do not have any proxies set up at all. I am my home network's administrator, and I've double and triple-checked my setup... nothing that I can think of or notice could be causing the problem.

Also, that command gives me the following output:
> archive.canonical.com has address 91.189.88.33

Also, I decided to ping that IP to make sure I can talk to it, and I can:
> PING 91.189.88.33 (91.189.88.33) 56(84) bytes of data.
64 bytes from 91.189.88.33: icmp_seq=1 ttl=56 time=189 ms
64 bytes from 91.189.88.33: icmp_seq=2 ttl=56 time=186 ms
64 bytes from 91.189.88.33: icmp_seq=3 ttl=56 time=188 ms
64 bytes from 91.189.88.33: icmp_seq=4 ttl=56 time=187 ms
64 bytes from 91.189.88.33: icmp_seq=5 ttl=56 time=189 ms
64 bytes from 91.189.88.33: icmp_seq=6 ttl=56 time=197 ms
64 bytes from 91.189.88.33: icmp_seq=7 ttl=56 time=189 ms
64 bytes from 91.189.88.33: icmp_seq=8 ttl=56 time=186 ms
64 bytes from 91.189.88.33: icmp_seq=9 ttl=56 time=187 ms
64 bytes from 91.189.88.33: icmp_seq=10 ttl=56 time=188 ms
^C
--- 91.189.88.33 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9005ms
rtt min/avg/max/mdev = 186.253/189.028/197.244/2.957 ms

---

### Post by sikander3786 on 2010-10-22
Did you simply try changing the update server from System > Administration > Software Sources to something else than the current one, Main server preferably.

---

### Post by Skyline969 on 2010-11-04
Just a quick post in here to change my status on this issue. I managed to solve the problem, below is the contents of my personal documentation regarding the issue:

> So, when I got the error

W:Failed to fetch [http://archive.canonical.com/dists/maverick/Release.gpg](http://archive.canonical.com/dists/maverick/Release.gpg) Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead. 

when running apt-get update, I found that it was a DNS resolution issue. To fix this, I opened Network Connections and edited my auto eth0. I went to the IPv4 Settings and changed it to Automatic (DHCP) addresses only. I then changed my DNS Servers to 8.8.8.8 - Google's DNS - and clicked Apply. I then disconnected and reconnected auto eth0 and all was working fine.

---

