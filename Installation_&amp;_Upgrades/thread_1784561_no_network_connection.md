---
title: "no network connection"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by Clive Richardson on 2011-06-17
Have just finished installing ubuntu 10.04.1 but am unable to establish a network connection. I have made sure it is 'enabled' and have tried rebooting. I would be very grateful for any help.
 Having seen other threads I have prepared the following information as each computer seems to have its individual problems:
desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:09.0 USB Controller: NEC Corporation USB (rev 41)
00:09.1 USB Controller: NEC Corporation USB (rev 41)
00:09.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:0c.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice Modem (rev 08)
00:0d.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
00:0e.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 07)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS
desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 00
       serial: 00:02:e3:24:51:b5
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=64 link=no maxlatency=52 mingnt=11 multicast=yes port=twisted pair speed=10MB/s
       resources: irq:5 ioport:d000(size=256) memory:dfffc000-dfffcfff memory:dffd0000-dffdffff(prefetchable)

desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:e3:24:51:b5  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:864 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66968 (66.9 KB)  TX bytes:66968 (66.9 KB)
Many thanks.

---

