---
title: "Help! Abandoned Ati Video Card Attacks!"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by theaceoffire on 2007-05-08
Ok, this took me FOREVER to figure out, but for a LONG time no linux program would run. Gparted, DSL, OpenSUSE, Ubuntu, you name it, it would not start.

I got errors such as:
Gparted 3.4-6:
Code:90 30 01 00 00 81 c2 88 02 00 00 39 d0 74 08 89 c8 5b e9 df 7f 02 00 8d 04 (etc)
EIP:[&lt;c010cbe&gt;] kmap_atomic +0x4b/0x75 SS:ESP 0068:dfca1d48
Kernal Panic Attempting to kill Init

Ubuntu [failed loading hardware drivers]

openSUSE booted, but I got the error pretty quick:
CD:///?devices=/dev/hda,/dev/hdb
Unknown Error: Unable to copy media directory to /var/tmp/TmpDir.RK1HuM/Media

^_^ Anywho, I have a Pentium 4, 3.02 Ghz Processor, 1.5 GB of Ram, lots of storage, and (here is the problem), an ATI Radeon Stealth Video Card 9250. 

If you have this error, I heard lots of ideas:> 
1. If you don't have a floppy drive (I don't), disable it.
2. Check the md5 sum (reasonable, but not my issue) of the linux disc your trying to boot.
3. Check the disc (Ubuntu and openSUSE have this of course)
4. Check the Ram/Disc integrity (Thank Goodness this wasn't my issue)
5. Unplug everything not needed (Didn't help, did it anywho)
6. Someone mentioned that it might be the IDE controller, not sure.
7. Upgrade your BIOS as far as you can from the motherboard manufacturer. 

However, the only way I was able to boot linux was by going into the bios and changing the default graphics manager thingie to motherboard instead of pci, making linux IGNORE my video card.

O.o of course now I have an issue: I have a working copy of Ubuntu, but it wont boot if I use my video card (not in safe mode either)...

^_^ Anyone have any ideas for me to try? I wanna leave XP behind me...

Oh, and IN ubuntu, it won't let me install the restricted drivers cause it thinks I don't have any hardware that needs it.

O.o here is some more of my system info if it helps anyone...
> 
System Info
Internal Units:~~~~~~~~~~~~~~~~~~~~~
HP Pavilion a1120n (ACPI Uniprocessor PC)
Intel Pentium 4 Processor, 519K, 3.06GHz
200GB 7200RPM Serial ATA drive
1536 MB PC2 3200 DDR2 SDRAM
LightScribe DVD+-Writer/CD-Writer Disk Drive
CDRom Disk Drive
Radeon 9250 Stealth Video Card
AverMedia AVerTV Tuner M150 (Philips 1236 MK3)
Agere Systems PCI Soft Modem
Generic USB Readers (USB Device):CF,MS,SD,SM
1394 Net Adapter
Realtek RTL8139 (Net Adapter)
	{810x FamilyFastEthernet NIC}
PCIx3, USBx7, FireWirex3


Hope someone can help a noob out!


################EDIT#####################
See thread here for how I fixed this:
[http://ubuntuforums.org/showthread.php?t=436930](http://ubuntuforums.org/showthread.php?t=436930)

---

