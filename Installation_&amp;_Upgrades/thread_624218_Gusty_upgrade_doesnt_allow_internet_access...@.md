---
title: "Gusty upgrade doesnt allow internet access...:@"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by Scatterit on 2007-11-26
Ok heres my problem... Fiesty Fawn installed amazingly...

About a year ago when i installed Dapper Drake i couldnt get internet access... and sort of gave up on ubuntu for a little while... but then i installed Fiesty and i was more then happy when i could install it and the internet worked instantly...

Recently i have upgraded to gusty the same thing is happening... I cant get intenet access but the connection is there... 

Grr this is very frustrating and i'd really like to get this sorted...

Thankyou in advanced :)

---

### Post by kevinatkins on 2007-11-26
Hi,

How are you connecting to the internet?

---

### Post by Scatterit on 2007-11-27
D-Link Router with a cable.

---

### Post by niceguy123 on 2007-12-28
> **Scatterit said:**
> Ok heres my problem... Fiesty Fawn installed amazingly...

About a year ago when i installed Dapper Drake i couldnt get internet access... and sort of gave up on ubuntu for a little while... but then i installed Fiesty and i was more then happy when i could install it and the internet worked instantly...

Recently i have upgraded to gusty the same thing is happening... I cant get intenet access but the connection is there... 

Grr this is very frustrating and i'd really like to get this sorted...

Thankyou in advanced :)

Same problem here. Was this solved? How? I'm about to go back to FF. (after loss of two days work and all of my data). Now I can't even access the internet.

---

### Post by Scatterit on 2008-01-02
Hey mate... Ok I've only just got a solution so u can browse the internet...

A guy posted on another thread of mine and the solution (hopefully for you) is here...

[http://ubuntuforums.org/showthread.php?p=3887071#post3887071](http://ubuntuforums.org/showthread.php?p=3887071#post3887071)

:popcorn::)

---

### Post by zipperback on 2008-01-02
> **Scatterit said:**
> Ok heres my problem... Fiesty Fawn installed amazingly...

About a year ago when i installed Dapper Drake i couldnt get internet access... and sort of gave up on ubuntu for a little while... but then i installed Fiesty and i was more then happy when i could install it and the internet worked instantly...

Recently i have upgraded to gusty the same thing is happening... I cant get intenet access but the connection is there... 

Grr this is very frustrating and i'd really like to get this sorted...

Thankyou in advanced :)


Please list the output of the following commands:

lspci
ifconfig

Thank you.
- zipperback
:popcorn:

---

### Post by Scatterit on 2008-01-02
???????????:~# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0c.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0e.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0e.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
00:0e.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
00:0e.3 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)


??????????:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2F:7A:A1:29  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe7a:a129/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2690 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2513 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1998417 (1.9 MB)  TX bytes:406686 (397.1 KB)
          Interrupt:21 Base address:0x6800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

Thankyou

---

