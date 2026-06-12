---
title: "Wireless not detected"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by thabanismith on 2007-01-10
Hi

I'm using IBM thinkpad t60 and it's brand new,i installed ubuntu 6.10 but it does not detect wireless.

I did install "network manager applet" and the rebooted the machine hoping that after loging-in it will let me see or view the "gnome-network-manager showing available wireless networks" but it didn't.

Could you please direct me to an exact document or help me to find a way of making sure that it does detect my wireless.

Thank you

---

### Post by scrooge_74 on 2007-01-10
Check these links

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

---

### Post by mtierney on 2007-01-12
In case the links don't guide you, would you tell us what output you get when you enter the following in a Terminal window:

lspci
iwconfig
ifconfig

---

### Post by thabanismith on 2007-01-15
Hi, thanks for the reply

with 'lspci', i get the following

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

iwconfig, i get the following

lo        no wireless extensions.
irda0     no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.

with ifconfig, i get the following

eth0      Link encap:Ethernet  HWaddr 00:15:58:7C:7B:99  
          inet addr:192.168.0.27  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe7c:7b99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:197467 errors:0 dropped:0 overruns:0 frame:0
          TX packets:162318 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:156592692 (149.3 MiB)  TX bytes:79100267 (75.4 MiB)
          Base address:0x2000 Memory:ee000000-ee020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

Thank you

---

