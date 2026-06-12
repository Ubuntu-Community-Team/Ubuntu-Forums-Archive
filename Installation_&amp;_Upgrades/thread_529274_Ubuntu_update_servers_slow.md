---
title: "Ubuntu update servers slow?"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by hexstar on 2007-08-19
Anyone else noticing very slow speeds on the Ubuntu update servers (ca.archive.ubuntu.com and security.ubuntu.com)? Is this due to some of the servers being hacked into and as a result being put offline (thus putting a lot of extra stress on the remaining servers)?

hexstar@hexstar-desktop:~$ ping ca.archive.ubuntu.com
PING gulus.usherbrooke.ca (206.167.141.10) 56(84) bytes of data.
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=1 ttl=49 time=310 ms
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=2 ttl=49 time=290 ms
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=3 ttl=49 time=294 ms
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=5 ttl=49 time=275 ms
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=6 ttl=49 time=268 ms
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=7 ttl=49 time=295 ms
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=8 ttl=49 time=313 ms
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=9 ttl=49 time=295 ms

--- gulus.usherbrooke.ca ping statistics ---
9 packets transmitted, 8 received, 11% packet loss, time 8027ms
rtt min/avg/max/mdev = 268.315/293.192/313.257/14.412 ms

hexstar@hexstar-desktop:~$ ping security.ubuntu.com
PING security.ubuntu.com (82.211.81.138) 56(84) bytes of data.
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=1 ttl=40 time=162 ms
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=2 ttl=40 time=164 ms
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=3 ttl=40 time=162 ms
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=4 ttl=40 time=159 ms
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=5 ttl=40 time=167 ms
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=6 ttl=40 time=161 ms
64 bytes from auckland.ubuntu.com (82.211.81.138): icmp_seq=7 ttl=40 time=158 ms

--- security.ubuntu.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6023ms
rtt min/avg/max/mdev = 158.591/162.406/167.939/2.874 ms

---

### Post by hexstar on 2007-08-19
This issue is also not at my ISP as shown by the following traceroute:

hexstar@hexstar-desktop:~$ traceroute ca.archive.ubuntu.com
traceroute to gulus.usherbrooke.ca (206.167.141.10), 30 hops max, 40 byte packets
 1  Hexstars-Base-Station.local (10.0.1.1)  1.563 ms  1.563 ms  1.630 ms
 2  * * *
 3  ge-2-8-ur01.city.state.area.comcast.net (68.86.249.113)  15.776 ms  12.326 ms  25.640 ms
 4  68.86.90.150 (68.86.90.150)  16.539 ms  13.166 ms  11.493 ms
 5  68.86.90.149 (68.86.90.149)  19.182 ms  16.037 ms  18.428 ms
 6  68.86.90.165 (68.86.90.165)  23.913 ms  19.706 ms  19.504 ms
 7  TenGigabitEthernet3-1.ar1.snv2.gblx.net (64.214.174.109)  23.511 ms  27.496 ms  19.186 ms
 8  teleglobe-1.ar3.PAO2.gblx.net (208.51.134.98)  164.828 ms  164.693 ms  159.176 ms
 9  if-1-0.mcore4.PDI-PaloAlto.teleglobe.net (216.6.86.5)  157.033 ms  160.687 ms  155.120 ms
10  if-4-0.mcore4.NQT-NewYork.teleglobe.net (216.6.86.14)  226.898 ms  240.040 ms  232.838 ms
11  if-1-0.mcore3.MTT-Montreal.teleglobe.net (216.6.87.22)  233.808 ms  232.579 ms  238.380 ms
12  if-3-0.mcore4.MTT-Montreal.teleglobe.net (216.6.114.2)  233.044 ms  224.062 ms  317.646 ms
13  ix-11-1.mcore4.MTT-Montreal.teleglobe.net (216.6.115.46)  221.777 ms  225.749 ms  228.819 ms
14  amtrl-rq.risq.net (192.77.63.26)  223.231 ms  239.427 ms  235.248 ms
15  dmtrl-rq.risq.net (192.77.63.50)  224.863 ms  216.458 ms  224.490 ms
16  * * *
17  gulus.usherbrooke.ca (206.167.141.10)  264.384 ms  259.474 ms  257.301 ms

hexstar@hexstar-desktop:~$ traceroute security.ubuntu.com
traceroute to security.ubuntu.com (82.211.81.138), 30 hops max, 40 byte packets
 1  Hexstars-Base-Station.local (10.0.1.1)  1.594 ms  1.597 ms  1.757 ms
 2  * * *
 3  ge-2-8-ur01.city.state.area.comcast.net (68.86.249.113)  10.800 ms *  12.515 ms
 4  68.86.90.138 (68.86.90.138)  12.901 ms  11.701 ms  21.502 ms
 5  68.86.90.149 (68.86.90.149)  14.484 ms  16.663 ms  15.120 ms
 6  68.86.90.165 (68.86.90.165)  19.395 ms  21.930 ms  18.690 ms
 7  te-4-4.car2.SanJose1.Level3.net (4.79.43.133)  27.312 ms  15.412 ms  16.988 ms
 8  ge-1-3-0-89.bbr2.SanJose1.Level3.net (4.68.18.130)  21.064 ms  18.148 ms  27.175 ms
 9  as-0-0.bbr2.London2.Level3.net (4.68.128.110)  165.076 ms  162.951 ms ae-1-0.bbr1.London2.Level3.net (212.187.128.46)  163.591 ms
10  * ae-15-51.car1.London2.Level3.net (4.68.117.15)  161.790 ms  158.803 ms
11  tge9-3-146.core-r-1.lon2.adaptplc.com (212.187.196.82)  159.762 ms  160.276 ms  169.710 ms
12  85.133.32.134 (85.133.32.134)  166.190 ms  163.701 ms *
13  * * 82.211.81.76 (82.211.81.76)  160.836 ms
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  *

(path essentially seems to end at hop 13 here...what the??)

WTF is up with these horrible speeds????

---

### Post by hexstar on 2007-08-20
***bump***

---

### Post by SikEnCide on 2007-08-20
actuly. i had this [problem upon fiesty's release, i dont wan to say it but when i reinstalled it everything works fine.

---

