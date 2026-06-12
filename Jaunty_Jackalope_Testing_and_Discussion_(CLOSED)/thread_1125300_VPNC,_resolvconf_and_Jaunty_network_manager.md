---
title: "VPNC, resolvconf and Jaunty network manager"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hartz on 2009-04-14
Hello all.

It seems vpnc expects /etc/resolv.conf to be a symlink to /etc/resolvconf/run/resolv.conf

If it is not, it exists with an error.  If I make it a symlink, and start vpnc again, all works fine for a while.

But I think for some reason or another network manager occasionally goes and puts the info it got from DHCP back into /etc/resolv.conf, killing the DNS info gotten from the VPN connection.  Worse, sometimes /etc/resolv.conf turns back into a file!

Ever seen something like that?

---

