---
title: "WIFI Problem Asus motherboard"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by Ampsheep on 2012-02-22
Hey!
 
Have installed Ubuntu 11.10 om a 5-6 year old Desktop.
 
Motherboard: 
Asus P5AD2-E Premium, I925XE, Socket-775
on this motherboard its an onboard wifi.
Ubuntu cant find that.
all the wifi drivers to this motherboard are for Windows.
can anybody help? :)

---

### Post by roelforg on 2012-02-22
I'm really bad with WiFi;

But can you post the output of these commands:
```

sudo ifconfig -a
sudo uname -a
sudo cat /etc/network/interfaces
sudo cat /etc/resolv.conf
sudo lshw -C network

```

Note: the last one will take some time.

---

### Post by grahammechanical on 2012-02-22
I have the Asus P5B Delux motherboard that I brought in 2007. It has a built in wireless adapter and Ubuntu has no problems in recognising that adapter. The drivers are built into the operating system.

Asus does not supply drivers for Linux only for Windows. You may not need drivers. What wireless adapter do you have? The motherboard User Guide should tell you.

My wireless adapter is called Asus WiFi AP Solo. It uses the Realtek RTL 8187 integrated circuit (chip). When I run sudo lshw -C network I see the line "driver = rtl8187". That tells me that the driver is installed. If you see something similar then your driver is installed. And there must be another reason why you are not making a connection.

You need to give more information.

Please read through this Wireless Troubleshooting Guide

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Please describe what information you see when you click on the network manager icon in the left of the top panel.

Regards.

---

### Post by Ampsheep on 2012-02-23
hers the output:

sudo lshw -C network
[sudo] password for mathias: 
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 15
       serial: 00:11:d8:b2:00:36
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.10.107 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:cfefc000-cfefffff ioport:c800(size=256) memory:cfec0000-cfedffff
  *-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 15
       serial: 00:11:d8:b1:f1:5e
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:cfdfc000-cfdfffff ioport:b800(size=256) memory:cfdc0000-cfddffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: 88W8310 and 88W8000G [Libertas] 802.11g client chipset
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 07
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:cfce0000-cfceffff memory:cfcb0000-cfcbffff

---

### Post by grahammechanical on 2012-02-23
This tells us your wireless device

> product: 88W8310 and 88W8000G [Libertas] 802.11g client chipset
vendor: Marvell Technology Group Ltd.

You need to use something called ndiswrapper to install a Windows Driver. I have never used ndiswrapper so I cannot explain how to use it. Here is a link.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

You should find the ndiswrapper GUI in the software centre but you may still need to install ndiswrapper-utils through the terminal.

The guide is old. It mentions the Synaptic Package Manager which is no longer installed by default in 11.10. So, you will need to install Synaptic Package Manager through the software centre.

I have tried to find more up to date information especially relating to your wireless device but the information is old and not easy to follow.

Sorry, but this is the best that I can do.

Regards.

---

### Post by lkraemer on 2012-02-26
Ampsheep,
So far I don't see any reference to Wifi!


**1. How do I know if I have XXXX Wifi Hardware?**

Open a Terminal Window (Console) and use these commands to get more information on your hardware, wireless, Windows loaded drivers,
and Linux drivers that are currently blacklisted. **Copy & Paste to prevent errors!**
```

lspci
lsusb
lshw -C network
lsmod
ndiswrapper -l 
cat /etc/modprobe.d/blacklist.conf
iwconfig

```
iwconfig will show what the wireless is detected as......wlan0, ath0, etc.
**Copy & Paste each section into a txt file.  Please post the txt file.**

If your Wifi isn't detected in the above information you are out of luck.
 
Your options that can be used to get the Wifi functional:

1.  Use the Windows Drivers with ndiswrapper (Last choice!)
2.  Use the Default Ubuntu Drivers

If you haven't done so yet, connect via an Ethernet Patch Cable and do an
update, then try to enable the Hardware Drivers.  Maybe that will find your hardware.

Post the results.

lk

---

### Post by Ampsheep on 2012-02-28
heres the file.
hope you can help me now :)

---

### Post by lkraemer on 2012-02-29
Well, it appears that your ASUS Mobo has Wifi built in.  There is a Gentoo Forum posting about how someone
got it working with ndiswrapper and the ASUS Mobo Drivers.  If you attempt this you are going to need to
know the following:

1.  *nix is 32 bit or 64 Bit?
2.  ASUS Drivers must be same (as *nix) 32 bit or 64 bit?
3.  Compile or install nidswrapper and load the module.

REF:
[http://forums.gentoo.org/viewtopic-t-377578-start-0-postdays-0-postorder-asc-highlight-.html](http://forums.gentoo.org/viewtopic-t-377578-start-0-postdays-0-postorder-asc-highlight-.html)
Posting by TWO515TY
[http://www.linuxforums.org/forum/ubuntu-linux/95825-libertas-wireless-network-issue-dhcp-not-leasing.html](http://www.linuxforums.org/forum/ubuntu-linux/95825-libertas-wireless-network-issue-dhcp-not-leasing.html)

> 
Yay, another P5AD2-E Premium user. Getting some of my hardware (mainly the network stuff) to work with this mobo was a mofo,
but in the end, I got it going.

Basically, to get the wireless working, you need to use ndiswrapper-1.0, not 1.2. Go to the ndiswrapper website, download
and compile ndiswrapper-1.0 (I think you can emerge it, but I'm not sure). Install the necessary drivers, then do


modprobe ndiswrapper


and you should be able to use the wireless-tools to get it going from there.

Do note though that although this process worked for, me, I was using a 32 bit-install, and 32-bit drivers. It may be
different if you're on a 64-bit install and using 64-bit drivers.


So, you may or maynot be able to get it working............
To get ndiswrapper installed you can follow this reference:
[http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3ABroadcom](http://ubuntuforums.org/showthread.php?t=1470146&highlight=HOWTO%3ABroadcom)
**Just ignore the ALL references to STEP #2 B43**

OR, you can purchase a USB Wifi Dongle and plug it in and use it.

lk

---

