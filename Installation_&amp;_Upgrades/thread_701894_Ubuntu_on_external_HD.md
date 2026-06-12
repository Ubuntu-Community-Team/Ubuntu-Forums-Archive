---
title: "Ubuntu on external HD"
date: 2008-02-19
forum: Installation &amp; Upgrades
---

### Post by Psicho on 2008-02-19
Hi,

I was thinking of installing Ubuntu on my external hard drive. The goal I'm trying to achieve is to have Ubuntu boot automatically whenever the usb drive is connected to the pc at startup, and when it's not, the pc should not be aware of any form of dual booting. Basically I don't want to see a dual boot option when starting the computer and I just want to rely on the BIOS giving boot priority to the USB in order to decide which OS to run.

I know that is possible because I found a similar post about it in these forums, but I never found the specific instructions for how to achieve that kind of functionality. What would I have to specify during the installation of Ubuntu on the external HD to make sure GRUB is not set in dual boot mode with Windows?

Thank you!

---

### Post by Psicho on 2008-02-19
Well I went ahead and installed the OS onto the external drive, 59 gigs for root, 1 gig for swap. Through the "Advanced" window in one of the last screens of the installation wizard I specified /dev/sdb1 as the destination for GRUB.

Everything installed smoothly but when I try to boot from the drive, grub reports an error 17, saying that it cannot mount the selected partition.

Any suggestions? I already looked up the forum post where the user suggested changing the HDD settings to TYPE->USER and MODE->AUTO, but my BIOS doesn't happen to have that unfortunately.

---

### Post by confused57 on 2008-02-19
> **Psicho said:**
> Well I went ahead and installed the OS onto the external drive, 59 gigs for root, 1 gig for swap. Through the "Advanced" window in one of the last screens of the installation wizard I specified /dev/sdb1 as the destination for GRUB.

Everything installed smoothly but when I try to boot from the drive, grub reports an error 17, saying that it cannot mount the selected partition.

Any suggestions? I already looked up the forum post where the user suggested changing the HDD settings to TYPE->USER and MODE->AUTO, but my BIOS doesn't happen to have that unfortunately.
You could try Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

If you're getting a grub boot menu when you boot first to your external drive, try highlighting the Ubuntu entry, press "e", select line with root, press "e" again, change root from (hd1,0) to (hd0,0), press "enter", then "b" to boot.  This is temporary if it works, but can be made permanent:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Psicho on 2008-02-20
Thanks, that worked great (the second step).

---

