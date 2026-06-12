---
title: "Need help configuring system to make it faster"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by invincible_king on 2007-12-23
Hi guys, i have an old desktop, pentium III 500 Mhz, 384 MB ram, 40 GB hard disk, what is the best light weight distro would be best suited for this system, i would work on photo editing, video editing, web pages and stuff like that, i am not going to host the website on this machine. also, i work on java, C, C++. i would like to make the best use of this system. i have already installed ubuntu 7.10 on this system, and the system is kinda slow, and the browser ( mozilla firefox) is really slow, here is the system info

shashi@shashi-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e4000000-e5ffffff

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at e000 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

00:09.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
        Subsystem: D-Link System Inc DFE-530TX+ 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at e400 [size=256]
        Memory at e6000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: Trident Microsystems 3DImage 9750 (rev f3) (prog-if 00 [VGA])
        Subsystem: Trident Microsystems 3DImage 9750
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at e5400000 (32-bit, non-prefetchable) [size=4M]
        Memory at e5800000 (32-bit, non-prefetchable) [size=128K]
        Memory at e5000000 (32-bit, non-prefetchable) [size=4M]
        Expansion ROM at e4000000 [disabled] [size=64K]

shashi@shashi-desktop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
        Flags: bus master, medium devsel, latency 64
        Memory at e0000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: e4000000-e5ffffff

00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 64
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at f000 [size=16]

00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at e000 [size=32]

00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

00:09.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
        Subsystem: D-Link System Inc DFE-530TX+ 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at e400 [size=256]
        Memory at e6000000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: Trident Microsystems 3DImage 9750 (rev f3) (prog-if 00 [VGA])
        Subsystem: Trident Microsystems 3DImage 9750
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at e5400000 (32-bit, non-prefetchable) [size=4M]
        Memory at e5800000 (32-bit, non-prefetchable) [size=128K]
        Memory at e5000000 (32-bit, non-prefetchable) [size=4M]
        Expansion ROM at e4000000 [disabled] [size=64K]

shashi@shashi-desktop:~$ cat /proc/meminfo
MemTotal:       385860 kB
MemFree:         11152 kB
Buffers:          8908 kB
Cached:         125404 kB
SwapCached:       2192 kB
Active:         296552 kB
Inactive:        56884 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:       385860 kB
LowFree:         11152 kB
SwapTotal:     1124508 kB
SwapFree:      1089844 kB
Dirty:              88 kB
Writeback:           0 kB
AnonPages:      216972 kB
Mapped:          68180 kB
Slab:            12936 kB
SReclaimable:     6516 kB
SUnreclaim:       6420 kB
PageTables:       1880 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   1317436 kB
Committed_AS:   602084 kB
VmallocTotal:   638968 kB
VmallocUsed:      3176 kB
VmallocChunk:   635384 kB


please help me configure the system to make the best use of it.

Thanks and Regards
Shashi

---

### Post by oldsoundguy on 2007-12-23
No matter what you try and do, a 500 meg PIII running an fsb of 66mhz with 384meg of ram is NOT going to go fast .. especially with an ON BOARD video eating some of that memory and processor speed.  Photo and video processing is memory intensive stuff.  Time to consider making that your back up computer and get a newer one.
More memory MIGHT help .. but there are the above restrictions that really mess you up.(your current computer can not keep up with high speed dial-up, yet alone broadband!)

Even going with a stripped down kernel to cut down on loading will not speed that machine up appreciably.

Sorry!

---

### Post by invincible_king on 2007-12-23
Thanks buddy, i understand all of that you said.... but i want to make some use out of this machine, i dont want to discard this machine, i do have my laptop that is in very good condition and i love working on it. but when i get back home i prefer to work on desktop , laptop makes me very lazy... , is there anything i could do on this desktop!!!

---

### Post by oldsoundguy on 2007-12-23
check your motherboard manual .. you may be able to change to a faster (not by much, though) processor .. and there is the point of adding memory.  For photo work you NEVER have enough memory (layers eat memory!)  (my photo processing machine runs 2gb and it STILL  takes time with a 533fsb and a hyperthreaded 3.06 processor!)

---

### Post by richardjennings on 2007-12-23
xubuntu might be your best bet

---

### Post by jerrylamos on 2007-12-23
I've tried a number of linux's on older hardware and keep ending up using Xubuntu.  Seems to use less cpu cycles and less memory.  Ubuntu with Gnome soaks up more cpu doing the same thing, noticeable since I have 2 machines side by side.

Jerry

---

### Post by mmb1 on 2007-12-23
If you're going to go ahead and try to use it, I reccomend xubuntu, although you might be interested in fluxbuntu as well.

---

### Post by invincible_king on 2007-12-24
thanxs guys... am gonna try xubuntu.... will install it straightaway!!!

---

### Post by pointone on 2007-12-24
Fluxbuntu is the most lightweight of the 'buntu's, but Puppy Linux or DSL are even less resource-intensive...

---

### Post by Pumalite on 2007-12-24
I would go with the Xubuntu Feisty Alternate CD if you still can get it:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
Xubuntu Gutsy uses more memory and with that RAM you cannot boot a Live CD unless you make a 500 MB /swap partition ahead of time.

---

### Post by K.Mandla on 2007-12-24
You might take a look at this thread. ...

[http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

And as a second resort, I have a collection of speed tweaks for Gutsy on my blog. 

[http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/](http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/)

---

