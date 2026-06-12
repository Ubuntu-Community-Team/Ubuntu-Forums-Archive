---
title: "Fresh Install No Connectivity"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by MD5SUM on 2010-10-21
I just installed Ubuntu 10.10 i86 Desktop on a separate partition via Wubi Installer.  The installation process went fine and there were no issues with one exception.  Once I hit the desktop I noticed that Ubuntu was not recognizing my windows network.  Since I have installed previous versions of Linux on my computer I know that it always auto connects to my network. 

matt@ubuntu:~$ sudo ifconfig -a

eth0    

Link encap:Ethernet HWaddr 00:22:15:a1:cd:ac
        UP BROADCAST MULTICAST MTU:1500 Metric:1
        RX packets:0 errors:0 dropped:0 overruns:0 frame:0
        TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000
        RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
        Interrupt:23 Base address:0xe000

lo

      Link encap:Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:100 errors:0 dropped:0 overruns:0 frame:0
        TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:7616 (7.6 KB) TX bytes:7616 (7.6 KB)


Since there is a hardware address for eth0 I can assume that Ubuntu sees my NIC, and I know my NIC works fine so I guess there must have been an error during the install.  So I ran Dmesg and grepped for eth and found this:


matt@ubuntu:~$ dmesg | grep eth

[ 0.984882] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.

[ 0.985118] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23

[ 0.985122] forcedeth 0000:00:14.0: setting latency timer to 64

[ 1.496603] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x1374 @ 1, addr 00:22:15:a1:cd:ac

[ 1.496605] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3

[ 11.400610] eth0: no link during initialization.

[ 11.401135] ADDRCONF(NETDEV_UP): eth0: link is not ready

 

So I see that there was a problem linking during initialization but honestly I don't know how to go about fixing it.  When I went to my etc directory and looked in the network folder and catted the interface file all that was in there was:

matt@ubuntu:/etc/network$ cat interfaces

auto lo

iface lo inet loopback

 

I also tried to manually configure eth0 then use ifup and ifdown but since the OS doesn't recognize eth0 I get an error message.

 If anyone has any suggestions or has had this problem before I would love some input.

---

