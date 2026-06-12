---
title: "Hard RAID0 and SATA DVDROM / CDRW not recognised"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by kash4u on 2005-05-19
It is particularly frustrating for someone who is relatively experienced with Windows systems and who is evaluating a dual boot move to Linux to be unable to install any Linux distro out of the box.  I had hoped that by now installing Linux would be a painless process but alas this has not been true for me.

I had attempted to use a range of the popular 'Live' distros (eg, SuSe, Fedora, Knoppix, etc...) - but every single one failed.  The reason (from what little I know of Linux) is because of my hardware:

AMD Athlon 2600XP
Windows XP Prof.
1GB DDR
DFi LanParty Ultra B (nForce 2 chipset)
Hard SATA (Silicon Image) 3114 Raid 0 (2 * Hitachi Deskstar 160GBs)
IDE Primary Master IBM Deskstar 13GB
Nec DVDRW (USB 2)
LiteON DVDROM (connected to SATA port via PATA to SATA Adapter)
LiteOn CDRW (connected to SATA port via PATA to SATA Adapter)

In particular I think all the distros had problems dealing with my hard RAID 0 setup.  Imagine my delight when Ubuntu (Hoary 5.04) Live ran 'out of the box' so to speak.  So I decided to install it.

It failed to mount my SATA DVDROM, so I ran install from the USB DVDRW.  It recognised that I had three hard drives but failed to recognise my raid 0 setup (which was originally setup from the Si3114 BIOS (not via Windows software)).  I want to install to a linux partition which has already been created on the RAID volume (via Windows) - but it doesn't recognise the RAID setup.

So, what do I do to get Hoary installed on my existing RAID setup and get it to recognise my DVDROM and CDRW??  Please bear in mind that I am new to Linux - I don't mind technical procedures as long as they are explained step by step.

Many thanks

---

### Post by alastair on 2005-05-19
You might not be able to get the RAID recognised. Although it might be configured via BIOS, it still requires driver support once the OS boots (to recognise the 2 disks as a single "raid" volume). No doubt Windows has a driver - but Linux may not have (or not "out of the box" anyway).

Both Linux and Windows could deal with a s/w (OS created) stripe though. It would be a shame to let "Silicon Image" determine whether or not you try an alternative.

---

### Post by WOTHed on 2005-09-01
I have your mobo and I've heard raid will work if you turn off the bios raid and let linux handle it software style.

I havn't tryed it yet but I heard people doing it sucusfully.

Thats form a blank set of hds don't know about with nfts partions etc.

PS. Have you had your gb onbord lan working? I can get the nforce 100mb one going but not the realtec 1gb

---

### Post by Standy on 2008-05-14
I know this is a long lost post thread but... does anyone have driveres or such for si3114 silicon ? i cant delete what i've got on it, bios style, because it's 1,64 TB worth of data on there....

---

