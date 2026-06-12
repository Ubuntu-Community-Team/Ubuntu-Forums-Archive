---
title: "Boot from USB storage device"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by Particle on 2008-01-13
I've got an install of Ubuntu 7.10 on a 4GB flash memory card of mine.  This device is connected via a USB card reader.  Now, in older revisions of my motherboard's BIOS, I could select such a device to boot from.  If the card was plugged in, it showed up as a removable storage device.  This feature disappeared many revisions ago, however.  So, now I need a way to boot to this CF card using a boot CD/rescue mode/something so long as it doesn't involve overwriting my normal bootloader for a complicated Windows Server 2003 setup.

Any ideas are welcome and appreciated!

---

### Post by enrique.vidal on 2008-01-13
What Bios brand and version is the one you have? I had a similar problem once I know its annoying I had to update my BIOS.

Have you tried rolling back to your previous version? or have you looked for an update that includes this option, it is odd that the vendor included this option on an old version in remove it on the new one that surely makes no sense from them.

Perhaps the option is still there but hidden under a different name.

---

### Post by Pumalite on 2008-01-13
Check Super Grub; it can boot just about anything, anywhere, but I'm not sure a bout a FlashDrive.
[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Particle on 2008-01-13
I have a DFI ICFX3200-T2R/G motherboard with the latest release.  The BIOS that came with the board did have the option, but it has been removed in successive revisions.  I can't go back to the old one that supports this function due to system instability with the old version.

I did try super grub disk off of Ultimate BootCD, but it failed to see anything other than my RAID controller arrays.

---

