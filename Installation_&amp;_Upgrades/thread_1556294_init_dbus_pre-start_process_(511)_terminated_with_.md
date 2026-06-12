---
title: "init: dbus pre-start process (511) terminated with a status 1"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by w2vy on 2010-08-19
I had been having problems with every LiveCD after 8.04.1 I tried both xubuntu and ubuntu (same internals, same results)

I ended up installing xubuntu 10.4 using the text mode installer.

The system basically works, I can not get gdm running.

dbus fails as noted above. I found [launchpad bug #446971]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/446971") and tried some of the work arounds with no success.

The system is an old eMachines T1120

```
CPU: Intel Celeron Processor 1.20GHz (w/256KB)
Operating System: Genuine Microsoft Windows XP Home Edition
Chipset: Intel 810e chipset
Memory: 512MB SDRAM (PC133)
Hard Drive: 40GB HDD
Optical Drive: Built-in 16x Max. CD-RW Drive; 3.5&#8243; 1.44MB FDD
Video: Intel Direct AGP 3D (810e shared)
Sound: AC ’97 Audio
Modem: 56K ITU v.92-ready Fax/Modem
Peripherals: Keyboard, Mouse, Stereo Speakers
Ports/Other: 3 USB ports (1 on front), 1 Serial, 1 Parallel, 2 PS/2, Audio In & Out; 1 Midi/Game on front, Mic-In & Head Phone jack on front 
```

I am booting with i915.modeset=1 (and I also tried 0 for fun)

lspci

```
tom@w2vy:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
01:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
01:0d.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
tom@w2vy:~$ 
```

Any suggestions?

Tom
ps. this thread has morphed from [this one]("http://ubuntuforums.org/showthread.php?t=1551849") the focus changed dramatically so I figured a new thread was in order so that future searchs may be more useful

---

### Post by Bex2 on 2010-10-01
Having what appears to be the same problem with newly-installed 10.04.1 Server on a new system.  There are no files in /var/run/dbus.

---

