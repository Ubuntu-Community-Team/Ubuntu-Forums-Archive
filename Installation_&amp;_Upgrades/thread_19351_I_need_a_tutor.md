---
title: "I need a tutor"
date: 2005-03-11
forum: Installation &amp; Upgrades
---

### Post by speedy2782 on 2005-03-11
I am currently working on my first ever ubuntu install and am running into some difficulties. I have been able to get the thing running and working on the internet through eth0. I was attempting to get my wireless card working and BAM! no eth0 anymore either. 
Would someone be willing to teach me how to effectively set up my ubuntu before I fall back into a lost life of using microsoft windows.
Thanks a lot
Speedy

---

### Post by gw90se on 2005-03-11
Speedy, sorry but I can't helpou with this one, though I am sure that someone will be able to. But don't jump ship too fast. This is well worth the learning curve.

Besides, you can get answers here and not have to call redmond and sit on hold while some screen jockey runs though prompts on a in house web site.

---

### Post by bored2k on 2005-03-11
[QUOTE=speedy2782]I am currently working on my first ever ubuntu install and am running into some difficulties. I have been able to get the thing running and working on the internet through eth0. I was attempting to get my wireless card working and BAM! no eth0 anymore either. 
Would someone be willing to teach me how to effectively set up my ubuntu before I fall back into a lost life of using microsoft windows.
Thanks a lot
Speedy[/QUOTE]
 You need to make a list here of the problems you are encountering, that way I can help you in what I can and others in the others stuff.

---

### Post by az on 2005-03-11
What was the problem with eth0?  What make is your wireless card?

Dont Panic.

Before we go any further, you can manage a webserver from across the globe from a command line.  If the configuration of a wireless card involves you typing things in, do not panic.

Also, post the output of 
lspci
ifconfig

---

### Post by speedy2782 on 2005-03-12
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 650/M650 Host (rev 80)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter
0000:02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

root@laptop:/home/benjamin # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:44:7D:0A
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe44:7d0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:634186 (619.3 KiB)  TX bytes:158759 (155.0 KiB)
          Interrupt:225 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1651424 (1.5 MiB)  TX bytes:1651424 (1.5 MiB)

This is where I am at. I don't have any drivers loaded currently for the MA521. The chip is a rtl8180. My laptop is a Dell Inspiron 1000 if that helps.  
Ben

---

### Post by az on 2005-03-12
Right.  Your eth0 seems to be working.  Is that so?

There are no Realtek wireless drivers available for linux (I believe) since the company does not give a damn about open source.

You should try ndiswrapper.

locate the windows driver (on a cd or something)
cd /media/cdrom/Drivers
sudo ndiswrapper -i drivername.inf
sudo modprobe ndiswrapper
ndiswrapper -l
sudo tail /var/log/messages
ifconfig
iwconfig
sudo dhclient wlan0 (Or whatever name of the device)

---

### Post by speedy2782 on 2005-03-12
i have ndiswrapped the heck out of the .inf files for my card. here is what happens


root@laptop:/home/benjamin # ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:44:7D:0A
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe44:7d0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6974 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6045566 (5.7 MiB)  TX bytes:1222850 (1.1 MiB)
          Interrupt:225 Base address:0x1800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:95337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95337 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6927736 (6.6 MiB)  TX bytes:6927736 (6.6 MiB)

root@laptop:/home/benjamin # iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Installed ndis drivers:
net8180 hardware NOT present
netma521        hardware NOT present
root@laptop:/home/benjamin #


The card I am using is a NetGear Wireless PC Card 32-bit cardbus ma521

Any help is much appreciated.
Ben

---

### Post by az on 2005-03-12
Boot.
Open up a terminal.
sudo tail -f /var/log/messages
open another terminal
inert your card
It is interesting to note what you see in the logs at this point.
insert your ndiswrapper module.
sudo modprobe ndiswrapper
Note again what appears.

Post the logs.

---

### Post by hallowname on 2007-07-03
if anyone does need a tutor, i am starting a tutoring service at [http://www.linuxtutors.com]("http://www.linuxtutors.com")

---

