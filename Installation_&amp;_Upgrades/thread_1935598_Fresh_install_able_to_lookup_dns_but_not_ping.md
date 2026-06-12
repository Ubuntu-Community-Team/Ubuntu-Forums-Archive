---
title: "Fresh install able to lookup dns but not ping"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by misterbk on 2012-03-04
Hi,

I have a fresh install of kubuntu 11.10 here.  For the past couple hours, it has been able to resolve DNS but cannot ping anything past the NAT gateway.

This is everything I did, in order:

Installed Kubuntu amd64.
Successfully could use internet.
Used internet to install samba. (apt-get install samba)

Edited /etc/samba/smb.conf to let myself connect to a share. Works. (even right now.)

Set an IP reservation in my router so that the machine would be on .2 instead of .125, which is the address it initially got.

Bounced eth0 (ifconfig eth0 down; ifconfig eth0 up) to get the new address. (because dhclient apparently no longer works.)

Verified the new IP address in the router, and via ifconfig.

Used internet to install openssh-server  (apt-get install openssh-server)

Edited /etc/ssh/sshd_config to add this line, which solves long timeout issues when logging in via ssh:

(/etc/ssh/sshd_config):
UseDNS no

Attempted to use Muon to install krfb.  <-- **at this point I notice that I cannot ping anything, but can resolve DNS.**


I can do this:
$ nslookup google.com
Server:         10.11.12.1
Address:        10.11.12.1#53

Non-authoritative answer:
Name:   google.com
Address: 74.125.239.2
Name:   google.com
Address: 74.125.239.3
Name:   google.com
Address: 74.125.239.4
Name:   google.com
Address: 74.125.239.5
Name:   google.com
Address: 74.125.239.6
Name:   google.com
Address: 74.125.239.7
Name:   google.com
Address: 74.125.239.8
Name:   google.com
Address: 74.125.239.9
Name:   google.com
Address: 74.125.239.14
Name:   google.com
Address: 74.125.239.0
Name:   google.com
Address: 74.125.239.1


But I cannot do this:

**$ ping google.com**
PING google.com (74.125.239.1) 56(84) bytes of data.
^C
--- google.com ping statistics ---
30 packets transmitted, 0 received, 100% packet loss, time 29232ms

**$ ping 74.125.239.2**
PING 74.125.239.2 (74.125.239.2) 56(84) bytes of data.
^C
--- 74.125.239.2 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 5999ms


I can't find anywhere in the GUI to do a dhcp release / renew, but I've done these other troubleshooting steps:

* Unplugged / replugged ethernet
* Rebooted the Kubuntu machine
* Bounced eth0 again (ifconfig down / up)

I'm on a Windows box across the room, connecting via the same router.

While Kubuntu cannot ping anything or use the internet in any way (except for resolving DNS just fine):
* I can still connect to Kubuntu fine via SSH
* I can still connect to Kubuntu fine via Samba

(In fact the nslookup command is run via a putty session to the box from my windows machine.)

Any ideas what might be going on here?

---

### Post by misterbk on 2012-03-04
Disregard - Not a problem with Kubuntu install.


For any network geeks who want to know what happened:

I was replacing a previous system with a new one, and wanted to keep it on the same address.  There was a stale MAC/IP binding from the old system, because my router is bad at removing bits from one section when you make changes to another section.  For some reason there was a delay between obtaining the new address and the router blocking packets due to the binding violation.

My router is a Netgear ProSafe, and has two sections:

1: DHCP clients and reservation assignments (in Network Configuration -> LAN Settings -> LAN Groups)

2: IP/MAC bindings (in Security -> Address Filter -> IP/MAC Binding)

It's bad about leaving stale IP/MAC bindings around after you've reserved an IP address in DHCP reservations.

(Yeah, don't buy pro routers unless you really like learning about networking.  :)  )

---

