---
title: "Open VPN Bridge"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by xxilus on 2010-05-19
I am trying to install openVPN on ubuntu server 10
I am working through [https://help.ubuntu.com/community/OpenVPN]("https://help.ubuntu.com/community/OpenVPN")
but I am running into problems. I think that I configured my network interfaces file incorrectly
/etc/network/interfaces
This is what it looked like before.
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```


And this is what I tried (and failed) to add the bridge
```

auto lo br0
iface lo inet loopback

iface br0 inet dhcp
  bridge_ports eth0
  bridge_fd 9      ## from the libvirt docs (forward delay time)
  bridge_hello 2   ## from the libvirt docs (hello time)
  bridge_maxage 12 ## from the libvirt docs (maximum message age)
  bridge_stp off   ## from the libvirt docs (spanning tree protocol)


auto eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down 

```

this is apparently not correct, because it just killed my internet connection.

Can somebody help me write this configuration file?
Also, I does anybody know where I can get documentation on this configuration syntax?
Do you know what books will help me understand this?
what is a network bridge?

---

### Post by xxilus on 2010-05-20
I just tried this. It did not work either.
```
auto lo
iface lo inet loopback

auto br0
iface br0 inet dhcp
	bridge_ports eth0 tap0
	pre-up  openvpn --mktun --dev tap0

auto eth0
iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down 

```

---

### Post by xxilus on 2010-05-26
I got it working without a bridge.
The instructions in the attached rtf is what worked for me.

---

