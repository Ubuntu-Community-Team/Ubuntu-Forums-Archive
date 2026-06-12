---
title: "[SOLVED] RAID not detected"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by Xyem on 2008-10-25
I have a pair of 500GB Maxtor drives configured in RAID1 at the BIOS level as I intend to install several systems onto them and want them all to be RAID'ed equally.

However, after booting a Hardy ( 8.04.1 ) LiveCD I find that Ubunbtu see's the drives separately, instead of as one. It would appear that nv_sata is not detecting the RAID but I do not know where to go from here..

> #lspci -v
[..snip..]
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85)
	Subsystem: Giga-byte Technology Unknown device b002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	I/O ports at 09f0 [size=8]
	I/O ports at 0bf0 [size=4]
	I/O ports at 0970 [size=8]
	I/O ports at 0b70 [size=4]
	I/O ports at e600 [size=16]
	Memory at e2005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping

00:0f.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85)
	Subsystem: Giga-byte Technology Unknown device b002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
	I/O ports at 09e0 [size=8]
	I/O ports at 0be0 [size=4]
	I/O ports at 0960 [size=8]
	I/O ports at 0b60 [size=4]
	I/O ports at eb00 [size=16]
	Memory at e2006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping
[..snip..]


I thought the entire point of RAID at the BIOS level was to remove the need for the operating system to be aware it was RAID'ed..

---

### Post by Xyem on 2008-10-25
Some parts annoying, other parts great. I found the answer after a couple of minutes posting here. Some people here must be psychically sending me the answers.

This time, the answer was 'dmraid'.

The HOWTO that helped me can be found here [on this very forum.]("http://ubuntuforums.org/showthread.php?t=2557")

In short:
( Enable universe/multiverse )
sudo aptitude install dmraid
sudo dmraid -ay -v

---

### Post by rev_b on 2008-10-26
Thanks for sharing, I'll try it now, as I'm having exactly the same problem trying to install ubuntu on my new system with 2 320 Gb sata disks in raid 0. 8.04 and 8.10 rc see separate disks.

Should't this be included on the installation disk??

---

### Post by Xyem on 2008-10-26
Quite possibly, apparently dmraid is in Intrepid's 'main' repository so there might be more 'click and go' support for it in that release.

I'm having problems actually installing Ubuntu to the RAID ( I get various errors depending on how I go about it ). I'm currently trying to follow [this HOWTO]("http://bbossola.wordpress.com/2008/03/07/dmraid-on-ubuntu-with-sata-fakeraid/").

I'll let you know how it goes.

---

### Post by Xyem on 2008-10-27
I followed the HOWTO up to the point of manually installing things then after a bit of messing with the GUI partitioner to get it to use the right partitions, I managed to get it to install.

GRUB failed so I installed that manually, but on reboot I got GRUB error 22. At this point, I gave up and destroyed the array and I am now using the drives separately.

I do have 2 other drives that I can use so I can plug them in and try to get an install working if you still need help rev_b. I'd probably follow the HOWTO more strictly.. just let me know and I'll take another bash at it.

OAT: Funnily enough, I discovered a "bug" in the Windows XP installer where if you reboot during the formatting, the installer will not start again ( after 'Setup is analysing your setup' or whatever it is just a black screen ). It required me to boot Linux and 'dd' the first few megabytes of the drives.

---

