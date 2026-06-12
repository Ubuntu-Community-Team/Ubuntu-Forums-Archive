---
title: "Install headaches on Toshiba Satellite Pro L510"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2010-10-29
Hi all,

Today I bought a Toshiba Satellite Pro L510 and after much screwing around I have Ubuntu installed ... kinda.

Installing Ubuntu is generally a breeze and I have three machines running 8.04 pretty much rock solid unless I fiddle with 'em, but; I download and boot from a 10.04 LTS cd and gets to the new purpley splash with a couple of icons down the bottom, then goes into endless full-screen terminal scrolling and the computer heats up.

So I tried 8.04. Not much different. I try 10.10; same as 10.04 LTS. So I try the alternate installer rather than desktop but that crashes too. I finally find a website suggesting to run the alternate installer, hit F4 and choose 'failsafe graphics' (which wasn't there for me) and then F6 and select everything but 'Free Software Only'. Hey, worked and I get through the text based installer no problem, restart and I'm looking at a grub2 menu and can select Windows 7 or Ubuntu. Cool.

So I select Ubuntu but goes to a text based, command line Ubuntu. Hasn't loaded a desktop. I try to 'sudo apt-get install ubuntu-desktop' from the CD but after much scrolling tells me not there. It is telling me I have umpteen updates I should get and asking me to insert the CD, which is fine as the machine is not online, but then can't find what it's looking for. 

So I've gotten this far. My router is not set as a DHCP server; all machines have static IPs which is why this new one is not online. Would the simple answer be to plug it directly into the internet gateway router and do the updates from there, ubuntu-desktop included?

Tnx in advance ... :)

---

### Post by Bucky Ball on 2010-10-29
BTW, these are the specs and I read somewhere that the i3 processor can be a bit dicky with Ubuntu:

Intel® Core&#8482; i3-330M Processor (2.13GHz, 1066MHz FSB, 3MB L2 cache)   
14&#8221; High Definition LED backlit display   
ATI Radeon HD4570 dedicated graphics. Hybrid and switchable with integrated Intel HM55 chipset.   (not in front of the machine but actually a HD5175 from memory - slightly faster)
4GB RAM   
320GB HDD   (5400RPM)
Express card slot   
HDMI Out   
Bluetooth   
Superfast WiFi N   
eSATA/USB Combo   
Windows 7 Home Premium   
Intel® High Definition Audio Sound   
Dual-layer super multi DVD drive

---

