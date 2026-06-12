---
title: "Internet documentation for Jaunty"
date: 2009-02-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ddrichardson on 2009-02-22
I and the documentation team are in the process of updating the system documentation to reflect changes in Jaunty.

We need feedback from anyone with experience of using NetworkManager to connect to:

[LIST]
[*]Mobile Broadband
[*]DSL
[*]Virtual Private Networks
[/LIST]
I don't have any of these connections to test with so am not able to test and am concerned that these sections will be lacking.  I am however able to write up and commit any input anyone has.

I'm posting this in the absolute beginners section because there is a good cross section of experienced users who can help and a great resource of new users who can relate actual problems encountered in attempting these connection types.

Please, please don't use this thread as a place to discuss dial up network connections.  I am aware of this deficit in NetworkManager and am working with several bug reports to provide a stable documentation solution for release.

---

### Post by perlluver on 2009-02-23
What kind of documentation are you looking for on DSL?  I have a Verizon DSL Broadband connection, and it uses dhcp to obtain the IP address.  Let me know so I can help out.

---

### Post by ddrichardson on 2009-02-23
Network manager should be able to connect to DSL and has a tab for settings, I *think* this is for PPPoE. I suspect that most ADSL connections have a router doing the connection and sending DHCP offers to connected machines. For DSL Iam particularly interested in any connections provided by a USB DSL modem - such as those used by AOL (which is quite popular in the UK still, for example).

Any experience, problems or information that people think might be useful to new users in configuring their network connections is welcome.

Actually, I am wondering if users differentiate connection type from provider - it might be an idea to provide a set of steps for each provider.

---

### Post by mr.p on 2009-02-23
What kind of information are you after?  A how to connect to a VPN using NetworkManager?

I can test a few of these things out so let me know.

---

### Post by ddrichardson on 2009-02-24
> **mr.p said:**
> What kind of information are you after?  A how to connect to a VPN using NetworkManager?

I can test a few of these things out so let me know.
Yes thanks, VPN would be appreciated - what steps you took in NM and any problems encountered (such as installing extra packages - if necessary). Screencaps are not used in the documentation because of translation issues but if its not a problem a grab of the main screens is useful for me to get the right wording.

---

### Post by ddrichardson on 2009-02-24
> **u.lover said:**
> Yeah, tell bro. I've two different DSL connections to connect with internet
If you connected using NetworkManager, wat providers you use, how its connected and steps you took to get it to work. Was it straight forward or did you need to install any packages or refer to any support pages?

Really, anything that you consider might not be apparent to someone who is new to Ubuntu and is generally unfamiliar with IT.

---

### Post by perlluver on 2009-02-24
With Verizon DSL, routed through a Linksys Router, I am automatically connected to the internet upon boot-up.  The IP address is obtained through DHCP.  

However in order for the DSL modem to be set-up, it has to either be set-up in Windows first, or you can gain access to the modem via 192.168.1.1.  

Let me know any other info you need, I will check this thread later on.

---

### Post by ddrichardson on 2009-02-24
> **perlluver said:**
> However in order for the DSL modem to be set-up, it has to either be set-up in Windows first, or you can gain access to the modem via 192.168.1.1.
Thats a good point - so the connection to the router is picked up as auto eth0 and then you connect the router to a DSL service through its internal server?

---

### Post by perlluver on 2009-02-24
> **ddrichardson said:**
> Thats a good point - so the connection to the router is picked up as auto eth0 and then you connect the router to a DSL service through its internal server?

I don't understand that question.  So here is my explanation: My computer is hooked up to a Linksys Router, which is in turn connected to the DSL modem.  The DSL modem is connected to the internet.  And it is picked up as auto eth0 on the network manager.

---

### Post by ddrichardson on 2009-02-24
> **perlluver said:**
> I don't understand that question.  So here is my explanation: My computer is hooked up to a Linksys Router, which is in turn connected to the DSL modem.  The DSL modem is connected to the internet.  And it is picked up as auto eth0 on the network manager.
Thanks, it wasn't a question - just needed confirmation I understood your setup.

