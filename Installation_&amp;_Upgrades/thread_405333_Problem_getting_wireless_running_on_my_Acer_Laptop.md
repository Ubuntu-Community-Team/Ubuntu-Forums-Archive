---
title: "Problem getting wireless running on my Acer Laptop"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by dmercie on 2007-04-09
Hi, I just installed Kubuntu 6.10 Edgy Eft on my Acer Aspire 3610.

wired networking (eth0) works perfect, but I never succeded in making wireless (broadcom) on it.

Furthermore, when I tried several approaches on different forums, I "lost" my eth1 interface which is my wireless network card.

When I tried to compile acer_acpi 0.4, it didn't get through (errors at the make step) but succeded with acer_acpi 0.3. Wireless led does not come up.

ifconfig gives the following:
eth0      Lien encap:Ethernet  HWaddr 00:0A:E4:E7:91:76
          inet adr:192.168.1.106  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::20a:e4ff:fee7:9176/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:7325 erreurs:0 :0 overruns:0 frame:0
          TX packets:5748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:7773121 (7.4 MiB) Octets transmis:619555 (605.0 KiB)
          Interruption:225 Adresse de base:0x8000

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)

ndiswrapper -l gives:
Installed ndis drivers:
bcmwl5  driver present, hardware present

cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

If anything else is required to help, please post.

btw I am just starting with linux, but read a lot of it...

Thank you for your leniency.

dm

---

### Post by stchman on 2007-04-10
> **dmercie said:**
> Hi, I just installed Kubuntu 6.10 Edgy Eft on my Acer Aspire 3610.

wired networking (eth0) works perfect, but I never succeded in making wireless (broadcom) on it.

Furthermore, when I tried several approaches on different forums, I "lost" my eth1 interface which is my wireless network card.

When I tried to compile acer_acpi 0.4, it didn't get through (errors at the make step) but succeded with acer_acpi 0.3. Wireless led does not come up.

ifconfig gives the following:
eth0      Lien encap:Ethernet  HWaddr 00:0A:E4:E7:91:76
          inet adr:192.168.1.106  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::20a:e4ff:fee7:9176/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:7325 erreurs:0 :0 overruns:0 frame:0
          TX packets:5748 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:7773121 (7.4 MiB) Octets transmis:619555 (605.0 KiB)
          Interruption:225 Adresse de base:0x8000

lo        Lien encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:0 (0.0 b) Octets transmis:0 (0.0 b)

ndiswrapper -l gives:
Installed ndis drivers:
bcmwl5  driver present, hardware present

cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

If anything else is required to help, please post.

btw I am just starting with linux, but read a lot of it...

Thank you for your leniency.

dm

If your wireless card is a Broadcom 43xx wireless I have a procedure on my website to install ndiswrapper and windows drivers.

[http://www.stchman.com](http://www.stchman.com)

You might need to uninstall the old Broadcom wireless drivers.

---

