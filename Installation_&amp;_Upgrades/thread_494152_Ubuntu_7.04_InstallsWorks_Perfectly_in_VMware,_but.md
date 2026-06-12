---
title: "Ubuntu 7.04 Installs/Works Perfectly in VMware, but not on a Physical Drive?"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by maya923 on 2007-07-06
Hello all!

I'm wondering if anyone has come across this issue at all.  I have VMware WorkStation ACE Edition v6.0.0 build 45731 installed my PC.  I downloaded and installed Ubuntu 7.04 into a virtual machine, and everything works perfectly off the bat.  However, if I install Ubuntu 7.04 onto an actual physical SATA hard disk, I get video issues and my sound card does not work at all.

I'm using an ATI X1650 video card, and my sound card is the Creative X-Fi Platinum.

I already can get video working correctly; that's not a problem.  However, I know about the issues with the X-Fi series of sound cards not being supported in Linux.  What baffles me is when I check the Hardware Manager in the virtual machine, it uses the drivers for the Ensoniq ES1371 and Ensoniq SoundScape.  I have attempted to install those in my physical disk installation of Ubuntu, but to much avail, nothing works.

Has anyone gone through a similar situation? My PC specs are as follows:

Intel® Core 2 Duo E6700 Conroe Processor 2.67GHz, 1066FSB, LGA775, 4MB Cache
Gigabyte GA-965P-DQ6 P965 Express Core 2 Extreme/Core 2 Duo 1066FSB LGA775 DDR2 ATX Motherboard w/Audio, Gigabit LAN, Serial ATA
Corsair TWIN2X2048-6400 2GB Kit DDR2-800 XMS2-6400 Xtreme Performance Memory Retail
Western Digital Raptor 74GB 10,000rpm SATA
Hitachi Deskstar T7K500 250GB Serial ATA 3.0Gb/s 7200RPM Hard Drive w/8MB Buffer
Microsoft Windows XP Professional
ViewSonic VX2235wm 22" Widescreen LCD Multimedia Display
Creative Labs Sound Blaster X-Fi Platinum Sound Card
ATI Technologies X1650 PRO Video Card, PCI Express, 512MB
Logitech diNovo Edge Ultra Slim Advanced Keyboard
Creative GigaWorks T20
Sony CRX32-AE CD-RW/DVD-ROM and Sony DRU830A DVD/CD

Thanks so much in advance!

---

### Post by dabl on 2007-07-06
Yes, I have observed an analogous situation -- different hardware, but the Live CD worked while the installation required tweaking.

I think those Windows drivers that you are observing (Ensoniq ES 1371) are really more like "translators" than real hardware drivers.  I'm not a computer engineer, but I think your virtual machine, be it Linux or Windows, sits on a translation layer in the "real" OS that is running the computer.

That's a nice hardware rig, and you've done well to get your ATI card working.

However, those newer Creative Labs sound cards (Audigy, et al) are a problem with Linux -- I don't know that a happy solution exists. :(

---

