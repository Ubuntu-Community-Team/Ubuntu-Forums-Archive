---
title: "ubuntu 7.10 won't install on asus m3a mb w/ amd64 phenom cpu"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by franklovecchio on 2008-01-04
The Ubuntu amd64 desktop install cd loads up - I select the first option, start or install Ubuntu - the splash screen appears with the nice little logo and loading bar - then the computer freezes.  Sometimes the orange loading bar goes quickly across the screen for a second, sometimes the orange loading bar doesn't appear at all.  Either way, FREEZE.

I've tried using the "hdep=disable" (or something along those lines, i forget now) in the boot options, but that didn't work.  I also disabled the splash screen to see if I could get an error message of some sort - when I did this, the last outputted line is "mounting root file system... ..." and the nothing.

I have also tried a copy of Windows xp64 Professional (pirated, of course), but that seems to keep freezing the computer and I can not get a full install to happen.  It will boot up the windows splash screen, and then try and continue the install, but it always crunks out i.e. restarts.

I did a RAM check using the ubuntu cd, everything checks out fine.  Is this a HDD problem?  SOMEONE PLEASE HELP!!! All the hardware is new.  

Here are the specs:

Motherboard:  ASUS M3A AM2+/AM2 AMD 770 ATX AMD
Brand-ASUS
Model-M3A
CPU Socket Type-AM2+/AM2
CPU Type-Phenom FX / Phenom / Athlon 64FX / Athlon 64X2
FSB-2600MHz Hyper Transport (5200 MT/s)
Chipsets
North Bridge-AMD 770
South Bridge-ATI SB600

CPU:  AMD Phenom 9500 Agena 2.2GHz 4 x 512KB L2 Cache 2MB L3 Cache
Socket AM2+ 95W Quad-Core Processor
Brand-AMD
Processors Type-Desktop
Series-Phenom 9000 Series
Model-HD9500WCGDBOX
CPU Socket Type-Socket AM2+
Core-Agena
Multi-Core-Quad-Core
Name-Phenom 9500

RAM:  CORSAIR Dominator 4GB(4 x 1GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2
8500) Quad Kit Desktop Memory
Brand-CORSAIR
Series-Dominator
Model-QUAD2X4096-8500C5DF
Type-240-Pin DDR2 SDRAM
Capacity-4GB(4 x 1GB)
Speed-DDR2 1066 (PC2 8500)
Cas Latency-5
Timing  5-5-5-15
Voltage-2.1V

Video Card:  PNY VCQFX1500-PCIE-PB-V Quadro FX1500 256MB 256-bit GDDR3
PCI Express x16 Video Card
Brand-PNY
Model-VCQFX1500-PCIE-PB-V
Interface-PCI Express x16
Chipset Manufacturer-NVIDIA
GPU-Quadro FX1500
PixelPipelines-12
Memory Size-256MB
Memory Interface-256-bit
Memory Type-GDDR3
DirectX-DirectX 9
OpenGL-OpenGL 2.0
DVI-2
TV-Out-HDTV / S-Video Out
VIVO-No

Power Supply:  XCLIO GREATPOWER X14S4P4 700W ATX12V 700W Power Supply 100 - 240V
Brand-XCLIO
Model-X14S4P4 700W
Series-GREATPOWER
Type-ATX12V
Maximum Power-700W
Fans-14cm ball bearing fan
PFC-Active
Main Connector-20+4Pin
+12V Rails -4
PCI-E Connectors-2 x 6Pin
NVIDIA SLI Support-NVIDIA SLI Certified

Hard Drive:  Western Digital Caviar GP WD10EACS 1TB 5400 to 7200 RPM 
Brand-Western Digital
Series-Caviar GP
Model-WD10EACS
Interface-SATA 3.0Gb/s
Capacity-1TB
RPM-5400 to 7200 RPM
Cache-16MB
Average Seek Time-8.9ms
Average Latency-5.6ms

---

### Post by yetanothersteve on 2008-01-06
I saw a write up at [phoronix.com]("http://www.phoronix.com/scan.php?page=article&item=961&num=1") and more notes in their forums about their Ubuntu + Phenom experience.

Please do post a reply as to the outcome of your situation because I was thinking of buying this motherboard.

---

