---
title: "Clean install of 12.04 eth0 not working"
date: 2012-05-05
forum: Installation &amp; Upgrades
---

### Post by jas251 on 2012-05-05
Hello all -

I just did a clean install of 12.04 (server not desktop) for a home based web dev platform.  "Out of the box" i cannot get any traffic in or out of eth0 (not even a ping).  "lo" works just fine.

Install try 1 resulted in me trying to manually reconfigure eth0, open ports and services in ufw, etc... only to result in no joy and a suspicion that I mucked it up worse on my own...  So, out of sheer "the Ubuntu gods are all powerful" I did another clean install and got back to "defaults".  Still no joy.  So, something in the default install configuration is blocking my eth0.

I can see packets coming in/out via ifconfig counts (below) so the physical and link layers are good.  The IPs are assigned.  I can ping/SSH on localhost so the app layers are good.  This keeps bringing be back to some unknown unknown at the firewall.

What am I missing?  Thanks

Here's the ifconfig:
--------------------------------------------------------

eth0   Link encap:Ethernet  HWaddr 00:17:31:c5:ce:56
       inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
       inet6 addr: fe80::217:31ff:fec5:ce56/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
       RX packets:2920 errors:0 dropped:0 overruns:0 frame:0
       TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:231585 (231.5 KB)  TX bytes:15489 (15.4 KB)
       Interrupt:21 Base address:0xde00
---------------------------------------------------------

---

### Post by dino99 on 2012-05-05
there are lot of issues with network-manager & resolvconf & dnsmasq right now

[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

myself have removed network-manager and installed wicd as a workaround till getting a new resolvconf package (the one from quantal seems have fixed this issue, so it should be backported very soon on precise)

[https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

note: starting the system, then unplugging the network cable and plugging it again a few seconds later, might help detection of the good settings.

---

### Post by darkod on 2012-05-05
Are you using DHCP?

Did you try a ping to an IP or only to a domain? If you try to ping 8.8.8.8 for example?

If ping to IP works, it sounds like DNS server issue. Should be easy to sort out.

If running static IP, make sure you have netmask and gateway configured too. If running dhcp that should be taken care by the dhcp server.

---

### Post by jas251 on 2012-05-05
I have tried both DHCP and static.
Currently running static.

/etc/network/interfaces:
---------------------------------
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
---------------------------------

The ping I've been trying is to 192.168.0.1 (my router) - and yes, I've pinged to it from other machines that are working just to do the dummy check.  Have also tried a few other local machines.  Ping to 192.168.0.100 (this machine's IP) works fine as does localhost.  Ping to 8.8.8.8 does not work (destination host unreachable).

Thanks for your brain cycles!

---

### Post by jas251 on 2012-05-05
Hi Dino99 -
Thanks for the thoughts.  Unfortunately I don't have network manager installed at all right now (server version).  Next idea?
Thanks

---

### Post by darkod on 2012-05-05
Is it possible by any chance that you have OUTPUT traffic blocked by the firewall?

See what iptables rules say:
sudo iptables -L -n -v

---

### Post by jas251 on 2012-05-05
Right now its the default post install policy...

sudo iptables -L -n -v:
----------------------------------------
Chain INPUT (policy ACCEPT 30 packets, 3139 bytes)
 pkts bytes target     prot opt in     out     source          destination

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source          destination

Chain OUTPUT (policy ACCEPT 7 packets, 766 bytes)
 pkts bytes target     prot opt in     out     source          destination
----------------------------------------

---

### Post by darkod on 2012-05-05
Hmmm, I'm puzzled.

Time to try another network cable?

---

### Post by epyon22 on 2012-05-30
Did you figure this out? I am having this same issue. It's very weird ifconfig only shows lo interface, though I can't ping 8.8.8.8. ip link shows a eth1 interface but ifup says "ignoring unknown interface eth1=eth1."

---

