---
title: "Ubuntu Gutsy beta works fine, but how about the Internet ?"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by Devoske on 2007-10-10
Hey, 

I just installed the Gutsy beta version on my laptop ( hp 9000 series ), and it looks as if everything works fine, except for the video, sound etc drivers... To install these, I need to get acces to the Internet. We have Telenet, a provider in Belgium of DSL Internet, but I don't know the things like a username and a password and stuff because I'm a student and we are with 10 people in one building. So these things are not known for everyone. Which steps should I follow to get Internet installed ? On Windows Vista, I just had to plug it and I was able to get on the Internet. In other words, this is completely new for me.

Thanks !

---

### Post by Devoske on 2007-10-10
Can anybody help me ? It was a task from our professor to get Ubuntu working by tommorow, so I don't have much time left.... Thanks !!!

---

### Post by Wim Sturkenboom on 2007-10-10
Somewhere under system->networking? No Ubuntu at hand at the moment. You probably have to set it to DHCP.

---

### Post by Devoske on 2007-10-10
I tried that already , but I can't seem to get connection :s

---

### Post by Wim Sturkenboom on 2007-10-11
You can check if you get an ip address by running ifconfig. If so, you can check if you can ping a website by name or if you ping it by address? If the first does notwork, but the second one does, you have a DNS issue and you might have to setup the dns servers in your configuration; that's the time to contact your 'network administrtaor'.

---

### Post by Devoske on 2007-10-11
When I type in ifconfig, I get this : 

Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/12 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:190 errors:0 dropped:0 overruns:0 frame:0
TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:9500 (9.2 kB) TX bytes:9500 (9.2 kB)

What does this mean ? Can this be such an DNS issue ?

Thanks !

---

### Post by andreeh on 2007-10-11
It means that it's not finding your network card and/or your IF is not up.

Post the output of these commands:

```
sudo ifup eth0
```
```
lspci -v
```
```
dmesg | grep -i net
```

---

### Post by Camp0s on 2007-10-11
Uhm.. maybe ubuntu hasn't detected any of your network card, try:

ifconfig wlan0 up
ifconfig eth0 up
ifconfig eth1 up
ifconfig wifi1 up

Abd post the messages that your system gives, these commands are absolutely no harm for your pc, they just try to bring up network devices.


Your next command will be:

dhclient <iface>

Where iface is the name (eth0, wifi0...) of the first device which will respond.

But beware ! this solution assume your hardware is working properly... if it's a driver issue..

---

### Post by Devoske on 2007-10-11
andreeh, these were the answers to the commands you said : 

dimitri@dimitrilemmens:~$ sudo ifup eth0
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth0.





dimitri@dimitrilemmens:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: cc000000-ceffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1800 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1820 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at f8504800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at f8500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        Memory behind bridge: f8000000-f80fffff
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: f4000000-f7ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f3ffffff
        Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f8100000-f81fffff
        Prefetchable memory behind bridge: 0000000088000000-00000000880fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1860 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at f8504c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
        Memory behind bridge: f8200000-f82fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18a0 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 219
        I/O ports at 18d8 [size=8]
        I/O ports at 18cc [size=4]
        I/O ports at 18d0 [size=8]
        I/O ports at 18c8 [size=4]
        I/O ports at 18e0 [size=32]
        Memory at f8504000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: medium devsel, IRQ 10
        Memory at 88100000 (32-bit, non-prefetchable) [size=256]
        I/O ports at 1c00 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at cc000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
        Subsystem: Intel Corporation Unknown device 1101
        Flags: bus master, fast devsel, latency 0, IRQ 218
        Memory at f8000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at 4000 [size=256]
        Memory at f8100000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <access denied>

07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at f8200000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

07:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at f8200800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8200c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8201000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cc
        Flags: bus master, medium devsel, latency 32, IRQ 11
        Memory at f8201400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>



dimitri@dimitrilemmens:~$ dmesg | grep -i net
[   16.911369] NET: Registered protocol family 16
[   17.034767] NET: Registered protocol family 8
[   17.034768] NET: Registered protocol family 20
[   17.065348] NET: Registered protocol family 2
[   17.673497] audit: initializing netlink socket (disabled)
[   18.093079] NET: Registered protocol family 1
[    7.292000] r8169 Gigabit Ethernet driver 2.2LK loaded
[   16.860000] NET: Registered protocol family 31
[   20.740000] NET: Registered protocol family 17
[   76.636000] NET: Registered protocol family 10

---

### Post by Devoske on 2007-10-11
Camp0s, I gave in the commands you asked but as you can see he doesn't find any device and  I&#8221;m sure everything from the Internet itself is ok because I'm working with another pc 
( the one that I'm on right now ) and it's no problem to get connected to the Internet

dimitri@dimitrilemmens:~$ ifconfig wlan0 up
SIOCSIFFLAGS: Toegang geweigerd
dimitri@dimitrilemmens:~$ ifconfig eth0 up
eth0: ERROR while getting interface flags: Onjuist apparaat
dimitri@dimitrilemmens:~$ ifconfig eth1 up
SIOCSIFFLAGS: Toegang geweigerd
dimitri@dimitrilemmens:~$ ifconfig wifi1 up
wifi1: ERROR while getting interface flags: Onjuist apparaat


Is it still of any use that I do the &#8220; dhclient &#8220; command ? Thanks !

---

### Post by andreeh on 2007-10-11
> 02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
Subsystem: Intel Corporation Unknown device 1101
Flags: bus master, fast devsel, latency 0, IRQ 218
Memory at f8000000 (64-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>There's your network card (by the way, my bad on the eth0 thing, all wlan cards have wlan0 wlan1 etc)

I've never heard of that card, neither do I know if there's any modules for it. However, this might be helpful (note that this is for 7.04 and might not work under Gutsy).

[http://ubuntuforums.org/showthread.php?t=471794](http://ubuntuforums.org/showthread.php?t=471794)

Regards.

Edit: I just noticed that you have a ethernet card also, which one do you try to set up?
[B]
Edit 2
[/B]try 
```
sudo modprobe r8169
```
and
```
sudo ifup eth0
```

---

### Post by Devoske on 2007-10-11
Ok, thanks first for reading those pages of text :p

I am trying to use the ethernet card, and in my network settings, I have only enabled one connection : the wired connection ( it says that it has the adress &#8220; dhcp &#8220; ) ( I also tried to enable all the connections, but that didn't help ). So, now back to the commands you asked me to enter : 

dimitri@dimitrilemmens:~$ sudo modprobe r8169
[sudo] password for dimitri: ( here I entered my userpassword, but nothing happened ), so I went to the next command :


dimitri@dimitrilemmens:~$ sudo ifup eth0
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth0.

Hope this makes you any wiser...

Thanks !

---

### Post by andreeh on 2007-10-11
If modprobe didn't give you any output it should have gone well.

post your ```
dmesg | tail
``` output after modprobe, and also try ```
ifconfig
``` once more (after) to see if your card might have been getting some other eth*.

I'm not in any way an expert on these field but I've had my share of faulty modules / hard time getting network cards to work. :)

---

