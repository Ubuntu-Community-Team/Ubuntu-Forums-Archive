---
title: "How to save network setting"
date: 2005-07-31
forum: Installation &amp; Upgrades
---

### Post by batrachian on 2005-07-31
New to linux and ubuntu as well. So here comes the rookie's problem.

I am able to configure the network setting well once the system starts. However, it seems always switching back to original status once rebooting. As a result, the network  configuration takes a long while when starting and I have to configure the network each time system starts.

Please help and thanks in advance.

---

### Post by batrachian on 2005-08-02
anybody has any ideas?

Thanks

---

### Post by heimo on 2005-08-02
When you configure network the way you do now, does /etc/network/interfaces file change?

You can edit it directly too. *man interfaces* helps, basicly - you put in something like this (for static configuration):
 ```
 
			  auto lo eth0
			  iface eth0 inet static
				   address 192.168.1.1
				   netmask 255.255.255.0

``` 

You should also have dns servers listed in /etc/resolv.conf (man resolv.conf).

---

