---
title: "[SOLVED] Asus_m2r32-mvp"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by Dr Zin on 2008-10-28
Ok for  about a year ago installed Ubuntu 8.04 via the package manger and started to have issues.  Then i stop working on the issue because i was spent all my time last summer tryn to install a Linux distro "Gentoo" which i still love to today. and not understanding  the issue installed Ubuntu 7.04. installed like a dream  no issue i was happy for the time. Update flag popped up and said 7.10 is ready to down load, and i did. Then again it was time for 8.04 and installed and it crashed and sat there getting dusty. So life happens and i need to start working on a Linux again and i like the KDE better then th Gnome so here i am tryn to fix and upgrade my system and prefer not rip out my motherboard for another year or so. so I hunt and hunt for answers. Thank god for MS windows and torrent sites. What i found was....:)




[URL="https://wiki.ubuntu.com/ASUS_M2R32-MVP"][COLOR="Blue"]ASUS_M2R32-MVP[/COLOR]
[/URL]

>    * ASUS_M2R32-MVP

ASUS M2R32-MVP

Chipset AMD 580X CrossFire Chipset + ATI SB600

Bios Revision 0804

My setup:

    * -Athlon X2 3800+ AM2 (Windsor Core 2GHz + 2x512Kb Cache) 89 Watt -2x1 gig Corsair 5-5-5-12 DDR2 800mhz -ASUS ATI X1900 XTX PCIe Video card -520 watts P/S -Onboard sound -Onboard NIC 

Ubuntu 8.04.1 LTS (Hardy Heron) Installation issues

    * -Had to remove 'quite splash' and add "pci=nomsi" "apci=off" to prevent the installation from stalling during SATA HD detection. 

Post installation issues:

    * - "pci=nomsi" has to be added to the kernel initialization script to facilitate booting. Otherwise the system will hang every time. 

What was tested

    * -Onboard NIC: Seems to work fine up to 1Gb/sec -Onboard Sound: Playback and volume control seem to work in stereo. (Microphone and 5.1 channel playback untested) -Video card: Compiz Fusion up and working fine(Cube, Rotate, Fire, Annotate, Water, Reflection, Dbus, Cubecaps), Mpeg/AVI video playback working, Flash Video playback working, -PS2 ports: both mouse and keyboard work(even ancient Model M IBM keyboard works fine) -SATA Devices: Tested several SATA HDs, all mounted up and read just fine. SATA DVD-Rom mounted and read fine. 

Other notes

    * I "have not" tried to install directly to a SATA HD, yet. Nor have I tried any serious 3D apps. Additionally no benchmarking have yet been performed. 

CategoryHardware

ASUS_M2R32-MVP (last edited 2008-08-06 16:16:30 by localhost)" 






so i got all happy about this but there is one thing that bugs me is > "Post installation issues:

    * - "pci=nomsi" has to be added to the kernel initialization script to facilitate booting. Otherwise the system will hang every time. " 

 i am still a a little new Linux but i can get around but not as fast of the pros out there I hope that will change. with the long winded opening to the questions.

Where do I put this in "pci=nomsi" install:confused:?
which one is better to the "alt" install or the GUI install for this change?
Will i have down load  Version to ad this change every time?

THE doctor ZIN

P.S.

it worked by placing the pic=nomsi and apci=off worked when doing the install  cool i happy now. but when the 8.10 comes out fully do need reinstall form scratch?

---

### Post by Dr Zin on 2008-10-30
anyone let me know it if the 8.10 is have the same issue with they did with 8.04

---

