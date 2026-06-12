---
title: "Ubuntu w/ Intel Wireless 2100"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by eelozano on 2005-07-20
So I've been reading through the forums for about 2 hours and I think I have started going backwards so I'm going to post here.

Ok originally my problem was that the wireless wasn't working.  I would unplug the network cable (it worked fine) and the wireless wouldn't work.

I've now degenerated to the point where I can not have the wireless (eth1) active...if I do the non-wireless connection work anymore.

I realize I need to supply you with information to get help, but I'm not sure what information you will need so if you can go ahead and tell me I'll get it to you as fast as I possibly can.

---

### Post by eelozano on 2005-07-20
I have gottent he wireless to work miraculously.  I installed the ndiswrapper and went through there little run thru and it seemed to work.

I still don't really know what I did though...back to the drawing board.

---

### Post by eelozano on 2005-07-20
Well it worked for a few minutes at least :)...its back down to its original lack of working again.

---

### Post by varunus on 2005-07-20
Can you post the output of "iwconfig" and "ifconfig" in a terminal here?  Also the output of "lspci -v" in a terminal?

Also, the output of "cat /etc/network/interfaces" in a terminal.

---

### Post by eelozano on 2005-07-21
Thank you for your response (and congratulations on going to school in Indiana :)...I'm at IU, but don't hold that against me).

========
= iwconfig =
========

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Squirrel"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:39:75:45
          Bit Rate=11 Mb/s   Tx-Power:off
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=100/100  Signal level=-46 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


=======
= ifconfig =
=======

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:C9:55:96
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fec9:5596/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20003 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15717205 (14.9 MiB)  TX bytes:2511542 (2.3 MiB)
          Interrupt:11

eth1      Link encap:Ethernet  HWaddr 00:0C:F1:49:30:89
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fe49:3089/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:5043 (4.9 KiB)  TX bytes:6768 (6.6 KiB)
          Interrupt:5 Memory:fafef000-fafeffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:219313 errors:0 dropped:0 overruns:0 frame:0
          TX packets:219313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20038480 (19.1 MiB)  TX bytes:20038480 (19.1 MiB)


=======
= lspci -v =
=======

0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [e4] #09 [4104]
        Capabilities: [a0] AGP version 2.0

0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 32
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fc000000-fdffffff
        Prefetchable memory behind bridge: e8000000-efffffff

0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 4541
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf80 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 4541
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf40 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: Intel Corp.: Unknown device 4541
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at bf20 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: Dell: Unknown device 011d
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at f4fffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] #0a [2080]

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: f6000000-fbffffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Intel Corp.: Unknown device 4541
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at bfa0 [size=16]
        Memory at 20000000 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: Dell: Unknown device 011d
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at b800 [size=256]
        I/O ports at bc40 [size=64]
        Memory at f4fff800 (32-bit, non-prefetchable) [size=512]
        Memory at f4fff400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: Conexant: Unknown device 5422
        Flags: medium devsel, IRQ 5
        I/O ports at b400 [size=256]
        I/O ports at b080 [size=128]
        Capabilities: [50] Power Management version 2

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 02) (prog-if 00 [VGA])
        Subsystem: Dell: Unknown device 011d
        Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at c000 [size=256]
        Memory at fcff0000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: [58] AGP version 2.0
        Capabilities: [50] Power Management version 2

0000:02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
        Subsystem: Dell: Unknown device 865d
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at faff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Vital Product Data
        Capabilities: [58] Message Signalled Interrupts: 64bit+ Queue=0/3 Enable-

0000:02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
        Subsystem: Dell: Unknown device 011d
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at 20001000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 20400000-207ff000 (prefetchable)
        Memory window 1: 20800000-20bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
        Subsystem: Dell: Unknown device 011d
        Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
        Memory at 20002000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: 20c00000-20fff000 (prefetchable)
        Memory window 1: 21000000-213ff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

0000:02:03.0 Network controller: Intel Corp. PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
        Subsystem: Intel Corp.: Unknown device 2565
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at fafef000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2


====================
= cat /etc/network/interfaces =
====================

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid Squirrel



auto eth0







auto eth1


===============
===============



So this is all the info you requested.  The wireless is eth1 (although I'm sure if you can read these files you already know that :) )

---

### Post by eelozano on 2005-07-21
Ok I figured it out.

Basically when using eth0...eth1 has to be disabled and when using eth1.....eth0 has to be disabled.

Is this normal?

---

### Post by varunus on 2005-07-21
Glad you got it working, but that's a little weird...On my laptop (atheros card, though) you can have both enabled.  In the GNOME networking utility (System->Administration->Networking), there's a label for "default gateway"; is it set to eth1 on your computer when you have both enabled?  Or is it set to eth0 when both are enabled?  That's all I can think of, unless programs are seeing eth0 and trying to get to the net through it instead of through eth1...

I guess you don't need to have both enabled, though...

And I'll try not to hold the Purdue-IU rivalry against you.   ;-)

---

