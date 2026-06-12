---
title: "Install Probs 7.10 on P3 PC"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by genosmm on 2008-05-19
Tried to install both 7.10 Desktop and Server on my P3 eTower 633ids and both failed.  

Install Failure Specs: 
7.10 for PC locked at init:tty3main process ended respawning.

7.10 Server made it to formatting 33% of default partitions (ext3 file). Screen message mentioned partition #1 of SCSI 1.  This PC only has std IDE hard drives.

Here are the eTower 633ids Specs: only upgrade is 512MB memory
Specifications CPU: 	Intel® Celeron® 633MHz (w/128KB L2 Cache) 
Operating System: 	Genuine Microsoft® Windows® Millennium Edition
Chipset: 	Intel® 810 chipset, 66MHz FSB
Memory: 	64MB SDRAM (1 DIMM available for upgrade up to 256MB)
Hard Drive: 	15GB HDD
Optical Drive: 	Built-in 12x Max. DVD-ROM; 3.5" 1.44MB FDD
Video: 	Intel® Direct 3D 2x AGP (shared memory)
Sound: 	Intel® 82801 AC '97 Audio
Modem: 	56K ITU v.90 PCI internal Fax/Modem
Peripherals: 	Keyboard; Mouse; Stereo Speakers
Ports/Other: 	2 USB ports (1 is on front bezel); 1 Serial; 1 Parallel; 1 Midi/Game; 2 PS/2; Audio In & Out, Microphone In; 3 Expansion slots - 2 available 

If there is an easy way for screen capture of the error screen will try to send actual error screens.

Also did a forum search and found this [http://ubuntuforums.org/search.php?searchid=41539755](http://ubuntuforums.org/search.php?searchid=41539755)  but did not find anyone having my problem.

Thanks

Gene

---

### Post by mikewhatever on 2008-05-19
64 MB of RAM is not enough to install and run Ubuntu. Xubuntu may install from an Alternate CD, but you'd probably want a lighter system.
[http://psychocats.net/ubuntu/minimal](http://psychocats.net/ubuntu/minimal)

I am not sure what's the deal with partitioning during the server install. Gparted live cd or another similar tool may work better.

---

