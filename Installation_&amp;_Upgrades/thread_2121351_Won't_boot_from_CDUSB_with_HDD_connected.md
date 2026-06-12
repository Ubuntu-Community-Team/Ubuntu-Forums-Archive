---
title: "Won't boot from CD/USB with HDD connected"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by AmbiguousOutlier on 2013-03-01
Hello, I haven't really touched ubuntu in a few years, I got my laptop working perfectly, and I have now forgotten everything I learned. So I'm effectively a begginner again.

I decided to get out my old HTPC which has been collecting dust for awhile. I wanted to install the new XBMCbuntu on it. However I have a new standalone raid system so wanted to pull out my 4tb of hdd from the HTPC and use a working 500gb hdd which is quieter and faster. However now the computer hangs at "Verifying DMI Pool Data........". Despite setting it to boot from DVD or usb. If however I disconnect my HDD I can boot into the "live disk" version on xbmc or ubuntu. When trying the boot from DVD, with the HDD connected it doesn't even spin so it's not getting as far as looking at the disk. I've reset the CMOS jumpers. And as I'm not sure what the problem is, I'm unsure what to google. 

Any suggestions?

Kind Regards
Rhys

---

### Post by grahammechanical on 2013-03-01
You need to understand the error message [http://wiki.answers.com/Q/What_does_verifying_DMI_pool_data_mean](http://wiki.answers.com/Q/What_does_verifying_DMI_pool_data_mean) & [http://www.computerhope.com/issues/ch000474.htm](http://www.computerhope.com/issues/ch000474.htm)  Have you tried putting the 4TB drive back in? I am guessing but I think that there is confusion in the BIOS about the hard drive it is expecting to find. If you have reset the BIOS back to factory defaults which hard disk is it expecting to find? The 4TB or some other hard disk? The issue is, in my guess work opinion, between the BIOS and the hard disk.

> [SIZE=2][COLOR=#333333][FONT=verdana]Enter [/FONT][/COLOR][CMOS setup]("http://www.computerhope.com/issues/ch000192.htm")[COLOR=#333333][FONT=verdana] and verify that the hard drive settings are set properly and that it is set to Auto Detect.[/FONT][/COLOR][/SIZE]

Regards.

---

### Post by AmbiguousOutlier on 2013-03-02
I tried using one of the disks from the raid, however the same problem occurred. 

I have solved the problem albeit somewhat dubiously. 

I removed the HDD and booted up using the live cd, then on the installation page I "hot swapped" in the HDD and installed Ubuntu. Seems to work fine now. Although I'm sure plugging a HDD drive in whilst power is on isn't good for anything. 

Anyway, all's good that ends well.

---

