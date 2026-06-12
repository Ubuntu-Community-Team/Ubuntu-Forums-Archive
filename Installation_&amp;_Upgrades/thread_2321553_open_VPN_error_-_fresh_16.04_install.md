---
title: "open VPN error - fresh 16.04 install"
date: 2016-04-23
forum: Installation &amp; Upgrades
---

### Post by rich-looklively on 2016-04-23
Hi,

On a fresh install of 16.04 kubuntu.

Error on importing openvpn conf into networkmanager;

"connection.gateway-ping-timeout: cannot set property: value of "6619252" of type 'guint' is invalid or out of range for property type 'gateway-ping-timeout' of type 'guint' "

Any confirmation, or ideas?

Thanks.

---

### Post by bashiergui on 2016-04-24
What's your gateway set to?

Have you checked this
[https://help.ubuntu.com/16.04/serverguide/openvpn.html](https://help.ubuntu.com/16.04/serverguide/openvpn.html)

---

### Post by rich-looklively on 2016-04-25
It's set the same as it was before the fresh install.
And the same as it is on my other openvpn-is-working machine.

I just import the conf as supplied by my vpn supplier.

Thanks for your suggestion.
:)

---

### Post by dreibh on 2016-04-25
I observe the same issues with PPTP and OpenConnect VPNs. I created a bug report: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1574826](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1574826) .

---

### Post by rich-looklively on 2016-04-29
Heres how I got round it...

I put the vpn conf files supplied by my provider into */etc/openvpn/ *[I][I]then when 
rebooting it connects to the vpn servers, or when running "service 
openvpn start" (as root).

Perhaps this helps someone?[/I][/I]**

---

### Post by sakrani on 2016-05-10
I copy/pasted the content of /etc/NetworkManager from fedora 23(KDE) running on the same machine to the same folder of my kubuntu installation and it works very fine, I hope it helps

---

