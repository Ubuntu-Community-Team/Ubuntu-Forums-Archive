---
title: "Intrepid wireless ok on LiveCD -- gone on install"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zacktu on 2008-10-15
I decided to add Ubuntu to a laptop that was only Windows.  Before doing that I used the 8.10 beta liveCD to check out the wireless.  It worked beautifully.  Clicking on the Network Manager icon showed my wireless router immediately.  It was a snap to complete the setup.  I created a new partition and installed 8.10 beta from the CD.  Now, there's no wireless!  Executing iwconfig shows no awareness that there's even a wireless device.

What happened?

---

### Post by forger on 2008-10-15
post back the output of this command in terminal:
```
apt-cache policy gnome-about
apt-cache policy network-manager-gnome
lspci
sudo lshw -C network
```
You might consider [filing a bug]("https://bugs.launchpad.net/ubuntu/+filebug") with this information and a description of your problem

---

### Post by zacktu on 2008-10-16
Here are the results of executing the commands you suggested:

zack@mozart:~$ apt-cache policy gnome-about 
gnome-about: 
  Installed: 1:2.24.0-0ubuntu2 
  Candidate: 1:2.24.0-0ubuntu2 
  Version table: 
 *** 1:2.24.0-0ubuntu2 0 
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages 
        100		 /var/lib/dpkg/status 
zack@mozart:~$ apt-cache policy network-manager-gnome 
network-manager-gnome: 
  Installed: 0.7~~svn20081012t133407-0ubuntu1 
  Candidate: 0.7~~svn20081012t133407-0ubuntu1 
  Version table: 
 *** 0.7~~svn20081012t133407-0ubuntu1 0 
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages 
        100 /var/lib/dpkg/status 
zack@mozart:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) 
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) 
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03) 
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) 
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03) 
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) 
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01) 
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller 
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller 
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05) 
zack@mozart:~$ sudo lshw -C network 
[sudo] password for zack: 
  *-network               
       description: Ethernet interface 
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:12:3f:fa:d7:48 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.29a latency=0 link=no module=tg3 multicast=yes port=twisted pair 
  *-network UNCLAIMED 
       description: Network controller 
       product: PRO/Wireless 2200BG [Calexico2] Network Connection 
       vendor: Intel Corporation 
       physical id: 3 
       bus info: pci@0000:03:03.0 
       version: 05 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm cap_list 
       configuration: latency=64 maxlatency=24 mingnt=3 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 32:f6:c3:a4:93:83 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
zack@mozart:~$

---

### Post by muzzamo on 2008-10-19
I'm having the same problem. iwconfig is showing:

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

ppp0      no wireless extensions.


In my case I have been running intrepid since the beta, but on one of the most recent updates my wireless stopped working. 

I tried installing knetworkmanager and (not surprisingly) it can't see any wireless devices either. 

I guess this would be a bug against the intel wireless driver? 

Whats interesting is that this would be quite common hardware so i'm suprised that this forum post was the only other confirmation that this is an issue.

---

### Post by muzzamo on 2008-10-19
I did a cat /var/log/syslog | grep 2200 and this is what I got:

```

Oct 18 22:09:19 murray-laptop kernel: [   19.080919] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
Oct 18 22:09:19 murray-laptop kernel: [   19.080922] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Oct 18 22:09:19 murray-laptop kernel: [   19.431495] ipw2200 0000:02:01.0: PCI INT A -> Link[LNKE] -> GSI 10 (level, low) -> IRQ 10
Oct 18 22:09:19 murray-laptop kernel: [   19.535981] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Oct 18 22:09:19 murray-laptop kernel: [   19.536067] firmware: requesting ipw2200-bss.fw
Oct 18 22:09:19 murray-laptop kernel: [   21.840154] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
Oct 18 22:09:19 murray-laptop kernel: [   21.840168] ipw2200: Unable to load firmware: -2
Oct 18 22:09:19 murray-laptop kernel: [   21.840172] ipw2200: failed to register network device
Oct 18 22:09:19 murray-laptop kernel: [   21.840278] ipw2200 0000:02:01.0: PCI INT A disabled
Oct 18 22:09:19 murray-laptop kernel: [   21.840300] ipw2200: probe of 0000:02:01.0 failed with error -5

```

---

### Post by muzzamo on 2008-10-19
I've filed a bug for this one: 

[https://bugs.launchpad.net/ubuntu/+bug/285837](https://bugs.launchpad.net/ubuntu/+bug/285837)

---

