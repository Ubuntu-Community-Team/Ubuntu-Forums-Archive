---
title: "ubuntu on a cluster"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by satbobo on 2007-04-02
Hi everybody.
I am a completely newbie in setting up networks of computers and I have been told to setup a cluster of 16 computers running ubuntu.
Can you give me some references or hints on how to do that?
Cheers,
sat

---

### Post by satbobo on 2007-04-04
please...noone can point me in the right direction?
thank you...

---

### Post by az on 2007-04-04
(old page)
[https://help.ubuntu.com/community/UbuntuOnCluster?highlight=%28cluster%29](https://help.ubuntu.com/community/UbuntuOnCluster?highlight=%28cluster%29)

Packages:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=cluster&searchon=all&subword=1&version=edgy&release=all&page=1&number=50](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=cluster&searchon=all&subword=1&version=edgy&release=all&page=1&number=50)

---

### Post by satbobo on 2007-04-04
Thank you... I am quite newbie.. I hope I can follow that guide smoothly...
Even if actually I cant understand what they mean with:
"nat active on the server or all machines must receive a public IP address by dhcp"
(how can I do that?)

Do I need a "server" release of ubuntu or just a simple desktop one?
Thank you

---

### Post by rillip on 2007-04-04
What you're asking is really far beyond the scope of the forum.  You're talking about server administration here.  If you've been asked to set up an Ubuntu cluster, and you don't understand that last section, you're not cut out for the job, no offense.  It's trying to tell you they all get an IP address in the normal fashion, not just internal IP addresses.  An internal IP is one like 192.168.0.101 which you would have only routable inside a lan.  It wants each machine to have an externally routable ip address, i.e. 208.234.30.80.

I've never set up an ubuntu cluster, but I can confidently say that the Ubuntu desktop package isn't made for this sort of thing.

I don't want to sound rude, but this isn't really a DIY project if you don't know about the technologies involved.

---

