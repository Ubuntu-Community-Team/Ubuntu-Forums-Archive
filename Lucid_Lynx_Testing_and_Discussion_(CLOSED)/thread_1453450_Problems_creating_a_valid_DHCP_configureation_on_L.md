---
title: "Problems creating a valid DHCP configureation on Lucid Server x86 (Beta 2)"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by RecursiveDream on 2010-04-13
I'm trying to set up dhcpd server on a machine getting an ip from another nic using dhcp client. My Linux Admin guide gave me an example for dhcpd.conf, which I have customized a little bit.

The confusing part is the guide tells me, "The dhcpd.conf file contains a dummy entry for the external interface (required)..." I tried to leave it out, because it looks like it is assuming too much if I am getting my ip from a dhcp server on the external net. Leaving it out causes dhcpd to complain that I haven't set up the external nic.

Here is what the guide suggested:
```
# dhcpd.conf
#
# global options
option domain-name "synack.net";
option domain-name-servers gw.synack.net;
option subnet-mask 255.255.255.0;
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.51 192.168.1.60;
  option broadcast-address 192.168.1.255;
  option routers gw.synack.net;
}

subnet 209.180.25.1.0 netmask 255.255.255.0 {
}

```Here is what I tried to use:
```
# dhcpd.conf
#
# global options
option subnet-mask 255.255.255.0;
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.51 192.168.1.60;
  option broadcast-address 192.168.1.255;
  option routers 192.168.1.1;
}
```The reason I tried to leave out the "dummy" subnet line, is because I wasn't sure if I could be sure of what my subnet would be if I am getting my lease from my ISP.

If I do put it in, does it matter exactly what it says? I don't know if the subnet is /24 or what. Also, this "dummy" line doesn't appear in the [wiki]("https://help.ubuntu.com/9.10/serverguide/C/dhcp.html"), or the [mini dhcp howto]("http://www.tldp.org/HOWTO/DHCP/index.html") linked from there either. Why not?

---

### Post by Iowan on 2010-04-13
I had DHCP3 on my Breezy server, but don't remember a dummy entry for external interface (partly because my server had/has only one interface). Unless you're serving DHCP address on the external interface, I'm not sure why the DHCP server cares about it all. My current (Hardy) server uses DNSMasq, so my memory is a li'l rusty about the old configuration.

---

### Post by RecursiveDream on 2010-04-14
> **Iowan said:**
> My current (Hardy) server uses DNSMasq, so my memory is a li'l rusty about the old configuration.

Hmm... I have used dnsmasq on the same machine as my browser for the interwebs, but I didn't know it was also a lightweight dhcp server. Thanks, I'll be sure to check it out!

---

### Post by Iowan on 2010-04-14
:confused: I presume it's a "similarly" named program - I can't imagine DNSMasq as a browser, (but I've been wrong before)...

---

### Post by RecursiveDream on 2010-04-14
Erm, no sorry, I meant I had set it up to do dns caching to make surfing the interwebs faster.

Thinks are looking up for the moment. I more or less followed the wiki guide to set up dnsmasq and it looks like I'm getting there. However, I ran into a few hitches.

Here is my configuration:

```
     ___--------___
    {              }
{ Interwebs (cable modem) }      <===>      [ Ubuntu Server ]      <===>      [ Ubuntu Desktop ] 
    {___        ___}
        --------
```In Ubuntu Server's /etc/network/interfaces, I have:
```
# The primary interface (WAN)
auto eth1
iface eth1 inet dhcp
# The LAN interface
auto eth0
iface eth0 inet static
  address 192.168.0.1
  netmask 255.255.255.0
  broadcast 192.168.0.255
```(I didn't add a "gateway" line; AFAIK eth0 doesn't need it if the server IS the gateway, right?)

1) The wiki article says to put 127.0.0.1 (localhost) at the top of /etc/resolv.conf -- I did this, but after a "/etc/init.d/networking restart" it was overwritten :)
My server is getting a dhcp lease from my isp on eth1.

2) On the client (Ub. Desk.) I am getting a dhcp lease with a correct address from the range I specified in /etc/dnsmasq.conf on the server -- however, dns isn't working yet.

I will try and get the exact dnsmasq.conf file from the server and post it, but I can't log in with ssh yet. (On Ubuntu < Lucid I used to set a different port, protocol 2, enable password auth, and disable root login, and I was good to go. Now the config file format is changed; I may have borked it but it seems making the same changes doesn't result in the same configuration.)

Anyhoo, any wisdom from the Linux sages would be more than welcome!

---

### Post by RecursiveDream on 2010-04-15
Update:

```
# dnsmasq conf :P

# Don't provide dhcp for the public interface :)
except-interface=eth1

# DHCP for the layman :)
dhcp-range=192.168.0.30,192.168.0.50,255.255.255.0
```I rebooted, and turned off the firewall. Ubuntu server gets the dhcp lease from the isp, and I can ping the Google. Interwebs, at last!

However, my Ubuntu-Desktop client is now getting not just an ip, but correct dns gibblets, while I guess my packets aren't getting correctly routed yet? Here is ping's behaviour now:
```
$ ping -c 1 www.google.ca
PING www.l.google.com (66.249.90.104) 56(84) bytes of data.

--- www.l.google.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms
```Can someone help me with this? I would also appreciate a comment on minimum ports that would need to be allowed for dns/whatever.

---

