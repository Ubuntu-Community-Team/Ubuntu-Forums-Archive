---
title: "xserver-common-lts-raring, can't auto remove"
date: 2013-09-27
forum: Installation &amp; Upgrades
---

### Post by destroyerzx12 on 2013-09-27
I've been messing with this for over an hr now I've looked on other threads and just can't get it to work i type sudo apt-get autoremove and it always comes up with and errors were encountered while processing:
   xserver-common-lts-raring

help would be greatly appreciated

---

### Post by destroyerzx12 on 2013-09-28
I figured it out!! 

I upgraded from 12.04 to 12.10 to 13.04 I have no idea if that what was cuasing issues but when I would type sudo apt-get autoremove. it would say usr/lib/xorg/protocol.txt to usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring
dpkg-divert: error: rename involves overwriting protocol.txt with protocol-precise.txt', not allowed.
errors were encountered while processing:
 xserver-common-lts-raring
E:Sub-process /usr/bin/dpkg returned an error code (1)

at first it said that permission was denied to protocol.txt so I changed it so I would have permission by cd /usr/lib/xorg then typing chown -R "username" protocol.txt

after I did that, thats when i got the above error so I decided to remove protocol-precise.txt I just cut it out of the xorg folder and put it in the main directory so if i had to I would still have it

after that I ran autoremove and it worked.

---

### Post by ramasuresh9 on 2013-12-07
I had similar issue please help me. 

sudo apt-get remove xserver-common-lts-raring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xserver-common-lts-raring
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1,646 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 211600 files and directories currently installed.)
Removing xserver-common-lts-raring ...
Removing 'diversion of /usr/lib/xorg/protocol.txt to /usr/lib/xorg/protocol-precise.txt by xserver-common-lts-raring'
dpkg-divert: error: rename involves overwriting `/usr/lib/xorg/protocol.txt' with
  different file `/usr/lib/xorg/protocol-precise.txt', not allowed
dpkg: error processing xserver-common-lts-raring (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 xserver-common-lts-raring
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ramasuresh9 on 2013-12-07
The above solution does not help me :(

---

