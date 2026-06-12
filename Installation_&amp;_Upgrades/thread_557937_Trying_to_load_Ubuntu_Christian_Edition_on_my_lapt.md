---
title: "Trying to load Ubuntu Christian Edition on my laptop"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by mcar2185 on 2007-09-23
I have a Compaq Presario VN6305 laptop that I'm trying to load Ubuntu Christian Edition on. I boot using the Live CD and before it can boot up Ubuntu, I get a slew of errors. The one that I notice is something like "Bios error". Anyone else had this problem? What can I do to remedy it? I really want to put Ubuntu on my computer as I hate Vista.

---

### Post by Pumalite on 2007-09-23
Do md5sum on you iso, burn at 4x, check for CD corruption after burn and before install, burn as 'Image': [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)
Post your specs. You might need the Alternate CD.

---

### Post by mcar2185 on 2007-09-23
Thanks. I did all of that (the slowest I could burn ISO through Nero was 10x) and it still froze. My specs:

1.6 GHz AMD Turion&#8482; 64 X2 Dual-Core Mobile Technology TL-50
256KB+256KB L2 Cache
1024MB DDR2 System Memory (2 Dimm)
NVIDIA GeForce Go 6150 (UMA)
100GB (5400RPM) Hard Drive (SATA)
Super Multi 8X DVD±R/RW with Double Layer Support
15.4" WXGA High-Definition Brightview Widescreen (1280 X 800) Display
High speed 56k modem
Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
802.11b/g WLAN
Imprint Finish & Integrated Microphone
Altec Lansing
101-key compatible & 1 Quick Launch Button - HP Quick Play DVD
Touch Pad with On/Off button and dedicated vertical and horizontal Scroll Up/Down pad
PC Card Slots 	

    * 1 ExpressCard/54 Slot (also supports ExpressCard/34)

External Ports 	

    * 5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards
    * 3 Universal Serial Bus (USB) 2.0
    * 1 Headphone out
    * 1 microphone-in
    * 1 VGA (15-pin)
    * 1 TV-Out (S-video)
    * 1 RJ-11 (modem)
    * 1 RJ -45 (LAN)
    * 1 notebook expansion port 3
    * 1 IEEE 1394 Firewire (4-pin)
    * 1 Consumer IR

-------------------------------------

The error I am getting is "bug: PCI BIOS". It then freezes up.

---

### Post by Pumalite on 2007-09-23
Your hardware is fine, but go with the Alternate CD due to the errors.

---

### Post by mcar2185 on 2007-09-23
OK, good. One quick question: How do I go about partitioning so that I can dual-boot Vista and Ubuntu (on the same HD) and still keep all of my documents? I know the Alternate CD is a bit more confusing as far as that is concerned, so I want to make sure I do it right.

---

### Post by Pumalite on 2007-09-23
Partition with Vista's partitioner (somewhere in Administration, hard drives). Then install Ubuntu>Manual. Set 10 GB for '/', 500 MB for /swap, and the rest for /home.
Post back with any problems.

---

### Post by mcar2185 on 2007-09-23
OK, how do I set up the /swap part? Do I use logical or primary? What about the others?

---

### Post by Pumalite on 2007-09-23
Windows needs a primary partition. Ubuntu is happy in logical and extended. Swap uses it's own format. You are allowed four primary partitions only.

---

### Post by mcar2185 on 2007-09-23
Got it to install, but now it won't boot up. It goes black right after the initial Ubuntu screen. What now?

From what I gather, you need to use the noapic command, and I'm trying to do that, but I get an error when accessing the menu.list file that it cannot be displayed.

---

### Post by Pumalite on 2007-09-23
You probably need to configure your xserver.
Ctrl+Alt+F1 to get a command line. At the command line:
sudo dpkg-reconfigure xserver-xorg, choose most defaults, choose 'vesa' as the driver, then: startx

---

