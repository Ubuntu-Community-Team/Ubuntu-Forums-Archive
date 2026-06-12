---
title: "Network Device keeps resetting to Loopback Interface"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by denclar on 2008-01-17
HI all--

I'm brand new to Ubuntu.  Just did a dual boot install to Ubuntu 7.10 to my HP desktop and can't reach the internet.  When I go to "Network Tools" the Network Device is always designated as Loopback Interface.  Even if I change it to Wireless Interface, as soon as I close Network Tools it's back to Loopback.

I'm using a Belkin wireless adapter.

Here are some of the settings:

Iwconfig shows:
  Wlan0  IEEE 802.22g  Essid  “RB6S0”  [the correct name of my network]
  Mode:  Managed  Frequency:2.422 GHz  Access Point 00:18:10:E5:B0:AC
  Retry min Limit:7   TRS thr:off  Fragment thr-2346 B
  Link Signal level = -59dBm
  All the rest of the entries are zeros

System Administration|Network shows:

  Wireless Connection is checked   Click on it—
	Network name is correct
	Password type is Hex
	Password is correct
	Configuration is DHCP

System Administration|Network Tools shows:
  Network Device is Loopback Interface(lo)
  When I change Network Device to Wireless interface (wlan0) I get 2 protocols in IP Information window:
  	IPv4    IP Address = 192.168.1.3  Netmask/Prefix  =  255.255.255.0 Broadcast = 192.168.1.255
      	And
	IPv6  IPAddress = fe80::211:50ff:fe88:7b1a  64  and Scope = Link

Interface Information shows:
	Hardware address = 00:11:50:88:7b:1a
	Multicast= Enabled
	MTU = 1500
	Link Speed = not available
	State = Active

Interface Statistics shows that bytes are being transmitted and received

BUT—When I close the Network Tools window and reopen it, the network device  is reset to Loopback Interface.

When I reset the Network Tools to Wireless Interface and enter an address using Firefox, the wireless adapter lights so I am reaching the wireless adapter but I can’t access the internet address.

When I was trying to set up a driver for the wireless adapter, I executed some commands I got from the forums although I didn't have any idea what I was doing.  I suspect I may have messed things up at that  point.

Any help will be greatly appreciated--and please remember that I am the ultimate beginner although I want to learn my way around linux/ubuntu.

Thanks to all.

Dennis

---

