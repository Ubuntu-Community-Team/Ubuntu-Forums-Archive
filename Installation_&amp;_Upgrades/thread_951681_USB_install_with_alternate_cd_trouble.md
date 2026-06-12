---
title: "USB install with alternate cd trouble"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by mybrownianmotion on 2008-10-18
I went and bought myself the Asus EEE pc the other day, and decided I want to put Ubuntu on it. I downloaded Unetbootin, and the Intrepid Alternate beta cd, and made my thumbdrive bootable.
The reason I am going with the alternate cd and not the live cd, is that I can not partition my drive into a LFS, and make encrypted partitions with the live cd.

The problem starts after booting off of the thumbdrive, it tries to look for a cd drive, but as the EEE doesn't have one, it fails.
I followed the advice here for mounting the usb stick as a cd rom: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) and it seems to work, it mounts the stick properly, but when I return to the installation, it now says "there was a problem reading data from the cd-rom, etc, failed to copy file from cd-rom. retry? yes, no". I can go into the terminal off of the install screen and cd to /cdrom, and I can see all the files on there, so I know it mounted correctly.

I am not sure where to go from here, anyone have any advice please?

---

### Post by leafw on 2008-11-09
I have the exact same problem with an eee 1000.

Did you find any solution so far?

---

### Post by leafw on 2008-11-09
I found a solution myself: don't copy the .iso file in the USB drive, but the actual folders as explained here:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Notice you'll need to edit the syslinux.cfg to remove the /cdrom path preceeding all entries.

---

