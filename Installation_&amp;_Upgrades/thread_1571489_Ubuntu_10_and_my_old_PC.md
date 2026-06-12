---
title: "Ubuntu 10 and my old PC"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by djnemo on 2010-09-09
Hello all im new in this forum ;) and this is my first message sorry if ask it somewhere wronge.

i installed ubuntu 10.04 on my old PC with 512MB of ram AMD 3.00 GHz it works very very slow and when i take a look on resources it seems all taken on loading the OS.

I thought if i downgrade it to 9.xx mybe it works better ?does this really helps me?
how can i solve this problem ?

thank you very much

---

### Post by andrewthomas on 2010-09-09
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

or you could just try Xubuntu or Lubuntu.

[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by plucky on 2010-09-10
> **djnemo said:**
> Hello all im new in this forum ;) and this is my first message sorry if ask it somewhere wronge.

i installed ubuntu 10.04 on my old PC with 512MB of ram AMD 3.00 GHz it works very very slow and when i take a look on resources it seems all taken on loading the OS.

I thought if i downgrade it to 9.xx mybe it works better ?does this really helps me?
how can i solve this problem ?

thank you very much

I have 10.04 installed on an AMD 800MHz with 512Mb memory and it is fine.Look at what is using up resources > it seems all taken on loading the OS. Please expand on this statement.

What VGA card do you have installed?
Open **System > Administration > Hardware Drivers** and see what drivers are loaded for your VGA card.

Post the output of the ```

lspci
top
``` commands from a terminal.

Good Luck

---

### Post by djnemo on 2010-09-10
here is the outputs:
```

**$ lspci**

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:05.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

```

```

**$ top**

Tasks: 127 total,   2 running, 125 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.6%us,  1.0%sy,  0.0%ni, 91.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    444540k total,   394400k used,    50140k free,     3860k buffers
Swap:   530104k total,    22720k used,   507384k free,   106716k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1459 m4jid     20   0  383m  93m  27m R  6.6 21.5   1:51.20 firefox-bin        
  940 root      20   0  246m  46m 7808 S  1.0 10.8   0:49.44 Xorg               
  833 root      20   0  397m  44m 1196 S  0.3 10.2   0:06.41 nessusd            
 1248 m4jid     20   0 40116  12m 9.8m S  0.3  2.9   0:24.94 multiload-apple    
    1 root      20   0  2784 1412 1052 S  0.0  0.3   0:00.34 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.72 events/0           
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper            
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns              
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr          
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm                 
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers        
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default        


```
i check Hardware driver but i doesn't find any uninstalled driver, just a soft modem.
[B]Memory 63% use by programs
22% in use as catch[/B]
my CPU is AMD Sempron 3000+ which is 1.80 Ghz
You guys dont think installing older version may help me in this ?

---

### Post by djnemo on 2010-09-12
[B]Im Still waiting for answer plz 
[/B]

---

### Post by Troublegum on 2010-09-12
With just 512MB RAM, Ubuntu is no fun at all. Installing an older version does not change that. **However, there a are different ubuntu variants that will be lightning fast on your computer and look still good. **

Ubuntu uses GNOME as its desktop. There are alternatives that do not require very much RAM. andrewthomas suggested Lubuntu. Lubuntu uses LXDE as its desktop. LXDE is also my recommendation. However, I'd suggest to take a look at Linux Mint LXDE ([www.linuxmint.org](www.linuxmint.org)). It's based on Ubuntu but uses LXDE as desktop. It runs very fast on 512MB RAM.

---

