---
title: "[SOLVED] Intrepid: problem with static ip address after upgrade"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by megamania on 2008-10-01
After upgrading from 8.04 to 8.10, my ethernet interface gets a dynamic ip address instead of the static ip address I set in /etc/network/interfaces:
```

:~$cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

```

When I start Ubuntu, the interface is assigned the address 192.168.1.70, which is the first address made available by the router. If I restart the network with "/etc/init.d/networking restart", I get the following output:
```

[sudo] password for xxx: 
 * Reconfiguring network interfaces...                                   [ OK ] 
 * Stopping NTP server ntpd
   ...done.
 * Starting NTP server ntpd
   ...done.

```
and then it hangs and I have to ctrl-c to exit. After that, however, the network is correctly configured (i.e. the address becomes 192.168.1.3).

As I said, this happens since I upgraded from 8.04 to 8.10 Alpha 6.

Any suggestions?

---

### Post by muzincs on 2008-10-01
This is a known bug.  Remove all four packages that show up as installed when you search for "network manager" in synaptic.  Then reboot.  You may have to do it again each time an upgrade reinstalls network manager.  Hope this helps.

---

### Post by ktp on 2008-10-01
This is a known bug: 
[https://bugs.launchpad.net/network-manager/+bug/256054](https://bugs.launchpad.net/network-manager/+bug/256054)

You can try to use the "ifupdown" system setting plugin, by adjusting a
configuration file followed by a system restart.

/etc/NetworkManager/nm-system-settings.conf:
  [main]
  plugins=keyfile,ifupdown

---

### Post by megamania on 2008-10-02
Thank you to both of you.

I read through the bug-report, and although I understand *how* to fix it, there's one thing I'm not sure I get: is network-manager currently using a different configuration file?
If that's the case, is it "normal" to have two different systems, both active, to manage the network interfaces? And why does a simple restart work?

If anybody is willing to explain, I'd appreciate it.

---

### Post by ktp on 2008-10-02
> **megamania said:**
> Thank you to both of you.

I read through the bug-report, and although I understand *how* to fix it, there's one thing I'm not sure I get: is network-manager currently using a different configuration file?
If that's the case, is it "normal" to have two different systems, both active, to manage the network interfaces? And why does a simple restart work?

If anybody is willing to explain, I'd appreciate it.

I think the idea what to make it just work without having a need for configuration file...I could be wrong so you can go read about it here:
[http://www.gnome.org/projects/NetworkManager/]("http://www.gnome.org/projects/NetworkManager/")
[http://live.gnome.org/NetworkManager]("http://live.gnome.org/NetworkManager")

---

