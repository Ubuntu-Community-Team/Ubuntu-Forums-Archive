---
title: "Upgrade nightmare with ISC-DHCP"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by drifting on 2011-08-16
Hi Guys.

Wonder if anyone can help, this is driving me absolutely nuts. I have a perfect working system on 10.4 LTS. But due to having to upgrade to to 11.4 due to a none working firmware tv sat card. I have been left with an absolute mess. Much of which is of my doing :-|

Problem:- DHCP, it used to work well, now with this upgrade webmin failed to allow me to configure it, and along the way I got so fed up with contradictory information on configuration. So even the adventurous type I listened to someone on here suggesting DNSMASQ. So removed all the previous DHCP files (Good riddance)  and installed DNSMASQ and kept getting this :-
"failed to bind DHCP server socket: Address already in use" which is total rubbish. So can only assume yours truly has mad yet another config error?

 domain=than				
dhcp-range=10.0.0.30,10.0.0.50,12h	
dhcp-option=option:router,10.0.0.1
dhcp-option=option:ntp-server,10.0.0.1
dhcp-authoritative
# Server DNS settings... this is required as the server itself will
# Server DNS settings... this is required as the server itself will
# not be obtaining it's IP address via DHCP and therefore would 
# not be automatically added to the DNS records for forward/reverse
# DNS queries as required by Kerberos
ptr-record=2.0.0.10.in-addr.arpa.,"vs.than" address=/vs.than /10.0.0.1 
 
# Kerberos and LDAP automatic stuff...
# This maps kerberos.than and
# ldap.than to the server and also makes all
# dhcp clients aware of the kerberos realm... magic :D
address=/kerberos.than/10.0.0.1 
address=/ldap.than/10.0.0.1 
 
txt-record=_kerberos.thanet,"THAN"
srv-host=_kerberos._udp.than,"kerberos.thannet",88
srv-host=_kerberos._tcp.than,"kerberos.thannet",88
srv-host=_kerberos-master._udp.than,kerberos."than",88
srv-host=_kerberos-adm._tcp.than,"kerberos.than",749
srv-host=_kpasswd._udp.than,"kerberos.than",464
srv-host=_ldap._tcp.than,ldap.than,389

Now I am stuck, so any help would be most welcome. And before you ask there are no other DHCP servers running on this server. 

Was considering ebox, until I found out that only supports 10.4, and the working version of DHCP (Snide remark)

Cheers

Paul

---

### Post by ppvolto on 2011-12-25
Hi drifting,
first i have the same Problem with a Bintec Router acting as WLAN AP,
the next thing is at the 16.12.2011 have i made a Upgrade at the Client Site (All Ubuntu Clients) and after this update with the Packages below the Problem Appears. I have changed today the Versions to the previous and hope thats it's. Other Programs communicating with the DHCP-Server are possible.

The Packages are
       isc-dhcp-client:amd64 (4.1.1-P1-17ubuntu10, 4.1.1-P1-17ubuntu10.1)
       isc-dhcp-common:amd64 (4.1.1-P1-17ubuntu10, 4.1.1-P1-17ubuntu10.1) //Only documentation?

I have searched for a new Version is aviable at [https://www.isc.org/software/dhcp](https://www.isc.org/software/dhcp) but i have no idea how to best update *Bintec use my uncle* 

Sorry for my poor English.

---

