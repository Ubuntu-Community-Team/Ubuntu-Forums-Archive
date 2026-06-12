---
title: "Sharing my wifi-connection"
date: 2010-02-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by revoltism on 2010-02-24
I am trying to connect my N900 to my computer through my motherboard wifi. It seams like it is found but not connected. I do not know what i am doing wrong. I get connection on my wired connection but not the wireless. I am a noob and maybe have missed some network configuration?

```
daniel@revoltism:~$ sudo dhclient wlan0 
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:15:af:03:59:15
Sending on   LPF/wlan0/00:15:af:03:59:15
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
``````
daniel@revoltism:~$ sudo iwconfig wlan0 
wlan0     IEEE 802.11bg  ESSID:"Brute"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:3AA0-34A6-2619-2E4B-5E4E-EBAC-7DF4-05CA-FD50-322E-3666-DA03-FD50-322E-3666-DA03
          Power Management:off
``````
daniel@revoltism:~$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:17:31:ee:db:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:17:31:ee:d2:22  
          inet addr:85.226.48.234  Bcast:85.226.51.255  Mask:255.255.252.0
          inet6 addr: fe80::217:31ff:feee:d222/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3335631 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1399233 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:255787475 (255.7 MB)  TX bytes:98501869 (98.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2985 (2.9 KB)  TX bytes:2985 (2.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:03:59:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
``````
daniel@revoltism:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 20
       serial: 00:17:31:ee:db:4f
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:ff8fc000-ff8fffff ioport:b800(size=256) memory:ff8c0000-ff8dffff(prefetchable)
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 20
       serial: 00:17:31:ee:d2:22
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=85.226.48.234 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:ff7fc000-ff7fffff ioport:a800(size=256) memory:ff7c0000-ff7dffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:03:59:15
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

``````
daniel@revoltism:~$ sudo lshw -businfo
Bus info          Device       Class       Description
======================================================
                               system      P5W DH Deluxe
                               bus         P5W DH Deluxe
                               memory      64KiB BIOS
cpu@0                          processor   Intel(R) Core(TM)2 CPU          6700 
                               memory      32KiB L1 cache
                               memory      4MiB L2 cache
                               processor   Logical CPU
                               processor   Logical CPU
                               memory      2GiB System Memory
                               memory      1GiB DIMM SDRAM Synchronous
                               memory      1GiB DIMM SDRAM Synchronous
                               memory      DIMM [empty]
                               memory      DIMM [empty]
cpu@1                          processor   
                               processor   Logical CPU
                               processor   Logical CPU
pci@0000:00:00.0               bridge      82975X Memory Controller Hub
pci@0000:00:01.0               bridge      82975X PCI Express Root Port
pci@0000:05:00.0               display     R580 [Radeon X1900]
pci@0000:05:00.1               display     ATI Technologies Inc
pci@0000:00:1b.0               multimedia  82801G (ICH7 Family) High Definition 
pci@0000:00:1c.0               bridge      82801G (ICH7 Family) PCI Express Port
pci@0000:00:1c.3               bridge      82801G (ICH7 Family) PCI Express Port
pci@0000:03:00.0  eth0         network     88E8053 PCI-E Gigabit Ethernet Contro
pci@0000:00:1c.4               bridge      82801GR/GH/GHM (ICH7 Family) PCI Expr
pci@0000:02:00.0  eth1         network     88E8053 PCI-E Gigabit Ethernet Contro
pci@0000:00:1d.0               bus         82801G (ICH7 Family) USB UHCI Control
pci@0000:00:1d.1               bus         82801G (ICH7 Family) USB UHCI Control
pci@0000:00:1d.2               bus         82801G (ICH7 Family) USB UHCI Control
pci@0000:00:1d.3               bus         82801G (ICH7 Family) USB UHCI Control
pci@0000:00:1d.7               bus         82801G (ICH7 Family) USB2 EHCI Contro
pci@0000:00:1e.0               bridge      82801 PCI Bridge
pci@0000:01:03.0               bus         TSB43AB22/A IEEE-1394a-2000 Controlle
pci@0000:00:1f.0               bridge      82801GB/GR (ICH7 Family) LPC Interfac
pci@0000:00:1f.1  scsi0        storage     82801G (ICH7 Family) IDE Controller
scsi@0:0.0.0      /dev/cdrom1  disk        DVD reader
scsi@0:0.1.0      /dev/cdrom   disk        DVD_RW ND-3520A
pci@0000:00:1f.2  scsi2        storage     82801GB/GR/GH (ICH7 Family) SATA IDE 
scsi@2:0.0.0      /dev/sda     disk        200GB WDC WD2000JD-00G
scsi@2:0.0.0,1    /dev/sda1    volume      8181MiB EXT4 volume
scsi@2:0.0.0,3    /dev/sda3    volume      178GiB Extended partition
                  /dev/sda5    volume      176GiB Linux filesystem partition
                  /dev/sda6    volume      1600MiB Linux swap / Solaris partitio
pci@0000:00:1f.3               bus         82801G (ICH7 Family) SMBus Controller
                  wlan0        network     Wireless interface
```

