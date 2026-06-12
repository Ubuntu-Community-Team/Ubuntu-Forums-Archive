---
title: "Netgear WNDA3100v2, Ubuntu 9.10, HP Pavilion g6 laptop"
date: 2012-08-28
forum: Installation &amp; Upgrades
---

### Post by pr0gramr7 on 2012-08-28
Hello, 

I recently installed Karmic Koala from liveCD and removed Windows 7 (At least, I believe it is erased). However, it is not recognizing wireless signals. That is, the LED button on the keyboard for the internal WIFI (RaLink 5390; driver: rt2x00) just stays red. I bought an external USB adaptor (Netgear WNDA3100v2; driver: ar9170), but Karmic is not recognizing it. I am sure I need a driver somewhere. Or maybe more than that. I am not familiar with how to add the Harware Drivers in the system. And I can imagine this is more complicated because I have no internet connection on the HP. (neither Ethernet nor WIFI). 

I have provided info below and the commands connected with them for much more specific details of the problem for my more experienced readers.

1.  lspci

01:00.0 Network controller: RaLink Device 5390 

2.  lsusb

Bus 002 Device 004: ID 0846:9011 NetGear, Inc.  
Bus 002 Device 003: ID 058f:a001 Alcor Micro Corp.  
Bus 002 Device 002: ID 8087:0024   


3. lspci -nn | grep 'Wireless Brand'  

(no response. returned to prompt.)


4.  ifconfig

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 


5.  iwconfig

lo        no wireless extensions. 
 
eth0      no wireless extensions. 

6.  lsmod

Module                  Size  Used by 
usbhid                 43968  0  
binfmt_misc            10220  1  
ppdev                   8232  0  
uvcvideo               65260  0  
lp                     11908  0  
iptable_filter          3872  0  
psmouse                57124  0  
ip_tables              21200  1 iptable_filter 
videodev               43360  1 uvcvideo 
v4l1_compat            16804  2 uvcvideo,videodev 
v4l2_compat_ioctl32    13344  1 videodev 
x_tables               25832  1 ip_tables 
parport                40528  2 ppdev,lp 
serio_raw               6596  0  
r8169                  38884  0  
mii                     6368  1 r8169 
video                  23612  0  
output                  3680  1 video 


7.  dmesg 

(VERY LONG; AM NOT SURE WHICH INFO / LINE IS USEFUL; MAYBE YOU CAN HELP!)


8.  sudo lshw -C network

 *-network UNCLAIMED      
       description: Network controller 
       product: RaLink 
       vendor: RaLink 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:c2500000-c250ffff 
  *-network DISABLED 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 05 
       serial: 44:1e:a1:d6:47:89 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
       resources: irq:33 ioport:3000(size=256) memory:c0404000-c0404fff(prefetchable) memory:c0400000-c0403fff(prefetchable) 



9. iwlist scan

lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 



10.  lsb_release -d

Description:	Ubuntu 9.10 


11.  uname -mr

2.6.31-14-generic x86_64 


12.  sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                               [ OK ]  


As you can tell, except for number 7, I have provided all the info I thought was pertinent for the problem. Please suggest for number 7 the line of the output that would be useful.

By the way, i am a newbie. This is my second post. I think my first post might not have been detailed enough so I am trying again with specific detail.

To sum up: I want to use the Netgear adaptor, not the RaLink that came with the computer. Also, I DO NOT HAVE ANY internet access on the HP, so please, if you would be so kind, let me know STEP-BY-STEP how to download, copy and install all potential info I will have to hunt from another computer. I am prepared to hunt, but I know I lack certain techniques / know-how regarding how to check for files, memory, checksums, etc. But I will learn.

P.S. I suppose if I could access the internet from the HP I would not need to write this thread.

P.S. #2  Just a side note, could you give me an opinion about whether or not this computer is good for installing / running Ubuntu distros or any Unix distro for that matter?

Thank you in advance.

---

### Post by pr0gramr7 on 2012-08-28
Hello,

QUESTION(S):

How do I correctly download, save, copy and install drivers and / or firmware if my laptop has no internet access?

Most of the info being posted seems to be geared toward downloading directly on the computer with the problem.

What if you cannot connect at all? What does one do?

I would be highly greatful if someone can teach me this skill!

I have provided info below and the commands connected with them for much more specific details of the problem for my more experienced readers.

(Netgear WNDA3100v2; driver: ar9170)
(RaLink 5390; driver: rt2x00)

1.  lspci

01:00.0 Network controller: RaLink Device 5390 

2.  lsusb

Bus 002 Device 004: ID 0846:9011 NetGear, Inc.  
Bus 002 Device 003: ID 058f:a001 Alcor Micro Corp.  
Bus 002 Device 002: ID 8087:0024   


3. lspci -nn | grep 'Wireless Brand'  

(no response. returned to prompt.)


4.  ifconfig

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 


5.  iwconfig

lo        no wireless extensions. 
 
eth0      no wireless extensions. 

6.  lsmod

Module                  Size  Used by 
usbhid                 43968  0  
binfmt_misc            10220  1  
ppdev                   8232  0  
uvcvideo               65260  0  
lp                     11908  0  
iptable_filter          3872  0  
psmouse                57124  0  
ip_tables              21200  1 iptable_filter 
videodev               43360  1 uvcvideo 
v4l1_compat            16804  2 uvcvideo,videodev 
v4l2_compat_ioctl32    13344  1 videodev 
x_tables               25832  1 ip_tables 
parport                40528  2 ppdev,lp 
serio_raw               6596  0  
r8169                  38884  0  
mii                     6368  1 r8169 
video                  23612  0  
output                  3680  1 video 


7.  dmesg 

(VERY LONG; AM NOT SURE WHICH INFO / LINE IS USEFUL; MAYBE YOU CAN HELP!)


8.  sudo lshw -C network

 *-network UNCLAIMED      
       description: Network controller 
       product: RaLink 
       vendor: RaLink 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:c2500000-c250ffff 
  *-network DISABLED 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 05 
       serial: 44:1e:a1:d6:47:89 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
       resources: irq:33 ioport:3000(size=256) memory:c0404000-c0404fff(prefetchable) memory:c0400000-c0403fff(prefetchable) 



9. iwlist scan

lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 



10.  lsb_release -d

Description:	Ubuntu 9.10 


11.  uname -mr

2.6.31-14-generic x86_64 


12.  sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                               [ OK ]  

I would like to use the Netgear adaptor since I saw that it is compatible with Ubuntu.

I could not find compatibility info for the Ralink however.

p.s. if you think I could use the RaLink instead, please let me know. It worked quite well under windows. 

Thank you in advance.

---

### Post by mörgæs on 2012-08-28
Threads merged. Please don't double-post.

---

### Post by pr0gramr7 on 2012-10-24
To Whom it May Concern:

This thread is no longer valid.

The circumstances involving this installation changed a little.

PLEASE REFER TO THIS POST:     [http://ubuntuforums.org/showthread.php?t=2049273](http://ubuntuforums.org/showthread.php?t=2049273)

Thank you.

---

