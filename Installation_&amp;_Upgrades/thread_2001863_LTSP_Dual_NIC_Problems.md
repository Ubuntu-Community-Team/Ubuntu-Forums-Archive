---
title: "LTSP Dual NIC Problems"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by wilman100 on 2012-06-11
Hi, I have a Ubuntu 10.04 LTS project underway. This is intended for a 30 user classroom and was built up some time ago at home.

The clients can log on to the server, however they all need Internet access and this is causing the problem because we have none and not sure how to make this work.

The client side consists of a connection between one of the  NIC's on the server and a switch with all the clients connected to that switch. This works fine and I see clients with 182.168.22.x addresses.

The available router is on another network which is accessible via a different switch to the one above The ip address of this other network is 192.168.1.0 with the router sitting at 192.168.1.100

I am at a loss as to how I should configure the various files for this installation.

The current /etc/network/interfaces file reads :-

auto lo
iface lo inet loopback

auto eth0
             iface eth0 inet static
             address 192.168.22.1
             netmask 255.255.255.0

auto eth1
iface eth1 inet dhcp

_____________________________________________________________

The /etc/ltsp/dhcpd.conf file reads

authoritative;

subnet 192.168.22.0 netmask 255.255.255.0 {
           range 192.168.22.20 192. 192.168.22.250;
           option domain-name "example.com";
           option domain-name-servers 192.168.22.1;
           option broadcast address 192.168.22.255;
           option routers 192.168.22.1;
           option subnet-mask 255.255.255.0;
           option root_path 2/opt/ltsp/i386";
           if substring( option vendor-class-identifier, 0, 9) = "PXEClient" {
                 filename "/opt/ltsp/i386/pxelinux.0"
            } else {
                 filename "/ltsp/i386/nbi.img";
             }
}
__________________________________________

I am sure that the  option routers line is wrong but I think that this is only part of it.

Can anyone help me particularly with the interfaces file.


Regards


Dave

---

### Post by forkandles on 2012-12-25
You have probably given up on this by now, but if not then try looking here:

[http://www.linuxquestions.org/questions/blog/beachboy2-315980/ltsp-setting-up-from-scratch-35204/](http://www.linuxquestions.org/questions/blog/beachboy2-315980/ltsp-setting-up-from-scratch-35204/)

---

