---
title: "[SOLVED] proxy settings in gnome-network-preferences doesn't apply"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by waynema on 2008-11-05
I just updated to Intrepid from Hardy. This problem suddenly appears :(

I want to use a global proxy for my system to access internet.
However, in GUI gnome-network-preferences, after setting server AND authentication and pressing "Apply System-Wide..."

the http_proxy env is set right with IP&port, but WITHOUT user\:passwd, like:
  
$ echo $http_proxy
[http://123.123.123.123:123/](http://123.123.123.123:123/)

I already checked the bug here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/271108](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/271108)

Problem above looks similar to mine, but solution doesn't work in my case.

I'm using:
gnome-control-center       1:2.24.0.1-0ubuntu7

Any idea would be great. Thanks in advance:)

---