---

### Post by revoltism on 2010-02-25
bump

---

### Post by gordintoronto on 2010-02-25
What's an N900?

---

### Post by revoltism on 2010-02-26
> **gordintoronto said:**
> What's an N900?

It is a mobile telephone running on debian linux. Pretty much the most powerful mobile out there.

---

### Post by gordintoronto on 2010-02-26
From: [http://www.esrun.co.uk/blog/ubuntu-gateway-access-point-server/](http://www.esrun.co.uk/blog/ubuntu-gateway-access-point-server/)

"Configure wireless card to setup access point

Again we&#8217;re going to open a terminal and edit our /etc/network/interfaces file by adding the following:

#wifi ap
auto ath0
iface ath0 inet static
wireless-mode master
wireless-essid linksys
address 192.168.1.1
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255

If you run &#8216;/etc/init.d/networking restart&#8217; and scan for wireless access points from another computer, you should now see an access point called &#8216;linksys&#8217;. "

If the phone uses dhcp, setting that up is described in the above link.

BTW, I Googled: ubuntu access point
and the link was the fifth result.

---

### Post by Iowan on 2010-02-26
[Here]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") is a help page on wireless ICS - dunno if it'll help...

---

### Post by revoltism on 2010-02-27
Thanks guys for pointing me out the correct path.. I was not sure what to look after. Now that you say it, it comes clear. I think i have about 20 pages open on the subject. lol! 

Well.. i'll come back if it works ;)

---

### Post by Iowan on 2010-02-27
> **revoltism said:**
> Well.. i'll come back if it works ;)
Hopefully, you'll come back if it *doesn't* work, too... :?

---

### Post by revoltism on 2010-02-27
> **gordintoronto said:**
> From: [http://www.esrun.co.uk/blog/ubuntu-gateway-access-point-server/](http://www.esrun.co.uk/blog/ubuntu-gateway-access-point-server/)

"Configure wireless card to setup access point

Again we’re going to open a terminal and edit our /etc/network/interfaces file by adding the following:

#wifi ap
auto ath0
iface ath0 inet static
wireless-mode master
wireless-essid linksys
address 192.168.1.1
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255

If you run ‘/etc/init.d/networking restart’ and scan for wireless access points from another computer, you should now see an access point called ‘linksys’. "

If the phone uses dhcp, setting that up is described in the above link.

BTW, I Googled: ubuntu access point
and the link was the fifth result.

Did not work..  now iwconfig say:
```
wlan0     IEEE 802.11bg  ESSID:"Riot"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

---

### Post by revoltism on 2010-02-27
After further investigation of my WiFi driver rtl8187 i discovered this bug report. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/97322](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/97322) Seems like it's a driver problem. I can't run it in Ad-hoc mode.

Is there any way to do this in "managed" mode? According to the man page "managed" is for (node connects to  a network  composed  of  many Access Points, with roaming)

I am pretty lost here...

---

### Post by gordintoronto on 2010-02-27
Sorry, I didn't realize you were running an Alpha release.  I would have directed you to the Lucid Lynx forum.

The phone doesn't see a WiFi network called Riot?

---

### Post by revoltism on 2010-02-27
> **gordintoronto said:**
> Sorry, I didn't realize you were running an Alpha release.  I would have directed you to the Lucid Lynx forum.

The phone doesn't see a WiFi network called Riot?

Yeah.. and what it seams i can't make the network Ad-hoc or Master. So i am stuck with Managed until they fix the bug.. 

Get's this when i try:
```
$ sudo iwconfig wlan0 mode Ad-hoc
Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan0 ; Operation not supported.
``````
$ sudo iwconfig wlan0 mode Master
Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan0 ; Invalid argument.
```

If i set up an Ad-hoc network from the telephone i can see it in Ubuntu but not connect. When i set it up in Ubuntu. It doesn't show.

---

### Post by Sef on 2010-02-27
Moved to Lucid forum.

---

### Post by espen77 on 2010-02-27
You might get it to work by setting up a softAP using airbase-ng.

---

### Post by revoltism on 2010-02-28
> **espen77 said:**
> You might get it to work by setting up a softAP using airbase-ng.

Ok, i have no clue how to do that. I downloaded it and peaked the man page but have not dared to do anything.

---

