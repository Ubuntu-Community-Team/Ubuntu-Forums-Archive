---
title: "ubiquity install wizard crashes; cannot install ubuntu-MATE 18.04.4"
date: 2020-03-24
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2020-03-24
I've tried several times now to install Ubuntu-MATE version 1804.4 from a live USB. 

Every time I hit "install," nothing happens. A circle spins for a few seconds, then stops.


 I get an error message saying that ubiquity has crashed.


 In the terminal I checked for ubiquity using: 

```
dpkg -l ubuiquity 
sudo apt update
sudo apt install ubiquity 
```

and saw that the live USB already has the latest version of ubuquity, which is 18.04.14.14.

I have a System76 Wild Dog, 64-bit desktop workstation, 4-core Q9650 3GHz, 8 GB ram. It has a BIOS, not UEFI.


Graphics: PNY Nvidia GeForce GTS 450, driver v. 367.44.
 OSs: Ubuntu-MATE 16.04 & 14.04. Drives: 2 960-GB Sandisk SSDs.

I want to install Ubuntu-MATE 18.04.4 onto one of the SSDs (A standalone  960-GB SSD in an enclosure, that I later want to move into the Desktop  box and boot directly from.)


 Here is some of the lengthy error message report:


 ExecutablePath:
/usr/lib/ubiquity/bin/ubiquity


 Package:
ubiquity 18.04.14.14


 ProblemType:
Crash


 Title:
ubiquity crashed with PermissionError in___init___(): [Errno 13]
Permission denied '/cdrom/.disk/info'




 How can I get a functioning  ubiquity in the live USB and get the install wizard to open so I can complete the  installation?

---

### Post by watchpocket on 2020-03-24
SOLVED: My live USB drive itself had permissions enabled for  user only.  

I created read and execute permissions for group and other:

  chmod go+rx /media/name-of-live-USB-stick

---

