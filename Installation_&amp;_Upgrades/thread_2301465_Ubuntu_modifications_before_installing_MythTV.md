---
title: "Ubuntu modifications before installing MythTV"
date: 2015-11-02
forum: Installation &amp; Upgrades
---

### Post by jrh74 on 2015-11-02
I built a computer (described below) with a view toward learning Linux. I got the operating system installed okay and have done a bunch of reading and played around a little but without a practical problem to solve, have allowed this project to languish.  Now, after more than a year I believe I have found a reasonably challenging problem to work on.   Microsoft is not supporting media center in windows 10 so I would like to try and install, configure and use MythTV as a replacement.  My questions are as follows:

 1.  Given the system as described, should I stick with 32 bit OS or should I change to 64 bit?  How do I change from 32 bit to 64 bit?  
2.   Should I install on the existing desktop OS or start fresh with MythBuntu and add features so that I can use this computer as a general purpose desktop (libreoffice, CAD etc, email, web surfing etc.)?  Is uninstalling ubuntu desktop difficult?  How  is it done?  Note that I have no problem about backing up since I have yet to install any important personal stuff.
3.  Should I upgrade to Ubuntu 15.04 before installing mythtv?

 Processor: Intel core i5-3750k 3rd Gen unlocked @3.40 GHz
Mother board: ASRock Z77 Pro 4
Operating system: Ubuntu desktop 14.04.2 32 bit
 Hard Drive: WDOEM  WD1TB BLUE SATA6.0 HD
 Memory: CRUCIAL 8GB 4X2D3 1333 DIMM CL
 TV tuner: Hauppauge WinTV-HVR-2250
 Windows 7 is installed on a seperate 500GB Hard drive

---

### Post by deadflowr on 2015-11-02
1)To upgrade from one arch(32-bit) to another(64-bit) you need to reinstall, simple as that.

2)If you're only ever going to use the system as a media center, then install mythbuntu fresh, otherwise you can go a head and install it on top of the existing system.
The backend will be set to always run in the background, but can be turned off. And you can launch the frontend as an app, or a standalone session.

But either way (either fresh install or added to an existing system) works fine, imho.
Mythbuntu can install a desktop that can be used for other purposes like web browser, etc etc.

2.5) I would ignore even trying to remove the Ubuntu desktop.
You'd be more likely inclined to reinstall if you did.

3)Stick to 14.04, 15.04 hits EOL(end of life) in January 2016.
I don't think mythbuntu even has a 15.04 anyway.

Sorry if I'm confusing, but hope it helps.

---

