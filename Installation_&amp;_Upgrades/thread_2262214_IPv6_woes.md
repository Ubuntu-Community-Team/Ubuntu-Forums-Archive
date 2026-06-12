---
title: "IPv6 woes"
date: 2015-01-23
forum: Installation &amp; Upgrades
---

### Post by Karl_Koscher on 2015-01-23
It looks like some of Ubuntu's IPv6 routes are broken, causing all sorts of issues (e.g. apt-get times out):

$ traceroute6 us.archive.ubuntu.com
traceroute to us.archive.ubuntu.com (2001:67c:1562::13) from 2607:f720:1300:1241:e1c3:5cb6:706:5427, 30 hops max, 24 byte packets
 1  2607:f720:1300:1241::1 (2607:f720:1300:1241::1)  0.503 ms  0.339 ms  0.308 ms
 2  2607:f720:13:2::5 (2607:f720:13:2::5)  4.663 ms  14.441 ms  0.842 ms
 3  mx0-ucsd-b-core-vlan2760.ipv6.ucsd.edu (2607:f720:1a:2::2)  0.338 ms  0.31 ms  0.315 ms
 4  hpr-lax-hpr--ucsd-10ge-2.cenic.net (2607:f380::108:9a41:a1d0)  3.358 ms  2.634 ms  2.65 ms
 5  hpr-lax-agg6--lax-hpr.cenic.net (2607:f380::108:9a41:af60)  8.167 ms  8.146 ms  8.094 ms
 6  2610:18:16:5800::15 (2610:18:16:5800::15)  7.766 ms  28.128 ms  7.786 ms
 7  2610:18::5502 (2610:18::5502)  90.462 ms  91.1 ms  91.899 ms
 8  2610:18::5902 (2610:18::5902)  88.752 ms  87.093 ms  87.981 ms
 9  2610:18::5802 (2610:18::5802)  89.357 ms  91.048 ms  88.012 ms
10  mcr2.cambridge-ma.us.xo.net (2610:18::302c)  86.226 ms  86.226 ms  86.19 ms
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *

However, not all routes seem broken:


$ traceroute6 us.archive.ubuntu.com
traceroute to us.archive.ubuntu.com (2001:67c:1562::13), 30 hops max, 80 byte packets
 1  2607:4000:200:15::2 (2607:4000:200:15::2)  0.283 ms  0.273 ms  0.263 ms
 2  * * *
 3  ae1--24.uwbr-atg-1.infra.washington.edu (2607:4000:ff01:9::3)  1.451 ms  1.364 ms  1.359 ms
 4  ae0--4010.icar-sttl1-2.infra.pnw-gigapop.net (2001:1860:4000:3001::134)  0.736 ms  0.738 ms  0.732 ms
 5  xe-0-3-0.11.rtr.seat.net.internet2.edu (2001:468:ffff:16c2::1)  0.782 ms  1.126 ms  0.772 ms
 6  * * *
 7  lo-0.1.rtr.paix.net.internet2.edu (2001:468:ff0b::1)  32.741 ms  32.921 ms  32.915 ms
 8  2001:450:2001:8006::1 (2001:450:2001:8006::1)  36.560 ms  36.531 ms  36.541 ms
 9  te0-7-0-21.ccr21.sjc03.atlas.cogentco.com (2001:550:3::d)  29.153 ms  29.159 ms  29.247 ms
10  be2047.ccr22.sjc01.atlas.cogentco.com (2001:550:0:1000::9a36:571)  29.106 ms  29.310 ms  29.326 ms
11  be2165.ccr22.sfo01.atlas.cogentco.com (2001:550:0:1000::9a36:1c41)  29.268 ms  29.052 ms  28.911 ms
12  be2133.ccr22.mci01.atlas.cogentco.com (2001:550:0:1000::9a36:1e42)  60.342 ms  60.634 ms  60.418 ms
13  be2157.ccr42.ord01.atlas.cogentco.com (2001:550:0:1000::9a36:676)  72.286 ms  72.038 ms  72.441 ms
14  be2138.ccr22.bos01.atlas.cogentco.com (2001:550:0:1000::9a36:2bca)  94.872 ms  94.912 ms  94.780 ms
15  2001:550:2:2c::15:2 (2001:550:2:2c::15:2)  94.212 ms  94.360 ms  94.596 ms
16  ragana.canonical.com (2001:67c:1562::13)  101.286 ms  96.593 ms  97.379 ms




Any idea what's going on? This seems to have been broken for at least a week.

---

### Post by snowkiterdude on 2015-01-23
I'm having the same problem.  Updates and installs are not working very well.  If I disable ipv6 it works just fine.  Sometimes ipv6 times out sometimes it works.


dig us.archive.ubuntu.com
;; ANSWER SECTION:
us.archive.ubuntu.com.    29    IN    A    91.189.91.24
us.archive.ubuntu.com.    29    IN    A    91.189.91.13
us.archive.ubuntu.com.    29    IN    A    91.189.91.14
us.archive.ubuntu.com.    29    IN    A    91.189.91.15
us.archive.ubuntu.com.    29    IN    A    91.189.91.23


