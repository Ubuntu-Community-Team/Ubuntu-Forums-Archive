---
title: "DVD codecs?"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by newbreed on 2008-05-24
Hardy user looking for help on playing dvds...
I get an error: [COLOR="Red"]An error occurred.Could not read from resource[/COLOR].

Thanks for any help.


-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by Bruce M. on 2008-05-24
Check out QuickStart in my signature.

Have a nice day
Bruce

---

### Post by newbreed on 2008-05-24
Thanks... I read but could not find download like...sudo apt-get install quick start came back with nothing...



nevermind...i found thanks ;)

---

### Post by Pumalite on 2008-05-24
sudo aptitude install ubuntu-restricted-extras
Make Medibuntu part of your repos and install all the codecs:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by newbreed on 2008-05-24
spoken like true friends... but it didnt work for me, although i sure picked up a whole bunch of other codecs, and the quick start didnt help, that one reminded me of Automatrixs.... thanks for thelp but after reboot I still get same error on totem movie player...:(

could it be something on dvd drive that is missing something? it plays everything else fine..

---

### Post by Pumalite on 2008-05-24
Did you get w32codecs?

---

### Post by newbreed on 2008-05-24
yes...

"Reading state information... Done
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."


with same error:

[IMG]http://i169.photobucket.com/albums/u206/stillkill_bucket/rd.png[/IMG]

---

### Post by Pumalite on 2008-05-24
Maybe your DVD is one of the new goodies from Sony.

---

### Post by newbreed on 2008-05-24
:confused:

---

### Post by newbreed on 2008-05-25
well this morning I get this, broken pixels.. hope some one can help me today, thanks in advance

[IMG]http://i169.photobucket.com/albums/u206/stillkill_bucket/f-1.png[/IMG]

---

### Post by mdpalow on 2008-06-06
QuickStart should fix your problem, but you didn't check out the signature of the original poster who suggested it.

Look in my signature below for the link to the QuickStart website. You can download it from there and should have everything working in a couple of minutes - assuming you don't have hardware issues.

---

