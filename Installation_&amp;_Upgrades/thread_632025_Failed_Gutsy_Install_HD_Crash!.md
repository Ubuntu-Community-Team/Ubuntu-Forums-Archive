---
title: "Failed Gutsy Install HD Crash!"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by rambn on 2007-12-05
I attempted a Ubuntu Gutsy 7.10 install three times on my Gateway laptop (specs listed below).  During the first two times, I was able to boot with the liveCD and proceed normally.  The installation process completed and prompted me to re-boot.  Upon rebooting, I got the initial Ubuntu logo fine, and then a blank screen.  Also, something weird that I haven't seen before, was the HD light was burning very dimly. 

After my third installation attempt completed successfully (or so it seemed), and a reboot, the laptop simply shut down after only a few seconds.  I was able to boot up  and able to access the BIOS settings via F2, but it just shuts down shortly thereafter.  What happened?  Is it possible that these failed Ubuntu installs have damaged my HD?  I have to say that would be my worst nightmare come true.  I've been using the liveCD for about two weeks now, and had just gotten the wireless working.  

It also may be important to note that during the installation attempts, I was hooked to the internet.  HELP.  please.

Processor 	AMD Turion™ 64 Mobile Technology ML-34
Operates at 1.8 GHz | 1 MB L2 Cache
HyperTransport™ technology at up to 1600 MHz
Screen 	15.4-inch Widescreen Ultrabright WXGA TFT
Chipset 	ATI Radeon® Xpress 200M Chipset (RS482M)
Memory 	1024 MB DDR 333 MHz (2 × 512) PC2700
Expandable to 2 GB
Total Slots: 2 DDR2 Slots | Available Slots: 0 DDR2 Slots
Video 	ATI Radeon® Xpress 200M Integrated Chipset with Radeon® X300 Based Integrated Graphics
64 MB shared video memory
Audio 	AC '97 2.3 Compliant Audio
Built-in speakers
Hard Drive 	120 GB hard drive (4200 RPM)
Optical Drive 	DVD+/-RW Multi-Format Double Layer (up to 8.5 GB)

Write maximum: 8X DVD +/-R, 6X DVD-RW, 8X DVD+RW, 2X DVD-R DL, 2.4X DVD+R DL, 24X CD-R and 16X CD-RW
Read maximum: 24X CD-R/RW/ROM, 8X DVD-R/RW/ROM, 4X DVD+/-R DL, RAM
Media Reader 	4-in-1 Digital Media Manager
Secure Digital (SD), Memory Stick, Memory Stick-Pro, and Multimedia card (MMC)
Modem 	56K ITU V.92 ready Fax/Modem
Network 	10/100 Mbps built-in Ethernet
802.11g Wireless LAN (up to 54 Mbps)
SecureEasySetup™, 125 High Speed Mode
Interfaces 	

    * 4 - USB 2.0 Ports
    * 1 - VGA External Connector
    * 1 - IEEE 1394 port
    * 1 - RJ11
    * 1 - RJ45
    * Microphone In
    * Headphone / Audio Out 

Pointing Device 	Touchpad with Vertical Scroll Zone
PCMCIA 	1 - Type I or Type II; Card Bus
Battery 	6-cell Lithium-ion

---

### Post by rambn on 2007-12-05
ok, well, it seems that I can boot from the liveCD SOMETIMES.  It still crashes, but for now I've got the liveCD running.

---

### Post by khurrum1990 on 2007-12-05
Hi, I don't think Ubuntu would damage ur hard disk. Are u getting a command prompt at least when u boot up Ubuntu? If u r then log in with ur user name and password and type:
"sudo dpkg-reconfigure xserver-xorg"
Choose the vesa driver for ur vga card and configure x server with a resolution u like and reboot.
If that doesn't work then try adding the "noapic" option in grub while booting.
The weird problem I don't understand is why Ubuntu fails to load after installation when it works fine in Live cd. One more thing, when u burned ur disc image, did u make sure the cd isn't damaged and all data is intact?

If Ubuntu doesn't work for u then there r many other distros, may be u would like to try OpenSuse at:
[http://en.opensuse.org](http://en.opensuse.org)

---

### Post by rambn on 2007-12-07
Well, I've done more research since my first post.  Turns out that the ATI Radeon 200M video card drivers have issues with Ubuntu (and other Linux distros, I believe).  

I've been unable to try any of the fixes offered on the forums, but now I can't get internet access from the recovery mode (my only option, given that the GUI doesn't work).  Again, I've searched the forums, but have had even less luck that with the GUI.

I should note that the previous release of Ubuntu 2D GUI works fine, but with that distro I can't get my wireless working.  

And I agree with the previous post, I don't understand why the 2D GUI interface works with the Gutsy liveCD but not with the install.

any ideas?

---

