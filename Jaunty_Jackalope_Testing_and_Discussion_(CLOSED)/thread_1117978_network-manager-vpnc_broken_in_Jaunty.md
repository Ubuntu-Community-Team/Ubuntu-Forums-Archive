---
title: "network-manager-vpnc broken in Jaunty?"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by loofi on 2009-04-06
Problem in Jaunty pr. 6.April: 
I am unable to receive any packages through the tunnel after successfully connection to my cisco pix. If I use the command line I am able to send and receive packets to my target networks. Also I have no problem in Hardy or Opensuse 11.1 with network-manager-vpnc.

There must be a bug in Jaunty or this version of network-manager-(vpnc). 
This post on Bugzilla for Fedora sums it up: 
[https://bugzilla.redhat.com/show_bug.cgi?id=479317#c20]("https://bugzilla.redhat.com/show_bug.cgi?id=479317#c20")

It seems that routing is in place but no traffic is received through tun0.
This bug should be fixed for people wanting to use jaunty for connecting to cisco based vpns.

Can anyone with access to Cisco Vpns confirm this behavior?

---

### Post by corep105 on 2009-04-07
I have the exact same problem. This is a big issue, since we are doing our best to push ubuntu as a corporate desktop. And vpn not working is a big issue. Besides that i love jaunty - big improvements in ui etc. Great stuff.

---

### Post by corep105 on 2009-04-12
did some more testing - it is working on my T60 laptop but not my T400. So problem must be NIC/driver in T400 i guess. But i have tried both wireless & cable & 3g modem and none of the options seem to work with vpnc.

---

### Post by corep105 on 2009-04-14
figured out the problem. I have dropped network manager for now. Had to do the following to make it work (assuming you have a vpn.conf file in current dir):

rm /etc/resolv.conf
ln -s /etc/resolvconf/run/resolv.conf /etc/resolv.conf
sudo vpnc --debug 1 ./vpn.conf

Apparently network manager gets it wrong when trying to setup connection. Changing resolv.conf to sym link and connecting to vpn as root works.

---

### Post by dro0g on 2009-04-14
I've had to go into NetworkManager and update a couple connections but vpnc has been working for me (just used it a few minutes ago and I have all updates applied as of today)

On the VPN tab I have NAT-T selected for the NAT Traversal method (On the PIX/ASA side Both TCP and UDP NAT Traversal are enabled)

Under the IPv4 tab, Method is set to Automatic(VPN) In the Routes button  "Use this connection only for resources on it's network" is checked. If it's not checked, things don't work right. I assume this is an attempt to make it more like Windows PPTP VPN where it defaults to sending all traffic through the tunnel.

I used to have an issue when I used Firestarter that I would have to disable the firewall when connecting to VPNs because it wouldn't pass the traffic.

---

### Post by loofi on 2009-04-14
Strange. On my laptop (hp 8530w) this works, but in my Vmware Workstation guest it does not. I can live with this. Especially now that it works on my brand new laptop.

I am not seeing any bugreport for ubuntu on this issue so I presume that its not affecting everyone. Let me know if things work out with NM on your T400 corep105.

---

### Post by bradb21 on 2009-04-16
My VPNC connection to my office had been working, I was out of town all last week and today I did a system update to get the most recent packages and now my VPNC connection doesn't work anymore. I get connected, I don't get the connection disclaimer message I've always gotten, not it's just "...." It appears I'm connected, but I can't get to anything across the VPN. I didn't change any of my configs I just updated to newer pkgs and now it doesn't work. Bummer!

---

