---
title: "Ubuntu 12.04 Automatic (VPN) addresses only ignored?"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by ustramooner on 2012-05-16
It seems that ubuntu 12.04 is ignoring the directive in the VPN configuration "Automatic (VPN) addresses only". As I understand (and how it worked before), this option means you don't pull the DNS config if this is selected.

I have tried disabling dnsmasq as per ([http://ubuntuforums.org/showthread.php?t=1968061](http://ubuntuforums.org/showthread.php?t=1968061))... but I'm stilling getting the VPN's nameserver in the /etc/resolve.conf file.

My scenario is I'm VPN to my home network from work, and I want to access my local devices, but I don't need to browse the web or look up any dns through it.

This worked fine before, but now all my DNS requests are taking ages whenever I'm connected to VPN.

---

### Post by jdthood on 2012-11-05
It is possible that the VPN nameserver address is being included statically in resolv.conf. This can happen if you upgraded from an earlier version of Ubuntu and the upgrade process decided to create a symbolic link /etc/resolvconf/resolv.conf.d/tail -> original. If this symbolic link exists and /etc/resolvconf/resolv.conf.d/original contains a nameserver address on the VPN then you should do the following.

1. Make sure that any nameserver addresses and search paths in /etc/resolvconf/resolv.conf.d/original have been entered into appropriate fields either in the NetworkManager connection details dialog (if you are using NetworkManager) or in /etc/network/interfaces (if you are using ifup).

2. Replace the symlink with a symlink /etc/resolvconf/resolv.conf.d/tail -> /dev/null

3. Either deconfigure and configure all interfaces or reboot.

---

