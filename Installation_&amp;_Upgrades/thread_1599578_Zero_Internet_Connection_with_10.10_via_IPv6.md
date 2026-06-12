---
title: "Zero Internet Connection with 10.10 via IPv6"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by drdos2006 on 2010-10-17
Luckily I have a second machine running 9.10 and could get onto the net for assistance.

I tried all sorts of modifications to sysctl, modeprobe files, etc and checked all over google for a fix. 

It appears that the IPv6 settings are part of the kernel, in this case I am going back to 9.10 and staying with 9.10 until this IPv6 is sorted out. Most home routers do not have IPv6 connections, only IPv4. This lack of Internet connection has happened with both server and desktop. I do not know the reasoning behind this decision but I will not be upgrading to 10 until IPv6 is sorted for me as a home user.

Able to boot with different partitions of a 320 GB hard drive with Windows Server 2008, Ubuntu server 9.10 plus Ubuntu desktop 9.10 but IPv6 with 10.10 installs on the respective server and desktop partitions does not allow a lan connection to the router. All are 64bit downloads. Big thumbs down from me.

ASUS motherboard, Core 2 Duo CPU 2.9 GHz, 2 GB RAM
regards

---

### Post by Yarui on 2010-10-18
Just curious, but do you have a very compelling reason to be using IPv6 to begin with?  I know this isn't really answering your question at all, but if you can get by with IPv4 I don't see why you should be so worried about IPv6.

I can understand if you are doing this as a sort of experiment to try to understand IPv6 better or something to that effect, but I have always been under the impression that IPv6 isn't really at all necessary at this point in time and trying to deal with it right now is just asking for a headache, since it is not well supported.

I could be totally wrong in all of this, though, so feel free to enlighten me.

---

### Post by Soul-Sing on 2010-10-18
As expected Europe is running out of IP addresses within one year on. To avoid problems ipv6 is an entirely new protocol developed to create an infinite number of IP addresses: IPv6. This allows far into the future, new devices, computer to connected to the Internet.
But....not all devices (routers/modems/firewalls) are "ipv6 ready" out of the box, which is a huge concern/problem for many providers and clients.

---

### Post by coffeecat on 2010-10-18
> **drdos2006 said:**
> It appears that the IPv6 settings are part of the kernel, in this case I am going back to 9.10 and staying with 9.10 until this IPv6 is sorted out. Most home routers do not have IPv6 connections, only IPv4. This lack of Internet connection has happened with both server and desktop. I do not know the reasoning behind this decision but I will not be upgrading to 10 until IPv6 is sorted for me as a home user.


IPv6 settings have been part of the Linux kernel - as you put it - for years. IPv6 was enabled by default in Karmic as well. In fact it was enabled way back in Breezy/Dapper times. Ipv6 is also enabled by default in Windows Vista and 7 as well as in the last three or so iterations of MacOS X. So any home router that has firmware that can't cope with this is either very old or junk.

---

### Post by drdos2006 on 2010-10-18
Yarui

It may be that Australian ISPs do not use IPv6 but 10.10 did not work for me. Could not connect to Internet for installation.

regards

---

### Post by drdos2006 on 2010-10-19
An update.
Tried Fedora 13 on Ubuntu 9.10 with Virtualbox, not a problem connecting to the Internet behind a bridged network connection. 
So I installed Ubuntu 10.10 64bit in Virtualbox and Internet connection behind a bridged network connection was not a problem.
This was on my primary machine with Pentium(R) Dual-Core CPU E6850 @ 3.00GHz, 2 cores and 4GB RAM Gigabyte Motherboard.

The secondary machine that Ubuntu 10.10 ( both 32 bit and 64 bit, both server and desktop ) would not connect to Internet was an ASUS P5G motherboard with Pentium(R) Dual-Core CPU E6500 @ 2.93GHz, 2 cores and 2 GB RAM. 
I had installed a second NIC (Netgear 8189) but still problem with IPv6. Motherboard is about 6 months old. 
Looks like it is a hardware issue.
Will keep you all updated.

regards

---

### Post by drdos2006 on 2010-11-01
I re-installed server 10.10 with a PCI Network Interface Card and de-selected the gigabyte on-board NIC in the BIOS. The gigabyte NIC would only ever [try to] connect through IPv6 and the 100Megabit card used IPv4.

regards

---