Its a good point though - I tend to assume that all users are coming from Windows which obviously isn't the case, so I need to add that a user might need to set up their Verizon account through 197.168.1.1 or whatever.

---

### Post by perlluver on 2009-02-24
> **ddrichardson said:**
> Thanks, it wasn't a question - just needed confirmation I understood your setup.

Its a good point though - I tend to assume that all users are coming from Windows which obviously isn't the case, so I need to add that a user might need to set up their Verizon account through 197.168.1.1 or whatever.

Indeed, it might be a bit difficult to do through the modem itself but it can be done.

---

### Post by ikisham on 2009-02-25
Here where I live (São Paulo, Brazil) I'm using (A)DSL. It's like perlluver said, only I haven't a router so there's no connection until I configure it (basically give the username and the password). That's why some people talk about the system not searching stuff online while installing, at least unless the user authorizes, cos it's just a chance to hinder the process when there's that problem with too much traffic at the servers. Now I'm using 8.04 and the NM is an older version; but I've used Interepid for 3 months. I'm not sure why but I've configured the network through pppoeconf and then the NM showed 'network unmanaged' like if it was overidden from the pppoeconf settings. Here in Hardy it doesn't show that cos, I think, it has that blocking function that's not present in Intrepid.
Anyway, both CrunchBang Linux and Knoppix 6 have a similar NM to ubuntu (only they have too that password checking enabled) and for both it boots automatically in eth0 but that doesn't work for us here (unless there's a router configured before the modem) since we need to authenticate the session. So we must create a DSL connection, i.e., input the username and the password, then I'm not sure if it's needed to logout before that takes effect but we then choose the DSLn. There are options to make it the default connection and to connect at boot time if I remember well but I don't remember if it works. Note that when configured through pppoeconf the network connection works allright. As stated, the NM in Intrepid is just as the ones in CB an Knoppix but I don't know if it has something to do with the desktop design or if it didn't work at first but when I though of using it (also in Hardy) it was too late since I had it configured already. But I have only one connection and no wireless so no need for the best feature of the NM that is to manage multiple connections.

---

### Post by ddrichardson on 2009-02-26
Thanks ikisham - yes NM now controls those files.

---

### Post by markbuntu on 2009-02-27
My att dsl modem has an address of 192.168.1.1. It can be configured, reset, tested etc, through firefox. Jaunty connects through a ethernet switch and wireless router to the dsl modem automatically.(This machine is hardwired).

---

### Post by ddrichardson on 2009-02-27
> **markbuntu said:**
> My att dsl modem has an address of 192.168.1.1. It can be configured, reset, tested etc, through firefox. Jaunty connects through a ethernet switch and wireless router to the dsl modem automatically.(This machine is hardwired).
Thanks for responding - to clarify, do you have a DSL modem attached to a router? Does NetworkManager connect to an ethernet or a wireless connection?

---

### Post by markbuntu on 2009-02-28
> **ddrichardson said:**
> Thanks for responding - to clarify, do you have a DSL modem attached to a router? Does NetworkManager connect to an ethernet or a wireless connection?

The DSL modem is attached to the router which is attached to the ethernet switch which is attached to the pc. Like this

Internet--ATT DSL Modem--Belkin Wireless G Router--Trendnet Ethernet Switch--PC. It is all hardwired together. It seems the switch and router are transparent to Network Manager. There are no other machines on the internal network right now.

Here is the relevant /var/log/syslog excerpt from the last jaunty boot.

