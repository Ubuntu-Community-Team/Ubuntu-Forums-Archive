---
title: "Can't get Zoom ADSL modem to connect to internet"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by googlebytes on 2007-04-15
First, I have to say I am completely new to Ubuntu. I have been a Windows man. I have Edgy 6.1 installed. I am trying to configure my new Zoom X5v 5030 ADSL modem with an ethernet connection. I have followed the Zoom documentation and flashed the modem with both encapsulation settings (PPP) my DSL provider, Qwest, uses, but still cannot connect to the internet. I got the user name and password from Qwest and flashed with that. I followed the Zoom's manual instruction for DEBIAN to make sure the file "/etc/network/interfaces" contains the line: iface eth0 inet dhcp. My Edgy file already contained this line.

I also changed Firefox browser by typing "about:config" into the location bar and changing the default false setting of "network.dns.disableIPv6" to true. -- still no general internet connection, although it does seen to be able to communicate with the Zoom VOIP gateway console page. 

My network setting is set for a wired connection with address DHCP. Is this right for PPP connection?
Please help. I'm sure I have some obscure setting incorrect somewhere.

---

