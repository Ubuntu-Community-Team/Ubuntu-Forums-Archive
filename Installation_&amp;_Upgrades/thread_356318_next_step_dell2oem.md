---
title: "next step dell2oem"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by dimnullspace on 2007-02-08
Please help me fill in the final steps!

1. Build an OEM (done):)

My OEM is: ASUS M2N32-SLI-D
AMD64 +3800 Dual Core
CORSAIR XMS2 240-Pin DDR2 800
NVIDIA GeForce 7300 GT, HDD WD 150G Raptor

2. Get it to POST. Hint -- drive the OEM box around in back seat of a car for a day to get it to POST -- what is with that? -- (done):)

3. flash bios to new ROM Rev to fix kernal panics (done):)

4. Install kubuntu-*-amd64.iso (done):)

5. Boot new linux kernal off HDD (done):)

6. Play around a xterm for a bit < for i in `man grep`;do echo been at this for days;done > (done):)

7. Connect to internet [COLOR="Red"]**(NOT DONE)**[/COLOR]:confused: 

where i am at with task 6.

a - i have a Comcast cable connection using a ethernet cable and Motorola modem
b - try " sudo ifconfig " (did not work)
c - try " sudo pppoeconf " (did not work)

do i need to update drivers? I have done nothing with vido or other drivers. ethernet diver? Am I stuck in the widows frame of mind? If "get drivers" should realy be step 7 let me know.

How do I go from step 6 to step 7 internet? Please advise, I have come so far.

aha

---

### Post by tgm4883 on 2007-02-08
From what I understand, running edgy 64bit is a pita, it is much easier to either run edgy 32 bit or feisty.

bust open a terminal and tell us what ifconfig says.

:EDIT:

Didn't read the whole thing.  When you ran ifconfig, what do you mean it didn't work?  Any error messages?  I have a feeling that your problems are stemming from your chipset.

Almost forgot.  whats does lspci return in terminal

---

### Post by dimnullspace on 2007-02-08
I will echo ifconfig when I get back home from work tonight. what i really want to know is what is my next step?

am i right that i should next get internet, or is it load drivers?

does it matter that I am running Kubuntu? from what i understand it is all ubuntu, just KED rather then Gnome.

thnks

---

### Post by dimnullspace on 2007-02-09
requested info

Using ethernet off a Motorola Surfboard Cable Modem SB5120

sudo ifconfig

eth0 Link encap:Ethernet HWaddr 00:17:31: D C:4B:FE 
inet6 addr: fe80::217:31ff:fedc:4bfe/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:6718 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:411172 (401.5 KiB) TX bytes:636 (636.0 b)
Interrupt:225 Base address:0xa000 

eth1 Link encap:Ethernet HWaddr 00:17:31: D C:59:78 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:233 Base address:0xc000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:416 errors:0 dropped:0 overruns:0 frame:0
TX packets:416 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:31232 (30.5 KiB) TX bytes:31232 (30.5 KiB)

wlan0 Link encap:Ethernet HWaddr 00:15:AF:03:CF:C6 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:2 errors:0 dropped:2 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:184 (184.0 b) TX bytes:0 (0.0 b)

sudo lspci

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation Unknown device 0370 (rev a2)
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 PCI bridge: nVidia Corporation Unknown device 0376 (rev a2)
00:14.0 PCI bridge: nVidia Corporation Unknown device 0374 (rev a2)
00:16.0 PCI bridge: nVidia Corporation Unknown device 0375 (rev a2)
00:17.0 PCI bridge: nVidia Corporation Unknown device 0377 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0393 (rev a1)
03:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
06:00.0 Mass storage controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)

---

### Post by tgm4883 on 2007-02-09
You need to get your internet working.  It looks like you have two network cards, but for some reason, neither are getting an ip address.  Lets try this

```
sudo dhclient eth0
```

and that should get you an ip address, if it doesn't, run this

```
sudo dhclient eth1
```

---

### Post by dimnullspace on 2007-02-10
tgm4883

Thanks, that worked. Really appreciate your help. gave up on the Ethernet and was trying to set up a WiFi, but the land line will work for know, anyways, 

One more question, does this mean that i don't have my video card driver installed right?

aha@nullspace:~$ sudo lspci | grep PCI
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:0e.0 PCI bridge: nVidia Corporation Unknown device 0370 (rev a2)
00:12.0 PCI bridge: nVidia Corporation Unknown device 0376 (rev a2)
00:14.0 PCI bridge: nVidia Corporation Unknown device 0374 (rev a2)
00:16.0 PCI bridge: nVidia Corporation Unknown device 0375 (rev a2)
00:17.0 PCI bridge: nVidia Corporation Unknown device 0377 (rev a2)

---

### Post by tgm4883 on 2007-02-11
No, I think this
```
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0393 (rev a1)

```

Means you don't have a video card driver installed.  I think what you have posted is about your chipset, which could be the root of the problem with the video card.  I am not sure though.

Are you running edgy 32 bit or 64 bit or feisty 32 bit or 64 bit Ubuntu?

---