they all respond to ipv4 icmp and http






dig AAAA us.archive.ubuntu.com
;; ANSWER SECTION:
us.archive.ubuntu.com.    36    IN    AAAA            2001:67c:1562::16
us.archive.ubuntu.com.    36    IN    AAAA            2001:67c:1562::17
us.archive.ubuntu.com.    36    IN    AAAA            2001:67c:1562::13
us.archive.ubuntu.com.    36    IN    AAAA            2001:67c:1562::14
us.archive.ubuntu.com.    36    IN    AAAA            2001:67c:1562::15


--- 2001:67c:1562::16 ping statistics ---
14 packets transmitted, 0 received, 100% packet loss, time 12999ms
...
traceroute6 2001:67c:1562::16
traceroute to 2001:67c:1562::16 (2001:67c:1562::16) from 2001xxxxxxxxx::1702, 30 hops max, 24 byte packets
 1  2001xxxxxxxxx::1 (2001xxxxxxxxx::1)  0.594 ms  0.627 ms  0.538 ms
 2  xxxxxxxx-1.tunnel.tserv8.dal1.ipv6.he.net (2001xxxxxxxx::1)  22.347 ms  22.58 ms  64.187 ms
 3  ge6-22.core1.dal1.he.net (2001:470:0:78::1)  33.162 ms  16.964 ms  24.224 ms
 4  as1299.gige-g2-17.core1.dal1.he.net (2001:470:0:167::2)  19.472 ms  51.182 ms  45.897 ms
 5  bost-b1-v6.telia.net (2001:2000:3018:84::1)  94.38 ms  65.735 ms  83.765 ms
 6  internap-ic-304640-bost-b1.c.telia.net (2001:2000:3080:93b::2)  65.786 ms  69.94 ms  71.989 ms
 7  * * *  8  * * *  9  * * * 10  * * *...
...
they all time out... via ping6 and traceroute6




So that is not indicating that anything is wrong just that those servers do not respond to icmpv6 echo requests.


However I would think that we should be able to view the archive though a web browser on ipv6:80.  So I tried going to....




us.archive.ubuntu.com  === works via ipv4
91.189.91.24/              === default apach2 page... not what I was hoping for but still connected via ipv4
[2001:67c:1562::16]/  === error 
[2001:67c:1562::17]/  === error 
[2001:67c:1562::13]/  === error 
[2001:67c:1562::14]/  === error
[2001:67c:1562::15]/  === error  


OK So lets make sure we can connect to other ipv6 http server...


dig AAAA ipv6.google.com
;; ANSWER SECTION:
ipv6.google.com.    1781    IN    CNAME    ipv6.l.google.com.
ipv6.l.google.com.    299    IN    AAAA            2607:f8b0:4000:809::1003
[2607:f8b0:4000:809::1003]/  === Works just Fine




So it looks to me like ipv6 updates are not working at all.  Sometime apt-get update will work but only after a long time of waiting(~90-300sec).  Most of the time I get the following error...


    Reading package lists... Done
    W: Failed to fetch us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg  Could not connect to us.archive.ubuntu.com:80 (91.189.91.23). - connect (101: Network is unreachable) [IP: 91.189.91.23 80]
    
    W: Failed to fetch us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.23 80]
    
    W: Failed to fetch us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.23 80]
    
    W: Some index files failed to download. They have been ignored, or old ones used instead.


The weird thing is that when waiting/connecting it shows the ipv6 address. not the ipv4 address in the error.


I'm having this same issue on all my ubuntu 12.04 and 14.04 servers and desktops.


Linux XXXXX 3.13.0-44-generic #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
lsb_release 
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch


eth2      Link encap:Ethernet  HWaddr f4:6dxxx  
          inet addr.x.x.x  Bcast.x.x.x  Mask.x.x.x
          inet6 addr: 2001xxxxxxxxx::1702/64 Scope:Global
          inet6 addr: 2001xxxxxxxxx::1701/64 Scope:Global
          inet6 addr: fe80xxxxxxxxxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1629712 errors:0 dropped:141 overruns:0 frame:0
          TX packets:1331569 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1580099777 (1.5 GB)  TX bytes:456536121 (456.5 MB)

---

### Post by sandyd on 2015-01-23
Ive been experiencing this on and off everywhere. Ive reported it to Canonical a while ago, though there has been no chance since.

For an easy fix....

Remove the pound sign from the following line in /etc/gai.conf
```

precedence ::ffff:0:0/96  100
```

This will instantly prefer IPv4 over IPv6.

You will still be able to use IPv6, it just wont be the first protocol that your networking stack tries.

---

### Post by Karl_Koscher on 2015-01-23
Thanks for the tip! I wish I had known about that when our campus IPv6 routes were messed up.

There is another workaround to force apt to use IPv4 too (the -o Acquire::ForceIPv4=true option), but I'm hoping the underlying issue can be fixed instead of just treating the symptoms. As universities and large ISPs like Comcast roll out IPv6, these issues will affect an increasing number of users, leaving them with a poor user experience.

---

