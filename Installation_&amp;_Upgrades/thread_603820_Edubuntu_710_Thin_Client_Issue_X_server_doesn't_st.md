---
title: "Edubuntu 7:10 Thin Client Issue X server doesn't start"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by donaldd on 2007-11-05
Hello All,
I have been trying to create a thin client environment at home by installing Edubuntu 7:10 on a pc which has plenty of disc space and memory.
I used my HP centrino laptop which boots into PXE as a thin client but it couldn't obtain an ip address.
After talking to my friend google found out that my router's dhcp was probably interfering with the one setup in Edubutu so I changed the server to a static ip address 192.168.5.254

/etc/ltsp/dhcpd.conf 
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.5.0 netmask 255.255.255.0 {
    range 192.168.5.201 192.168.5.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.5.1;
    option broadcast-address 192.168.5.255;
    option routers 192.168.5.1;
#    next-server 192.168.0.254;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}


I can now obtain an ip address and greeted by Edubuntu's splash screen but after a few minutes I am not logged into x windows but drop down to busybox initramfs.

Appreciate if somewhere could point me in the right direction as I am not sure what the problem is or where to look to find out.

---

### Post by SpiritIsReality on 2007-11-08
howdy
Do you have two nic cards in the server?
It looks like your router, the server, and the client are all on 192.168.5.0 network. 
Can you shut off the router dhcp or are there other computers on the network
who need a dhcp from the router? I think there is still 2 dhcp servers fighting over your laptop. I had that scenario and the ltsp servers dhcp usually lost.
It sounds like there is some configuration needed in the x served to the client.
please see this example and see if there is any help there.
[http://ubuntuforums.org/showthread.php?t=599166](http://ubuntuforums.org/showthread.php?t=599166) 
If you are just using one nic card in the server, then there's some eth0:0
configuring needed. [https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

