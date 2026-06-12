---
title: "Link http://in.archive.ubuntu.com/ubuntu/pool/main is not working"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by bhupeshrawal on 2007-03-01
I am not able to access [http://in.archive.ubuntu.com/ubuntu/pool/main](http://in.archive.ubuntu.com/ubuntu/pool/main) and thats why not able to do apt-get update.

Is this link is not working?

thanks
Bhupesh

---

### Post by Kateikyoushi on 2007-03-01
It is working from me, you could try to remove the "in." from the beginning that server might work or choose another mirror.

---

### Post by bhupeshrawal on 2007-03-06
There might be some networking issue in my company. I will update what the problem was...

---

### Post by Kateikyoushi on 2007-03-06
Similar problem is reported frequently these days so not necessarly your net's fault.

You could try to change the http to ftp in your sources.list, that worked for some.

---

### Post by bhupeshrawal on 2007-03-07
bad luck ftp is also not working :(

here is the traceroute from india:


Traceroute
Result for in.archive.ubuntu.com:

traceroute: Warning: in.archive.ubuntu.com has multiple addresses; using 91.189.89.6
traceroute to in.archive.ubuntu.com (91.189.89.6), 30 hops max, 38 byte packets
 1  59.163.11.57.static.vsnl.net.in (59.163.11.57)  0.777 ms  0.629 ms  0.611 ms
 2  203.197.33.130.static.vsnl.net.in (203.197.33.130)  0.651 ms  0.591 ms  0.582 ms
 3  59.163.16.146.static.vsnl.net.in (59.163.16.146)  189.230 ms  189.069 ms  189.587 ms
 4  216.6.97.45 (216.6.97.45)  190.066 ms  189.406 ms  189.694 ms
 5  g6-2.core01.jfk05.atlas.cogentco.com (154.54.12.185)  190.002 ms  189.394 ms  189.653 ms
 6  v3495.mpd03.jfk02.atlas.cogentco.com (154.54.6.45)  189.549 ms  189.794 ms  189.612 ms
 7  t2-2.mpd02.lon01.atlas.cogentco.com (66.28.4.42)  259.674 ms  259.616 ms  259.350 ms
 8  t4-1.mpd01.lon01.atlas.cogentco.com (130.117.2.17)  261.600 ms  261.557 ms  262.807 ms
 9  149.6.81.211 (149.6.81.211)  260.929 ms  260.121 ms  259.946 ms
10  byrd.canonical.com (91.189.88.11)  261.784 ms  262.034 ms  261.929 ms
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *

---

### Post by Kateikyoushi on 2007-03-07
Indeed the problem is in your connection or the server.

---

