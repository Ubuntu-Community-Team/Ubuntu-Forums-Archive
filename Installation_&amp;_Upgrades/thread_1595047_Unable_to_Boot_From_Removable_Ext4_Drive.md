---
title: "Unable to Boot From Removable Ext4 Drive"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Sanivo on 2010-10-12
I recently downloaded Ubuntu 10.10 and installed it onto a 250gb removable disk using a 240gb ext4 partition and a 10gb swap space. 

       I am using a Sony VAIO (VPCF115FM) and it would appear that my BIOS is very limited as to bootup options. I can only choose internal HDD/external device/network/CD Drive. I cannot check whether or not my BIOS is able to recognize the external ext4 (but from experiences so far it would seem that it cannot)

      After much tinkering i got my internal windows 7 to recognize the drive as ext3 (Used ext2 volume manager to add a registry entry for the drive). However, I need to unplug and replug in the drive for it to be recognized, if i leave it plugged in from booting it shows up as unrecognized. 

      Summary: I would like to be able to boot up Ubuntu off this external drive, but as of now it would appear that my BIOS is unable to recognize the drive. Windows can recognize it as ext3, and I can access contents of the ubuntu partition from windows. 

       If anyone has any information on how I could get this working that would be fantastic, i've tried formatting the drive to other filesystems (ext3,ext2,XFS) but none of them would work either, so any information would be sweet :D

~Sanivo

---

### Post by Sanivo on 2010-10-13
<Bump>

---

### Post by wilee-nilee on 2010-10-13
You might try the single session boot choice. Start your computer and hit the f12 key repeatedly immediately to see if you get to the choice of boot screen. The key may be another f-key or esc, see if you can find it. The usb device may show up in that post bios boot choice, it should show a USB boot option in the bios.

This may be a computer setup with a newer booting schema that is causing a problem, but any computer built in the last 5 years or so can generally boot a USB.

You can burn a plop cd and boot it and it will boot the usb drive. 
[http://www.plop.at/](http://www.plop.at/)

---

### Post by Sanivo on 2010-10-14
Not working quite yet, but thanks for the tip on plop, I'm mucher closer now. I'll just need to stalk around their forums to work out some kinks preventing me from booting still. Shouldn't be any major difficulty, Thank you!

---

### Post by C.S.Cameron on 2010-10-14
Is your drive listed under hard drives in BIOS?
If so set it as first hard drive to boot.

---

