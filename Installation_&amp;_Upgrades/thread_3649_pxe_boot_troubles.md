---
title: "pxe boot troubles"
date: 2004-11-08
forum: Installation &amp; Upgrades
---

### Post by bioborg on 2004-11-08
so, after an arduous endeavor, I booted off of pxe
now, I am having trouble setting up the mirror...
it doesn't like any mirror I give it, saying it cannot find releases file, 
even when i direct installer to directory the releases file is in.
Could I mirror a CdROM on my pc and use it?
why can't I get past the <select a mirror> step?
I would be happy to post any conf files that seemed useful to figuring out the problem.

---

### Post by bioborg on 2004-11-08
OK, so my issue is my client can resolve dns (it knows the numeric value of archive.ubuntu.org) but it finds No Route to Host when looking for the Releases file.

Here is my dhcpd.conf:

# Sample /etc/dhcpd.conf
# (add your comments here)
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1;
option domain-name "something.org";

subnet 192.168.1.0 netmask 255.255.255.0 {
   range 192.168.1.10 192.168.1.100;
}

 host pxeinstall {
    hardware ethernet 00:00:39:9f:03:21;
    fixed-address 192.168.1.90;
    filename "pxelinux.0";
}

now, i put the domain-name in the linksys gateway, and in this file...
I actually use gandi to resolve my dns...
but that is all kinda irrelevant, isn't it?  Should I put some real DNS in there, like the one from my ISP or the nameserver that points to my IP

when I open up a terminal when the client error messages, I cannot wget...

---

### Post by Cyberfreak on 2005-02-18
hi,
I have exactely the same pb...
installer works fine until it tries to download stuffs from a miror.
I tryed to set a ftp server on my network, but it doesn't work...
It seems that ubuntu installer can't acced the network when using pxe to boot... is it possible?

I have a ibm X21 with a 3com mini pi network card.

---