### Post by jiemeb on 2008-01-08
I have a similar problem. But I' 've try to install 7.10 on my asrock HD ready with Atlhon Dual core. and after put phenom processor. Ubuntu try to start and when the process HALD is starting system freeze. If you comment the HALD script. Ubuntu start normaly but network is not working :-(.

Perhaps a bug in hald program or some over called by HALD.

I made a test whith windows and this system works normaly but it is not my target :-(

If some body have an iea !

Slt
JM

---

### Post by savagex on 2008-01-10
On my M3A Ubuntu 7.10 amd64 did install without any problems (using an Athlon 64 X2 5200+ processor). However, when trying to copy over data from my old rig with

tar czf - . | ssh user@newrig "cd /mnt/data && tar xzfv -" 

Following things happened:

First try: Logged into my old machine via ssh (in a gnome terminal), issued the statement above, complete system freeze after like 10 seconds. After a hard reset the network device just wouldn't retrieve a new IP via DHCP. I had to power down the machine (including flipping the power switch on the power supply) and restart to make the network interface work again. I assume some wake-on-LAN thingie may interfere there.

Second try: Same procedure as above, this time it worked for some minutes. Went away to do others things. When I came back the gnome terminal was gone, the copy procedure was not finished (most files not on the new rig) and I had a very slight graphical corruption at one place of the screen (brand new Radeon 3850 here, no fitting driver, I assume perhaps the vesa driver is responsible).

Third try: This time on an old fashioned text console (with X running in the background, though). Worked for some seconds, then the output from tar was replaced with a system error message which may or may not have been a kernel panic (the message was too long to fit into the screen - the rest I could read contained buzzwords like "inode" etc. - and yes, after reboot I found one filesystem to be wrecked).

I did a shutdown and went to bed, slightly frustrated. I'll try to recover some log files and hope it contains something useful.

Suspects for this trouble:

 - the network interface. Driver trouble? jiemeb's observations may give credence to this.
 - perhaps the AMD 7xx chipsets need some special attention from the kernel?
 - perhaps some BIOS issue? Did flash a beta BIOS Asus provides to make the BIOS correctly identify the new 65nm G2 Athlon stepping.
 - Defect RAM? Have to run memtest.
 - Driver issue with the storage controller? I configured the BIOS to use the AHCI mode instead of the (default) IDE mode. Perhaps I should reverse.
 - Faulty mainboard/other components?
 - Design issues with the M3A itself?


Eeeeeek.


Edit: Aha. I may be struck by a bug in the atl1 driver for atheros gigabit interfaces:

[http://atl1.sourceforge.net/](http://atl1.sourceforge.net/)

> 2. There is a bug in the atl1 driver that results in a kernel hang or crash (oops) under heavy network load IF AND ONLY IF you have 4GB or more RAM in your system. This happens because of an L1 hardware design issue that is exposed by the atl1 driver. If you encounter this problem, modify your kernel's boot line and add this kernel parameter: mem=3900M. A fix has been added to the 2.6.23 kernel.

Yup, I have 4Gig of RAM.

---

### Post by NemesisUK on 2008-01-16
When I tried to install gutsy when it tries to install a kernel I get a message stating it cant find a kernel suitable for my hardware and the installation fails. I may give hurd a go and see if thats any better.

---

### Post by notbuu on 2008-01-20
hello!

i am going to buy an asus m3a board in the near future (the m3a32-mvp is realy expensive) for an amd 64 x2 6000+ processor with 2 gb of ram.

will this configuration work? i saw that there is this 4 gb bug and the problem with phenom cpus. are there any other issues?

thank you for your informations!

kind regards,

notbuu

---

### Post by Malakai on 2008-01-25
The problem all along was likely the atl1 driver. Been trying to figure out how to install gentoo with network from the getgo on my new 4200+ and asus m3a. Solution is the gutsy livecd doing a gentoo install via terminal, then setting up and booting into a new kernel with fixed drivers on first boot.

Of course I only have 2gigs of ram so I won't hit that particular bug, but the gentoo cd's kernel has no atl1 at all =)

Good luck all. Love your forum here, I hit it up often for info. I just cant part with my source based disto after getting used to it <3


By the way the M3A is a fantastic mobo, I recommend it to all, despite the driver trouble with the ethernet which isnt the fault of the board at all. It overclocks like a dream, and keeps nice and cool. Do yourself a favor and scrape the nasty thermal gunk off the northbridge chip with a razor and reapply it proper with some arctic silver 5. Not that it got super hot before, but with real thermal grease and not that nasty goop it stays nice and cool =)

4200+ brisbane at 2800mhz stock voltage and climbing..

---

### Post by notbuu on 2008-01-26
thank you for you informations!

summary:
it should be no problem to install 7.10 on the m3a board? right?
but there is a bug with 4gb ram setups where the network interface stops working? right?
if i used 2 gb ram i wouldn't have any problems? right?

one final question:
could you tell me if the lmsensor features are working?

would you like to run the commands "sudo sensors-detect" and "sudo sensors" an post the output here?

thanks a lot

kind regards

notbuu

---

### Post by ShamusPatt on 2008-01-28
I can confirm that Ubuntu 7.10 installs and runs on the M34A32-MVP Deluxe motherboard. I have the same board in a system I put together on the weekend (lots of fun, that). The specs are similar. I'm using a Phenom 9600 CPU. I do have "only" 2GB RAM (Patriot DDR3 / 1066). It's a different graphics card (PowerColor HD3850). 

I had no real issues with the install. I used the x64 Desktop Install ISO from an Ubuntu mirror.

As to lm-sensors, no, it doesn't work. Apparently it's not seeing the AMD thermal sensors (which has me a bit concerned as I'm not sure how well the cooling is going to work in this case, an NZXT Duet which is pretty small for all of this hardware).

---

### Post by notbuu on 2008-01-29
thank you for your information!

in this thread we discuss the m3a mainbord with amd 770 chipset. not the m3a32.

anyone else who have informations about this mainboard. maybe lm-sensors?

regards

---

