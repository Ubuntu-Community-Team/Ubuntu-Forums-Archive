---
title: "advice requested - ubuntu server or workstation best for home network?"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by Bert Berlin on 2008-05-12
I need some advice - I currently host a home network using CentOS 4.5.  The CentOS workstation is a pppoe client for my connection to DSL, provides dhcp and dns services to my network, and samba services for file and printer sharing.  It also provides firewalling on the pppoe link.  However, with the addition of some recent software, it has started to become unstable, and I would like to switch to Ubuntu.  I have one Ubuntu workstation on the network, and one Kubuntu, two Windoze workstations, and guest privileges via a wireless base unit.

My question is - should I upgrade the CentOS to ubuntu workstation or ubuntu server?  Will I be able to provide the same services with Ubuntu workstation (samba, dns, dhcp, file and print sharing, pppoe client, and firewall for the network)?  I am inclined towards Ubuntu WS rather than server as I wish to be able to use some of the available toys, and I understand that Ubuntu server has no widowing system - it is command-line based.

Any experiences or thoughts anyone wishes to share will be welcome.

Bert

---

### Post by Mr A Mouse on 2008-05-12
All of the services you are asking about (samba, dns, dhcp, file and print sharing, pppoe, and firewall) are available in both Server and Workstation variants. 

Disclosure: I have never successfully gotten my samba service to talk nicely to my Windows computers, though I'm 99% confident that the fault lies with the system administrator, not with the system itself. ;)

---

### Post by Bert Berlin on 2008-05-12
As an aside - you are right - samba can work quite nicely: but it may require a bit of fiddling and reading.  If you use SWAT to manage samba, there are very extensive help pages for every line of every page of the configuration dialog.  It is pretty widely used on Linux servers to provide file sharing services for windoze workstations.

b

---

