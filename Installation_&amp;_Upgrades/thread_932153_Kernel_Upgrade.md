---
title: "Kernel Upgrade"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by -Curtains- on 2008-09-28
I have a problematic sound card that apparently needs a special kernel fix (?) to run properly. At the moment I'm getting horrible static.

> **iucoen said:**
> This has been fixed in the kernel tree:
[http://lkml.org/lkml/2008/8/4/110](http://lkml.org/lkml/2008/8/4/110)

This problem applies to all newer nVidia HDA chips.

I've been looking around and I don't quite know what tutorial I should be looking for. Do I need to compile a custom kernel? Or is it some kind of update I can easily apply?

Thanks for any help!

---

### Post by Sef on 2008-09-28
What sound card do you have?

---

### Post by -Curtains- on 2008-09-28
Hi there,

Apparently it's a Realtek ALC1200 High Definition Audio chip. It's built into my motherboard, which is an Asus M3N78 PRO.

I've been testing the system in Windows and it works there - so it seems like it's not a hardware issue.

---

### Post by Sef on 2008-09-28
>  I've been testing the system in Windows and it works there - so it seems like it's not a hardware issue.

It would be a driver issue then.

I have an Asus mobo too.  What is your output of ```
lspci
```.  (Applications > Accessories > Terminal)

Mine is > 80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


---

### Post by -Curtains- on 2008-09-29
I just recently did a bunch of updates and attempted to compile my own custom kernel, things have changed - no I have no sound at all. lspci reports:

00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)


It was interesting to note that a lot of my motherboard wasn't recognized:
felix@Felix-Ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075c (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0751 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0760 (rev a2)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0778 (rev a1)
00:12.0 PCI bridge: nVidia Corporation Unknown device 075b (rev a1)
00:13.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:0a.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
01:0b.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0401 (rev a1)

Where to now? Reinstall and start from scratch...?

---

