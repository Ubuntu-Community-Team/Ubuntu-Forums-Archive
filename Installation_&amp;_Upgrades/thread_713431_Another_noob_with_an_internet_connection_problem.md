---
title: "Another noob with an internet connection problem"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by BigGeoff on 2008-03-02
Hi guys I hope someone can give me a pointer here as I have come so far only to fall at the last hurdle.

Got fed up with Windoze and finally made the move to Linux. Used a new WD Raptor and installed Gutsy 7.10 on my Evesham PC - installed fine and in a very short time and never threw up any errors on installation - I was really impressed, however, I can't seem to get an internet connection. The system has a Foxconn 945P7AA motherboard with built in LAN which is plugged into my cable broadband Ethernet box (this works fine with my laptop through a USB ethernet adapter under windows) and Ubuntu seems to find this as when I do ifconfig in terminal I get indications that eth0 is sending and receiving packets OK.  When I fire up Firefox and type an address it just fails at lookup and comes up with the server not found error. This also must mean I cannot get any updates either.

I get the feeling I have just missed something silly here but just can't figure out what.

Surely someone can help me out here?

Geoff

---

### Post by johnbouma on 2008-03-02
Can you post the output of both 'lspci' and 'ifconfig -a'

---

### Post by dwanders on 2008-03-02
Sounds maybe like DNS - doing an ifconfig -a would help figure the problem, as would knowing your settings in network manager.

---

### Post by BigGeoff on 2008-03-03
Thanks to both of you for replying - I will post as much info as I can tonight when I get home from work. Don't know much about networks but I will do my best.

Geoff

---

### Post by BigGeoff on 2008-03-03
Sorry about the late post - day job getting in the way. As requested:

geoff@evesham:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:01:6C:FB:9A:41  
          inet6 addr: fe80::201:6cff:fefb:9a41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17400 (16.9 KB)  TX bytes:26338 (25.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7901 (7.7 KB)  TX bytes:7901 (7.7 KB)

geoff@evesham:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 81)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 81)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
01:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 11)
04:01.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
04:04.0 Mass storage controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 13)

In network settings eth0 comes up with roaming enabled, but I have tried with DHCP and it didn’t make any difference.

Geoff

---

### Post by punkybouy on 2008-03-03
You don't have an IP address.  Your loopback is looking OK.  You can ping 127.0.0.1 and see if it responds.  I suspect it will which means the IP stack is installed properly.  You are not getting an IP address from your router/switch.  Is your router/switch setup for DHCP?  go to your windows machine and type "ipconfig -a" and jot down the DNS entries and your IP address scheme which I suspect is 192.168.1.0 with a mask of 255.255.255.0.  You could manually assign your Ubuntu machine an IP address say 192.168.1.5 with the same mask as above if that matches the subnet of your router along with the IP address of the router (default route/gateway) and DNS entries and if that works you could then troubleshoot why DHCP is not working.
Look at the configuration of your network card in System/administration/network.  On my Gutsy box its set to "roaming" mode. If not set to roaming set it that way and reboot.

---

### Post by BigGeoff on 2008-03-04
Sorry but I was so tired last night that I didn't even look at what I had copied and of course you are right about no IP address but I know it has shown up in the past. So tonight I checked all the cable connections, rebooted and bingo:

geoff@evesham:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:01:6C:FB:9A:41  
          inet addr:86.14.223.12  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::201:6cff:fefb:9a41/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6799 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7206374 (6.8 MB)  TX bytes:851925 (831.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6720 (6.5 KB)  TX bytes:6720 (6.5 KB)

So I just thought what the hell -  tried Firefox and here I am logged on and replying to this thread on my Gutsy system!

Assuming things don't do a U turn and stop working again I reckon I am in business.

Now I need to start trying to set up the rest of the system :confused:


Thanks guys

---

