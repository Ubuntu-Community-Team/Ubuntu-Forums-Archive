---
title: "broadcom or not broadcom"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by martinshort on 2009-12-25
just installed ubuntu on a new hp mini. it works kinda ok but it cant seem to get the wireless card working. digging a bit i found:

*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff

and:

01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 1507
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

and:
 modprobe -l | grep ssb
kernel/drivers/ssb/ssb.ko

then:

$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.


and then in the dmesg i found this:

[    8.506570] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    8.549158] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision

never seen a driver with such a long name before. 

2 questions: which one is the funny part? and where can i get the driver for this card?
 i mean broadcom is quite a household name in this business...

thanks..

---

### Post by martinshort on 2009-12-25
ok. i looked around. 
one question: how is it possible that a popular distribution as ubuntu does not have a native driver for the broadcom cards? 
it appears there are only 4 chips from the bcm43 family that need to be supported and this has been going on for a while. almost a year and a half now?!

check this post out. it has 21 pages. 
[http://ubuntuforums.org/showthread.php?t=896713&page=21](http://ubuntuforums.org/showthread.php?t=896713&page=21)

---

### Post by sakthidaran on 2009-12-25
Can you some more detail on your computer? Just saying HP Mini does not make clear.

If it is a desktop or laptop, then go to 
[http://ubuntuforums.org/showthread.php?p=8410902](http://ubuntuforums.org/showthread.php?p=8410902)
You will find, a similar problem where people have situation as if "No wireless in 9.10 with Broadcom BCM4312". Try the procedure given in post #27 or #28. I have found them working.

---

### Post by mikewhatever on 2009-12-25
That is a known issue, but easily solved.

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)
[http://ubuntuforums.org/showpost.php?p=8090292&postcount=1](http://ubuntuforums.org/showpost.php?p=8090292&postcount=1)

---

### Post by martinshort on 2009-12-26
ok. i solved it but it was here:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
and the readme file on the bottom.

the only thing now is that even though i put ssb in the /etc/modprobe.d/blacklist.conf it still loads on restart and the wl.ko is not loaded.

i'll read some more. i guess there is rc.d somewhere...

---

### Post by martinshort on 2009-12-26
something is not going very smooth..

i have ubuntu doing a ping to a remote server i have. drops like crazy. i have another machine with bsd next to it and that one is smooth - no drops to he same machine and faster runarounds. they both go through the same access point...

so what gives?

---

### Post by martinshort on 2009-12-27
hi again... i rebuild and reinstalled the driver from the broadcom site. still there are all these dropouts. 

here is a ping to the access point. i have 2 other bsd machines here pinging the same point at the same time as this one. no dropouts there. can somebody explain this:
....................................................
64 bytes from 192.168.1.1: icmp_seq=123 ttl=150 time=4.73 ms
64 bytes from 192.168.1.1: icmp_seq=124 ttl=150 time=211 ms
64 bytes from 192.168.1.1: icmp_seq=125 ttl=150 time=2.59 ms
64 bytes from 192.168.1.1: icmp_seq=126 ttl=150 time=4.12 ms
64 bytes from 192.168.1.1: icmp_seq=129 ttl=150 time=3.38 ms
64 bytes from 192.168.1.1: icmp_seq=130 ttl=150 time=94.9 ms
64 bytes from 192.168.1.1: icmp_seq=131 ttl=150 time=65.3 ms
64 bytes from 192.168.1.1: icmp_seq=132 ttl=150 time=4.49 ms
64 bytes from 192.168.1.1: icmp_seq=133 ttl=150 time=5.00 ms
64 bytes from 192.168.1.1: icmp_seq=134 ttl=150 time=4.69 ms
64 bytes from 192.168.1.1: icmp_seq=135 ttl=150 time=4.64 ms
64 bytes from 192.168.1.1: icmp_seq=136 ttl=150 time=6.15 ms
64 bytes from 192.168.1.1: icmp_seq=137 ttl=150 time=2.79 ms
64 bytes from 192.168.1.1: icmp_seq=138 ttl=150 time=6.54 ms
64 bytes from 192.168.1.1: icmp_seq=140 ttl=150 time=5.49 ms
64 bytes from 192.168.1.1: icmp_seq=141 ttl=150 time=4.60 ms
64 bytes from 192.168.1.1: icmp_seq=143 ttl=150 time=4.76 ms
64 bytes from 192.168.1.1: icmp_seq=144 ttl=150 time=5.99 ms
64 bytes from 192.168.1.1: icmp_seq=145 ttl=150 time=7.01 ms
64 bytes from 192.168.1.1: icmp_seq=148 ttl=150 time=3.63 ms
64 bytes from 192.168.1.1: icmp_seq=149 ttl=150 time=3.72 ms
64 bytes from 192.168.1.1: icmp_seq=152 ttl=150 time=12.1 ms
64 bytes from 192.168.1.1: icmp_seq=153 ttl=150 time=3.74 ms
64 bytes from 192.168.1.1: icmp_seq=155 ttl=150 time=43.4 ms
64 bytes from 192.168.1.1: icmp_seq=156 ttl=150 time=6.85 ms
64 bytes from 192.168.1.1: icmp_seq=157 ttl=150 time=4.09 ms

--- 192.168.1.1 ping statistics ---
157 packets transmitted, 111 received, 29% packet loss, time 156362ms
rtt min/avg/max/mdev = 2.008/14.514/211.636/34.038 ms

---

### Post by phillw on 2009-12-27
On a scale of 1 to 10 of releasing driver information that the linux community can use, Broadcom come in at about minus 10.

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Should have an answer to your particular chip-set.  Don't blame Linux, blame the company - If you pay for the hardware - you want it to work !!!

Regards,

Phill.

---

