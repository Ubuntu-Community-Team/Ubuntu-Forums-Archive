---
title: "Installed Ubuntu on HP Pavilion dv7 but installtion is unuseable"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by UeB on 2008-09-12
I bought a new HP Pavilion dv7-1001eg yesterday an tryed to install Ubuntu 8.04.1 on it. But Ubuntu is basically unusable.

I went through the installation without noticing any errors besides a freeze after the installtion was done (I was already told to take out the Ubuntu CD and press enter)

After the roboot I can log into gnome but the starting something is extreamly slow. For example just staring a gnome terminal needs 10 seconds.
The screen resolution is wrong and I cannot change it to the right one inside Gnome (should be 1440x900 but Gnome does not give me that option even after pressing the detect screen button)
Some Gnome apps especially for system configuration do not start at all.
If I press ctr+alt+f1 for a text only terminal and then switch back to Gnome all colours are wrong looking a bit psychodelic.

And the worst thing internet does not work!!!!

That is why I am writing from the preinstalled MS Vista at the moment.  

For internet I just need a woring ethernet device with either DHCP or static IP, gateway and subnetmask. I tryed both in this gnome net config window but I cannot even ping the gateway although it is definitly up because I am online with Vista at the moment.

Someting like sudo ifup --force eth0 did not help anything, too. Told me eth0 is up and running.

Any help? What should I try/do? 

thanks in advance

---

### Post by benjick on 2008-09-12
This is a very new model from HP. Did you try to activate backports to get drivers etc?

---

### Post by Bucky Ball on 2008-09-12
In a terminal, type:

**lspci**

... and we can look at what hardware you have.

---

### Post by UeB on 2008-09-12
lspci says:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. Unknown device 2380
08:00.1 System peripheral: JMicron Technologies, Inc. Unknown device 2382
08:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
08:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
08:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384
09:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

---

### Post by UeB on 2008-09-12
> **benjick said:**
> This is a very new model from HP. Did you try to activate backports to get drivers etc?

no I did not, but I will.

it really feels if there is something wrong with the installation. When using sudo in the text only terminal it takes 5 to 10 seconds until I am asked for my password.

---

### Post by UeB on 2008-09-12
[QUOTE=UeB;5776041]no I did not, but I will.[QUOTE]

ups I forgot that internet is not working ;-)

here is what ifconfig says:

```
eth0      Link encap:Ethernet  Hardware Adresse 00:1e:ec:a4:b0:f3  
          inet Adresse:172.16.78.32  Bcast:172.16.255.255  Maske:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:3802062978 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Basisadresse:0x2000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:2106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2106 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:107644 (105.1 KB)  TX bytes:107644 (105.1 KB)
```

sorry for the german words do not know how to switch terminal output to english only istead of this stupid half transalted thing.

and this is also strange:

```
moritz@skynet:~$ sudo ifup eth0 
sudo: unable to resolve host skynet
[sudo] password for moritz: 
ifup: interface eth0 already configured
moritz@skynet:~$ ping 172.16.0.1
PING 172.16.0.1 (172.16.0.1) 56(84) bytes of data.
From 172.16.78.32 icmp_seq=1 Destination Host Unreachable
From 172.16.78.32 icmp_seq=2 Destination Host Unreachable
From 172.16.78.32 icmp_seq=3 Destination Host Unreachable
From 172.16.78.32 icmp_seq=4 Destination Host Unreachable
From 172.16.78.32 icmp_seq=5 Destination Host Unreachable
From 172.16.78.32 icmp_seq=6 Destination Host Unreachable

--- 172.16.0.1 ping statistics ---
7 packets transmitted, 0 received, +6 errors, 100% packet loss, time 6015ms
, pipe 3
```

do not know what this unable to resolve means but it does not sound good.

what I tryed to ping was our gateway.

Getting this error messages online is difficult: I have to save them in a file on a usb had disc than open it under vista and copy it in this forum.

---

### Post by UeB on 2008-09-12
Ok I solved the problems with sudo and the slow/non-starting apps after a google serche:
had to do with this:

[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/195308](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/195308)

After changing /etc/hosts that it mached /etc/hostname sudo worked and gksudo worked correcly.

seems as the this gome network app somehow messed this up.

BUT still no internet!!! 

Although ifconfig says eth0 is up I cannot even ping machines in the LAN.

What to do??

---

### Post by Bucky Ball on 2008-09-12
System->Administration->Network

and make sure you have the correct details in there for your network and security, if you are running (WEP/WPA). Yep, your card is up no problems by the looks, just not connecting with the router.

Are you running windoze on the same machine? If so, you can get a clue of the info you need for your router by opening 'Run' from the 'Start' menu and typing 'com' in there. That should give you a list of your wireless details from memory. You can then try out the same in Ubuntu and no reason it shouldn't work.  :)

---

### Post by UeB on 2008-09-12
wireless?

I just need my wired ethernet to work nothing else.

I already tpyed in alle the info needed: my ip subent mask and gateway and the fist an secondary dns server. Alternatively I also tryed dhcp instead which should also work. But it does not!

I did excactly the same what I did with the notebook I had before ( it broke last week ) and there the internet over this WIRED network with the same gateway alsway worked. I used Ubunut for 2 years on it and never had problem with the networking device there ( was also a realtek something ).

---

### Post by UeB on 2008-09-13
damit. It is the driver looks like a lot of fun I have to go through:

[https://bugs.launchpad.net/ubuntu/+bug/208012](https://bugs.launchpad.net/ubuntu/+bug/208012)

I am ready for the sleghammer :mad:

---

### Post by lopata on 2008-09-13
i have  pavilion dv7  and i managed to get my wifi working

everything is in this threat  [http://ubuntuforums.org/showthread.php?t=879134](http://ubuntuforums.org/showthread.php?t=879134)

---

### Post by UeB on 2008-09-14
Problem solved by using this instructions:

[https://bugs.launchpad.net/ubuntu/+bug/208012](https://bugs.launchpad.net/ubuntu/+bug/208012)

(I mentioned these 2 posts earlier already) 

@lopata:
you are talking about WIRELESS lan.
I am talking about WIRED lan.

---

