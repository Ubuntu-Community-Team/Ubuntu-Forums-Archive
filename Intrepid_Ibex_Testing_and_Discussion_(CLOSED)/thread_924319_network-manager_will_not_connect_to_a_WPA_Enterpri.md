---
title: "network-manager will not connect to a WPA Enterprise network"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2008-09-19
I'm having troubles connecting to my campus wireless network with Intrepid Ibex (updated 19 Sept 2008). I have a Dell XPS m1330 laptop with ipw3945 card. This laptop connects fine under Ubuntu 8.04. 

Here are the setting my campus suggests I use.

SSID: uconnect.utah.edu
Encryption: WPA Enterprise
Encryption Type or Key: TKIP
EAP Method: PEAP
CA Server Certificate: Entrust.net (do not need to enter under Network Manager under Ubuntu 8.04)
Authentication Method: MS-CHAP v2
Username: *****
Password: *****

[https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/272185](https://bugs.edge.launchpad.net/ubuntu/+source/network-manager/+bug/272185)

---

### Post by gaussian on 2008-09-19
Can confirm this, with similar hardware (ip3945 card), different University. Was working for me under Gutsy, skipped Hardy before had time to test.

As an aside (workaround, not a fix): Install wicd and generate a template for this. Works for me.

---

### Post by Technoviking on 2008-09-19
> **gaussian said:**
> Can confirm this, with similar hardware (ip3945 card), different University. Was working for me under Feisty, skipped Hardy before had time to test.

As an aside (workaround, not a fix): Install wicd and generate a template for this. Works for me.

Would you confirm my launchpad bug?

Many thanks!!!

---

### Post by gaussian on 2008-09-19
> **Mike said:**
> Would you confirm my launchpad bug?

Many thanks!!!

As soon as launchpad comes back online :)

*UPDATE: done*

---

### Post by Nullack on 2008-09-19
> **gaussian said:**
> As soon as launchpad comes back online :)

*UPDATE: done*

Please note, confirmed is a status. A bug isnt confirmed by saying its confirmed in a comment. Theres lots of good info to help on the ubuntu wiki.

---

