---
title: "Problems using kickstart scripts with usb cdrom"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by clotterm on 2010-04-27
Hi.
I'm trying to set up a machine with Lucid using kickstart, according to the steps mentioned in [http://www.ubuntu.com/system/files/u1/AutomatedDeploymentsWP-20090126.pdf](http://www.ubuntu.com/system/files/u1/AutomatedDeploymentsWP-20090126.pdf) . I've chosen not to go for PXE so I need to put the ks script somewhere on the cdrom. For that I modified the isolinux.cfg to [http://pastebin.com/knbJ8KiQ](http://pastebin.com/knbJ8KiQ) and added the kickstart script to the isolinux folder: [http://pastebin.com/hJmSMGrR](http://pastebin.com/hJmSMGrR)

The CD-Drive is an external cdrom drive which is attached to the server via USB. The thing which is not working right now: For some reason the usb modules are not loaded at the beginning, so the installer complains "No common CD-TOM drive was detected .... Load CD-ROM drivers from removable media". When I hit no and select "none" as the referring module + "/dev/cdrom" as the device everything works fine. But how do I avoid these manual steps? How do I load the USB modules prior to the ks-scripts?

BR, clotterm

---

