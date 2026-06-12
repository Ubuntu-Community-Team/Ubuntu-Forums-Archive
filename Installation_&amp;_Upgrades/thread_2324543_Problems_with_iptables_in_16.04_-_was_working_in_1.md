---
title: "Problems with iptables in 16.04 - was working in 14.04 (insmod)"
date: 2016-05-14
forum: Installation &amp; Upgrades
---

### Post by theprez on 2016-05-14
Hello,

I thought I'd finally get more up to date and did a fresh install of 16.04 and am attempt to configure iptables - running the following command (which I need for openvpn purposes) generates an error:

[FONT=Menlo]iptables -t NAT -A POSTROUTING -s 10.8.0.0/24 -o en01 -j MASQUERADE[/FONT]
[FONT=Menlo]iptables v1.6.0: can't initialize iptables table `NAT': Table does not exist (do you need to insmod?)[/FONT]


I'm a little unclear on why this isn't working or what insmod is (doesn't appear to be a program that can be installed thru apt get) 

Any ideas?

Thanks

---

