---
title: "Off network updating"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by AmericanAqualung on 2007-03-10
Hey,
I'm in charge of managing several linux boxes that are part of a linux cluster.  They are all running Ubuntu Dapper Drake.  In our configuration, only the head node has access to the internet, and none of the other nodes do (the head has two NICs and the rest are on a private LAN).
Obviously it is trival to apply security updates to the head node, however I'm wondering if there is an easy way to apply security and library updates to the other nodes.  For example is there a list of most recent upgrades or a cache I can download somewhere?  This has really become a big priority since I realized this weekend was daylight savings.  Thanks.

-Andy

---

### Post by aa.ivanov on 2007-03-10
I have no experience with clusters, but if it was me to deal with this I would set the internet-connected node to be a local mirror of the ubuntu update servers. Then the rest of the nodes would be able download the updates from a mirror on the internal network.

May be this would be my starting point:
[https://help.ubuntu.com/community/Rsyncmirror](https://help.ubuntu.com/community/Rsyncmirror)

---

### Post by AmericanAqualung on 2007-03-10
Thanks!  This definately seems like it would work.  This should work perfectly, because the work nodes are always able to connect to the head and vice versa on the internal network, so we can either set up the head node to act as the mirror, or use another machine (w/ a lesser cpu) in a similar dual nic link to act as the mirror.  I just need to wait until I get back on site to discuss which route to use with my peers.

---