```

Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  (eth0): device state change: 1 -> 2 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  (eth0): bringing up device. 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  (eth0): preparing device. 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  (eth0): deactivating device (reason: 2). 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  (eth0): carrier now ON (device state 2) 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  (eth0): device state change: 2 -> 3 
Feb 25 16:05:24 mark-jaunty-desktop kernel: [   28.837459] r8169: eth0: link up
Feb 25 16:05:24 mark-jaunty-desktop kernel: [   28.837471] r8169: eth0: link up
Feb 25 16:05:24 mark-jaunty-desktop nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_e0_4d_9e_7b_81
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  dhclient started with pid 4145 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Feb 25 16:05:24 mark-jaunty-desktop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb 25 16:05:24 mark-jaunty-desktop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb 25 16:05:24 mark-jaunty-desktop dhclient: All rights reserved.
Feb 25 16:05:24 mark-jaunty-desktop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb 25 16:05:24 mark-jaunty-desktop dhclient: 
Feb 25 16:05:24 mark-jaunty-desktop NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit 
Feb 25 16:05:24 mark-jaunty-desktop dhclient: Listening on LPF/eth0/00:e0:4d:9e:7b:81
Feb 25 16:05:24 mark-jaunty-desktop dhclient: Sending on   LPF/eth0/00:e0:4d:9e:7b:81
Feb 25 16:05:24 mark-jaunty-desktop dhclient: Sending on   Socket/fallback
Feb 25 16:05:25 mark-jaunty-desktop avahi-daemon[3380]: Registering new address record for fe80::2e0:4dff:fe9e:7b81 on eth0.*.
Feb 25 16:05:27 mark-jaunty-desktop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Feb 25 16:05:27 mark-jaunty-desktop dhclient: DHCPOFFER of 192.168.2.2 from 192.168.2.1
Feb 25 16:05:27 mark-jaunty-desktop dhclient: DHCPREQUEST of 192.168.2.2 on eth0 to 255.255.255.255 port 67
Feb 25 16:05:27 mark-jaunty-desktop dhclient: DHCPACK of 192.168.2.2 from 192.168.2.1
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound 
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>    address 192.168.2.2 
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>    prefix 24 (255.255.255.0) 
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>    gateway 192.168.2.1 
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>    nameserver '192.168.2.1' 
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>    nameserver '64.105.204.28' 
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>    nameserver '64.105.124.155' 
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>    domain name 'WTFOVER' 
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Feb 25 16:05:27 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Feb 25 16:05:27 mark-jaunty-desktop dhclient: bound to 192.168.2.2 -- renewal in 2147483648 seconds.
Feb 25 16:05:27 mark-jaunty-desktop avahi-daemon[3380]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.2.
Feb 25 16:05:27 mark-jaunty-desktop avahi-daemon[3380]: New relevant interface eth0.IPv4 for mDNS.
Feb 25 16:05:27 mark-jaunty-desktop avahi-daemon[3380]: Registering new address record for 192.168.2.2 on eth0.IPv4.
Feb 25 16:05:28 mark-jaunty-desktop NetworkManager: <info>  (eth0): device state change: 7 -> 8 
Feb 25 16:05:28 mark-jaunty-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS. 
Feb 25 16:05:28 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) successful, device activated. 
Feb 25 16:05:28 mark-jaunty-desktop NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Feb 25 16:05:31 mark-jaunty-desktop ntpdate[4208]: adjust time server 91.189.94.4 offset -0.375309 sec
Feb 25 16:05:34 mark-jaunty-desktop kernel: [   39.648022] eth0: no IPv6 routers present


```

---

### Post by ddrichardson on 2009-02-28
OK so as far as NM is concerned its an ethernet connection to a DHCP server.  Thanks again.

What I need now is someone who has tried to connect using a mobile internet dongle or who has had to use the DSL settings in NM.

---

### Post by redmun on 2009-03-04
Ive tried to connect through mobile broadband :(
Its a Dell 5520 Generic I Mobile Broadband (3G HSPDA) Minicard (Actually a Expedite EU870D MiniCard (Rev. 02)). Broadband service through Telstra Bigpond NextG service (Australia). The machine is a Dell inspiron 1520 laptop. Tried about a dozen linux/BSD distros, with no success connecting to the internet through my card. Ive trawled the internet from top to bottom, and the only information regarding my card either is open ended (no solution) or reads like a scientific journal. The card works fine in windows (Ive been trying to shake the habit, but without hardware support for my card i aint going nowhere ). The service provider (bigpond) is no help as they only provide support for windows or mac, and refuse any linux support queries. Dell and its ever shrinking Ubuntu line of laptops, doesnt seem to have any linux support for my card either. I was thinking perhaps an earlier version of Ubuntu might be better for my EU870D card? Anyway sry 4 rant :)

Dave

---

