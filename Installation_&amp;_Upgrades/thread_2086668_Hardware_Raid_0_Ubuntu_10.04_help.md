---
title: "Hardware Raid 0 Ubuntu 10.04 help"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by Acer8888 on 2012-11-21
Hello, i have been using Ubuntu 10.04 server for about 2 months. I have some knowledge of ubuntu but it is still very limited. I am looking to setup a new server hard drive configuration. And would like a little input on what im trying to do.
 
What i have is a 60Gig SSD running the OS, I want to put in place 2 2TB harddrives in a Hardware RAID0. Im not concerned at losing data i mainly just want the Raid for performance.
 
I am using a XFX nForce 680i LT SLI Socket 775 Motherboard, i am aware of how to setup the raid in BIOS, what im not sure about is whats the configuration needed for Ubuntu? Will it automatically pick up the 4TB raid or is there steps i need to take first? I have heard i need to install a alternate Ubuntu installation, is that only if the OS is installed on the RAID? Has anyone used this motherboard or one similar in a RAID with Ubuntu?
 
Thank you in advanced for any input!

---

### Post by darkod on 2012-11-21
It is correct that the Alternate CD needs to be used for raid installations because it has better raid support, but that is substitute for the standard Desktop CD (or Live CD). It installs the desktop OS.

For a server installation, you use the Server CD which has built-in raid support.

Another alternative of bios raid (fakeraid) is to use software raid. In that case you don't configure anything in bios, you leave the sata mode to AHCI (not RAID). The raid is configured by the ubuntu OS. In many cases the software raid can work better than the fakeraid since the fakeraid does not have a real dedicated hardware raid card anyway. It does it with software too.

Those are the two options for raid.

---

