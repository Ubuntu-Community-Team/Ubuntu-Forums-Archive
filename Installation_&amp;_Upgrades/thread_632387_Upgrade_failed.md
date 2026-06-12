---
title: "Upgrade failed"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by zeroms on 2007-12-05
I tried to upgrade my Ubuntu Feisty to Gutsy.
:confused:Error message:
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

(I tried it Monday to and also this)
pls help.

thanks

---

### Post by Severun on 2007-12-05
Maybe there's something going on with your network that's preventing you from downloading?  Can you ping that host and connect to it via HTTP? (TCP port 80)

---

### Post by zeroms on 2007-12-05
*@*:~$ ping security.ubuntu.com
PING security.ubuntu.com (91.189.88.37) 56(84) bytes of data.
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=1 ttl=55 time=121 ms
64 bytes from auckland.canonical.com (91.189.88.37): icmp_seq=2 ttl=55 time=107 ms

--- security.ubuntu.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 5124ms
rtt min/avg/max/mdev = 107.368/114.339/121.310/6.971 ms

I can open a link in my browser, I see
BZh91AY&SY_=ia&#65533;&#65533;&#65533;_&#65533;PR&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;...........

---

