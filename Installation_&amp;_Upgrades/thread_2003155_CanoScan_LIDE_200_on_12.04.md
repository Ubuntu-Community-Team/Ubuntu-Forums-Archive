---
title: "CanoScan LIDE 200 on 12.04"
date: 2012-06-13
forum: Installation &amp; Upgrades
---

### Post by shvman on 2012-06-13
I'm stumped trying to get my Canon LIDE 200 scanner to scan in 12.04 (x64).  I got it working in 11.10 (32 bit) just fine on a different machine.

Here's my lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 2001:f103 D-Link Corp. DUB-H7 7-port USB 2.0 hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 004: ID 04a9:106d Canon, Inc. S750 Printer
Bus 001 Device 006: ID 04a9:1905 Canon, Inc. CanoScan LiDE 200

And a scanimage -L gives:
device `genesys:libusb:001:006' is a Canon LiDE 200 flatbed scanner

I've gotten it once or twice to scan about half of an image using scanimage >image.pnm, and then the scanner stops and locks up.  

If I 'scanimage -T' it sits there for about 30 seconds and then ends with a &quot;scanimage: sane_start: Invalid argument&quot;. 
 If I try a direct scan, I get:  $ scanimage>output.pmn scanimage: open of device genesys:libusb:001:007 failed: Invalid argument    
I'm beginning to think this is some kind of incompatibility with my mobo (785GM-E65)....since it works so well on a Dell laptop 1420 with Intel chips.   

Any ideas?

Thanks for your time.

---

### Post by shvman on 2012-06-16
OK, let me answer my own question.

The problem with my scanner involved my desktop computer.  I had newly installed Ubuntu 12.04 on my desktop and loaded XSANE to use my Canon LiDE 200 scanner.  It would NOT scan and gave errors and behaviors described in the original post.  It would not work with either Simple Scan and XSANE.  

I previously installed XSANE on my laptop.  Just for kicks, I compared the ' .sane/xsane' directories between the two machines and noticed that my desktop was missing 2 files in that subdirectory: xsane.rc and Canon:LiDE200.drc.   

I copied both files from my laptop to my desktop.  XSANE started working immediately after a reboot.    

I don't know at what stage of the XSANE installation process or initial use these files are supposed to be made, but somehow, that never happened in my case.  

Interestingly, the difference between the machines is that the laptop runs 11.10 and is 32 bit, while the desktop is 64 bit and runs 12.04.  I'm not sure the difference is important. 

Sorry to waste everyone's time.  I appreciate so many people  taking the time to read my original post.

---

### Post by robroyality on 2012-07-07
Thanks alot!!! Great solution that also worked for me. I restored an old backup of the "~/.sane/canon-lide-100.cal"-file and my LiDE 100 scans like before.

Kind regards,
Roy

---

