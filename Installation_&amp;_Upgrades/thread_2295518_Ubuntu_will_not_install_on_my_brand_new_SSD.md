---
title: "Ubuntu will not install on my brand new SSD"
date: 2015-09-19
forum: Installation &amp; Upgrades
---

### Post by gwelkind-w on 2015-09-19
Every time I try to install Ubuntu on my fresh-out-the-box new Samsung EVO, the installation takes me to the 'copying files...' page and then halts indefinitely (yes, I've left it on all night). I have tried this with Ubuntu 14.04, 15.04, YUMI, Rufus and Unetbootin, and two different bootable drives (yes, every permutation). It's insane, every single time the same thing happens, and it takes me about 5 minutes to even get to the screen when it hangs, so I've been wasting a looooooooot of time on this. I've checked the disk for errors in liveboot linux and in windows and seem to be in the clear. I have used gparted to clear the previous partial install after each iteration and proceed according to the basic 'install alongside other operating systems' path without checking any extra boxes.

I have the following in my twisty tie under 'copying files': 

```
einit -> bound
Sep 19 09:00:14 it NetworkManager[2190]: <info>   address 192.168.1.8
Sep 19 09:00:14 it NetworkManager[2190]: <info>   prefix 24 (255.255.255.0)
Sep 19 09:00:14 it NetworkManager[2190]: <info>   gateway 192.168.1.1
Sep 19 09:00:14 it NetworkManager[2190]: <info>   nameserver '192.168.1.1'
Sep 19 09:00:14 it NetworkManager[2190]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Sep 19 09:00:14 it NetworkManager[2190]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Sep 19 09:00:14 it avahi-daemon[1447]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.8.
Sep 19 09:00:14 it avahi-daemon[1447]: New relevant interface wlan0.IPv4 for mDNS.
Sep 19 09:00:14 it avahi-daemon[1447]: Registering new address record for 192.168.1.8 on wlan0.IPv4.
Sep 19 09:00:14 it avahi-daemon[1447]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::6a1c:a2ff:fe01:d4a4.
Sep 19 09:00:14 it avahi-daemon[1447]: New relevant interface wlan0.IPv6 for mDNS.
Sep 19 09:00:14 it avahi-daemon[1447]: Registering new address record for fe80::6a1c:a2ff:fe01:d4a4 on wlan0.*.
Sep 19 09:00:15 it NetworkManager[2190]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Sep 19 09:00:15 it NetworkManager[2190]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Sep 19 09:00:15 it NetworkManager[2190]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 19 09:00:15 it NetworkManager[2190]: <info> NetworkManager state is now CONNECTED_GLOBAL
Sep 19 09:00:15 it NetworkManager[2190]: <info> Policy set 'AUTOVIRUSDOWNLOAD' (wlan0) as default for IPv4 routing and DNS.
Sep 19 09:00:15 it NetworkManager[2190]: <info> DNS: starting dnsmasq...
Sep 19 09:00:15 it NetworkManager[2190]: <warn> dnsmasq not available on the bus, can't update servers.
Sep 19 09:00:15 it NetworkManager[2190]: <error> [1442653215.681021] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Sep 19 09:00:15 it NetworkManager[2190]: <warn> DNS: plugin dnsmasq update failed
Sep 19 09:00:15 it NetworkManager[2190]: <info> Writing DNS information to /sbin/resolvconf
Sep 19 09:00:15 it dnsmasq[11082]: started, version 2.68 cache disabled
Sep 19 09:00:15 it dnsmasq[11082]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Sep 19 09:00:15 it dnsmasq[11082]: DBus support enabled: connected to system bus
Sep 19 09:00:15 it dnsmasq[11082]: warning: no upstream servers configured
Sep 19 09:00:15 it NetworkManager[2190]: <info> Activation (wlan0) successful, device activated.
Sep 19 09:00:15 it dbus[1381]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Sep 19 09:00:15 it NetworkManager[2190]: <warn> dnsmasq appeared on DBus: :1.74
Sep 19 09:00:15 it NetworkManager[2190]: <info> Writing DNS information to /sbin/resolvconf
Sep 19 09:00:15 it dnsmasq[11082]: setting upstream servers from DBus
Sep 19 09:00:15 it dnsmasq[11082]: using nameserver 192.168.1.1#53
Sep 19 09:00:15 it dbus[1381]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
update_release_notes_label()
Sep 19 14:00:22 it ntpdate[11180]: step time server 91.189.94.4 offset 18000.135145 sec
Sep 19 14:00:34 it NetworkManager[2190]: <info> (wlan0): IP6 addrconf timed out or failed.
Sep 19 14:00:34 it NetworkManager[2190]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Sep 19 14:00:34 it NetworkManager[2190]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Sep 19 14:00:34 it NetworkManager[2190]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Sep 19 14:00:49 it wpa_supplicant[2385]: wlan0: CTRL-EVENT-SCAN-STARTED 
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 84401 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 84558 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 84432 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 84650 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 84764 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 84727 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 84865 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:131: Warning: Source ID 84892 was not found when attempting to remove it
  GLib.source_remove(self.rows_changed_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 85021 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/ubiquity/ubiquity/frontend/gtk_components/nmwidgets.py:18: Warning: Source ID 85230 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)

```

---

### Post by oldfred on 2015-09-19
What flavor of Ubuntu, or standard Ubuntu?
What then is rest of system? cpu, motherboard, video card/chip?

UEFI or BIOS install?
If only Ubuntu MBR(msdos) or gpt(GUID).

I always partition in advance as I want gpt on SSD. And then install with Something Else from hard drive to SSD is less than 10 Minutes.

---

