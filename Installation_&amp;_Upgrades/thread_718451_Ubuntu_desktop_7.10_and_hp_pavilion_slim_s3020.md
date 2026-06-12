---
title: "Ubuntu desktop 7.10 and hp pavilion slim s3020"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by palban on 2008-03-08
Hi all,
i just installed ubuntu desktop 7.10 on my machine, but i have problem with wifi and ethernet.

when i type iwconfig system show me wlan0, but if i type iwlist scanning system tell me there are not any wifi card. Ethernet not work. Pls help me

---

### Post by uberlube on 2008-03-08
What type of wireless card do you have. You've gotta provide as much info as you can to get speedy results. :)

---

### Post by palban on 2008-03-08
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1A:92:99:64:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:1A:92:99:64:29  
          inet addr:169.254.5.103  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:DC:A7:DD  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-DC-A7-DD-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


iwconfig:

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lspci:
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7500 LE] (rev a1)
02:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

lsusb

Bus 005 Device 003: ID 15a9:0004  
Bus 005 Device 004: ID 058f:6377 Alcor Micro Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c517 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

that's all. thanks in advance

---

### Post by uberlube on 2008-03-08
k im still gonna need the name of your wireless card as it is not shown in the output.

---

### Post by palban on 2008-03-08
i not know, but vendor is Ralink and my machine model is hp pavilion slim 3020.it. Man also ethernet card not work, but system detect it up

---

### Post by uberlube on 2008-03-08
K if your vendor is ralink then your chipset would be 1 of these options. Do any of these ring a bell?
RT2860
RT2870
RT2501
RT2500

You dont have the wondows version of the drivers on disk do you?

---

### Post by palban on 2008-03-08
no i have not windows, i just installed ubuntu.

---

### Post by uberlube on 2008-03-08
K out of those 4 above wich looks like the right one?

---

### Post by uberlube on 2008-03-08
Also do you know what exact model of 3020 you pc is? is it an s3020.be , .es , .it, .nl, .cs, jp, la , n ? It might just be easier if you would give me the serial number and product number of your PC. They should be listed on a sticker somewhere on it. This will help me narrow down the type of wireless card you have.

---

### Post by uberlube on 2008-03-08
You still there?

---

### Post by Pumalite on 2008-03-08
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by palban on 2008-03-08
sorry i just come back s3020.it is my pc model

---