### Post by ddrichardson on 2009-03-04
OK - sorry to hear you have problems. I don't want to sideline this discussion into support for a single connection type but as you mention it works in Windows, is it one of these devices that has a small area of flash ram that contains its Windows driver?

I only ask because sometimes these are misidentified (kinda - it *is *a mass storage device) and the fact that its a modem is missed.  I had to create a udev rule for one a friend at work was using.

---

### Post by TrueTom on 2009-03-06
I don't know if that helps you, but with a clean install there are no VPN clients installed and the VPN tab in NM is completely grayed out without any indication how to change that...

---

### Post by ddrichardson on 2009-03-06
Someone mentioned this, I'm not sure which package is required to enable it.

Scratch that, its network-manager-vpnc

---

### Post by Dougie187 on 2009-03-07
> **ddrichardson said:**
> Someone mentioned this, I'm not sure which package is required to enable it.

Scratch that, its network-manager-vpnc

It could be network-manager-vpnc, or network-manager-openvpn, or network-manager-pptp. All of which are vpn's and would depend on the server you are trying to connect with. If the client that your vpn provider... provides... is a cisco client, you most likely will use the vpnc package. I don't know what you would use for the openvpn package, and I don't really think anyone would see an implemented pptp vpn in a professional environment.

I think VPN's are going to be a documentation nightmare, as there are so many different kinds, and each one needs a different setup. However, I have currently set up a connection using VPNC and I think it is incredibly straight forward (assuming you have the correct information for logging into your vpn). I have also in the past set up a PPTP vpn with my desktop, and that took some setup, mainly on the server side, but the client side was pretty straight forward as well. There is also the openVPN connection, which I have never had to mess with, so I can't give any insight on that. But if you would like some more clarification on the steps I used to setup the VPNC connection let me know. Also, I don't have any certificates or anything, this is a connection using a simple group password, group name, user name, and user password, along with the server name.

---

### Post by bennachie on 2009-03-11
Broadband dongles can be a nightmare in most flavours of Linux, but the most common problem arises from failure to identify that the device is, in fact, a modem. There are lots of fixes out there, some of which work. I had hoped that the next iteration of Network Manager would mark a significant step forward in dealing with these now ubiquitous devices.

At the moment, I am using Fedora 10 on my eeePC 4G, rather than Ubuntu. That's mainly because installation and operation turned out to be simple and trouble-free, with no need for the minor hacks and updates that were recommended for 8.10. However, the Network Manager package seems to be essentially the same in both distros. 

Wi-fi works brilliantly on my eeePC (better than my Windows laptop in many cases). Connections via ADSL are fine, too, and the modems I have tried have been configured using Firefox. When I'm in the sticks, out of 3G range, getting GPRS access through a variety of cellphones has also proved to be straightforward. Some broadband dongles work just fine out of the box (I could provide a list of the devices I have tried, but it would already be out-of-date), some can be persuaded to work after a bit of fiddling about, and some have turned out to be just too much trouble to be worth messing with. 

One key problem is the pace at which "new" devices are being introduced (sometimes with little apparent benefit in features or performance), and I have a good deal of sympathy with the Linux developers who are trying to keep up with these commercially-driven face-lifts.

---

### Post by ddrichardson on 2009-03-11
> **bennachie said:**
> Broadband dongles can be a nightmare in most flavours of Linux, but the most common problem arises from failure to identify that the device is, in fact, a modem. There are lots of fixes out there, some of which work. I had hoped that the next iteration of Network Manager would mark a significant step forward in dealing with these now ubiquitous devices.
In fairness to NM developers, this is a HAL issue - I know the 3 Mobile dongle I tried worked once I defined HAL rules for it.

I'm also surprised that Mobile Broadband companies in general aren't pushing better support when there is such a large netbook market that is so well suited to these devices.

---

### Post by tr333 on 2009-03-12
Last time I checked NM on Jaunty, it was not possible to connect to a PPTP VPN running on a Windows server, as NM lacks the option for "Refuse EAP".  It existed in Hardy NM but is not present in the Intrepid or Jaunty versions of NM.  [https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/301593](https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/301593)

This issue appears to have been fixed upstream in NM but afaik the fix has not yet made it into Jaunty.

---

