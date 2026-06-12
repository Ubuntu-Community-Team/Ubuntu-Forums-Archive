---
title: "netatalk/appletalk printing problem"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by BobBlec on 2007-11-03
Greetings,
  I'm trying to add my linux machine (7.04) to my AppleTalk setup on my Mac.

  My Blue & White Mac (with a G4/500 MHz upgrade) is running OSX 10.3.9. I have my linux machine on an Ethernet LAN; it's sharing my Mac's Internet connection already (points to the Mac's IP rather than the DSL modem's). For a printer, I have an Apple LaserWriter 4/600 PS (named 'Zenger') hooked into the LAN via an old Dayna EtherPrint bridge. It works fine printing from my Mac, but not from the linux machine.

  I installed netatalk the way that [https://help.ubuntu.com/community/AppleTalk](https://help.ubuntu.com/community/AppleTalk) said to; when I ran nbplkup, I got this result:

rfblec@ubuntu:/$ nbplkup
          ubuntu:AFPServer                 65280.93:128
          ubuntu:netatalk                    65280.93:4
          ubuntu:Workstation             65280.93:4
          SmurfTower:Darwin             65445.180:128

  So netatalk is seeing the Mac (SmurfTower), but *not* the printer!

  On the Mac, I have Printer Sharing (System Preferences -> Sharing -> Services) and 'Share my printers with other computers' (System Preferences -> Hardware -> Print & Fax) enabled, which *should* be everything I need.

  So how do I get the linux machine to see my printer?

  Thanks!

  -Bob

---

