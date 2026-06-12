---
title: "Ubuntu on a HP Pavilion DV2845se"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by Poindexter on 2008-07-16
I wanted to know if anyone was able to install Ubuntu on a HP Pavilion DV2845se successfully? If so, were there any problems?

---

### Post by KC_Ransom on 2008-07-16
I recently installed Ubuntu on an HP Kayak XU with 450 Mhz processor. I wanted to use it for web development, and it was a bit slow for me. I then partitioned the drive and installed Xubuntu and then LAMPP. Xubuntu is much faster on this dinosaur.
The only real problems are:
1) I have an old 17-inch VGA monitor and the 60 Hz refresh rate is giving me a headache. Solution: get a better monitor or a peripherals switchbox so I can use the good one I have for my wintel box
2) there is no sound. Solution, unknown. I don't care too much, as this box is for webdev.

I don't know if a pavilion is older than what I'm using. What are the specs on the box, and what are you intending to use it for?
[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)
:lolflag:
KC

---

### Post by Poindexter on 2008-07-16
System Type
    Notebook
Built-in Devices
    Stereo speakers, Wireless LAN antenna
Width
    13.1 in
Depth
    9.3 in
Height
    1.5 in
Weight
    5.3 lbs
Localization
    English / United States
Notebook type
    Thin-and-light (4-6 lbs.), Budget
Screen type
    Wide-screen, High-gloss/Anti-glare screen
Wireless capabilities
    802.11b, 802.11g

Processor

Processor
    AMD Turion 64 X2 mobile technology TL-62 / 2.1 GHz
Multi-Core processor technology
    Dual-Core
64-bit processor
    Yes
Data bus speed
    800 MHz

Cache Memory

Type
    L2 cache
Cache size
    1 MB

RAM

Installed Size
    4 GB / 4 GB (max)
Technology
    DDR II SDRAM
RAM form factor
    SO DIMM 200-pin
RAM configuration features
    2 x 2 GB

Storage Controller

Storage controller type
    Serial ATA
Storage Controller / Serial ATA Interface
    Serial ATA-150

Storage

Floppy Drive
    None
Hard Drive
    250 GB - Serial ATA-150 - 5400 rpm
Storage Removable
    None
Hard drive type
    Portable

Optical Storage

Type
    DVD±RW (±R DL) / DVD-RAM
Disc Labeling Technology
    LightScribe Technology

Optical Storage (2nd)

2nd optical storage type
    None

Card Reader

Card reader type
    5 in 1 card reader
Supported flash memory cards
    Memory Stick, MultiMediaCard, SD Memory Card, XD-Picture Card, Memory Stick Pro

Display

Display Type
    14.1 in TFT active matrix
Max Resolution
    1280 x 800 ( WXGA )
Widescreen Display
    Yes
Features
    BrightView

Video

Graphics Processor / Vendor
    NVIDIA GeForce 7150M Shared video memory (UMA)
Total Available Graphics Memory
    1071 MB

Audio

Audio output type
    Sound card
Audio Output Features
    Altec Lansing speakers
Audio Input
    Microphone

Notebook Camera

Camera Type
    Integrated

Multimedia Functionality

TV Tuner Type
    None

Input Device(s)

Input device type
    Keyboard, Touchpad, QuickPlay

Telecom

Modem
    Fax / modem
Max transfer rate
    56 Kbps

Networking

Networking
    Network adapter
Networking / Wireless LAN Supported
    Yes
Data link protocol
    Ethernet, IEEE 802.11b, IEEE 802.11g, Fast Ethernet
Networking standards
    IEEE 802.11b, IEEE 802.11g

Expansion / Connectivity

Expansion Slots Total (Free)
    2 ( 0 ) x Memory - SO DIMM 200-pin, 1 ( 1 ) x ExpressCard/54
Interfaces
    3 x Hi-Speed USB - 4 pin USB Type A, 2 x Headphones - Output - Mini-phone stereo 3.5 mm, 1 x Microphone - Input - Mini-phone 3.5 mm, 1 x Display / video - VGA - 15 pin HD D-Sub (HD-15), 1 x Display / video - S-video output, 1 x Modem - Phone line - RJ-11, 1 x Network - Ethernet 10Base-T/100Base-TX - RJ-45, 1 x Docking / port replicator, 1 x IEEE 1394 (FireWire) - 4 pin FireWire, 1 x Remote control - Infrared

Miscellaneous

Included Accessories
    Remote control

Power

Power device form factor
    External

Operating System / Software

OS Provided
    Microsoft Windows Vista Home Premium 64-bit Edition

---

### Post by KC_Ransom on 2008-07-16
Gadzooks, this is one heck of a machine you have here! If I can get Xubuntu to work on my old clunker, you should have **no** troubles with this laptop.
Now, I picked Xubuntu because it doesn't use Gnome. I don't think Gnome should be an issue for you. 
The only thing to be wary of is keeping Vista during the install. I  suggest researching the best approach (partition first through Vista, then install?).
If you don't have the original Vista Cd's, then do a good backup. I use Maxtor onetouch on my laptop.

Good luck...let us know how it goes.

KC

---

### Post by Poindexter on 2008-07-20
Ok I installed ubunut on my HP Pavilion laptop as a dual boot gave it about 15 gigs allocated. Everything seems to be running smooth so far. Now how do I go about getting the packages installed on here? One minor thing is that my wireless NIC is not being detected how can I get the driver for it?

---

### Post by Ivy_ on 2008-09-22
I have the exact same computer, and have problems with screen resolution and with wifi.

---

### Post by Cazey on 2008-10-21
> **Ivy_ said:**
> I have the exact same computer, and have problems with screen resolution and with wifi.

I have everything on mine up and running, wifi, webcam, graphics all working great!

for the graphics [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
and for the wifi install ndiswrapper! and it'll **** u right up :popcorn:

---

### Post by jNorthern on 2009-01-03
I've had my dv2845se up and running with Linux for almost a year now.  (Dual boot intrepid/osx)  Works wonderfully--except the osx part. I was able to get compiz/beryl/awn running smoothly along with vmware, ie4linux...and every other bell and whistle Let me know if you need any help with the install!

---

