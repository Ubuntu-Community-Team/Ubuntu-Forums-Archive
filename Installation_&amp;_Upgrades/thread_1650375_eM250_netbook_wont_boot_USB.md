---
title: "eM250 netbook wont boot USB"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by JacobVengeance on 2010-12-21
I have been trying to install Ubuntu 10.10 UNR on my netbook, but it hangs up on boot menu and BIOS and never loads when trying to boot it. 

I have been using "Universal-USB-Installer-1.8.1.9" and the .iso to try and it won't work. Is there any other methods I could try or a different program used to write to USB on Windows 7?

---

### Post by sikander3786 on 2010-12-21
What do you mean by hang on boot menu and BIOS? Does it get past the Bios screen? Are there any error messages? And is your netbook properly set to boot from the USB device?

As an alternative, you can try Unetbootin.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by JacobVengeance on 2010-12-21
It doesn't get past main BIOS screen and just sits there.

---

### Post by sikander3786 on 2010-12-21
And if you just remove the USB drive, it gets past the Bios screen and successfully boots the other OS there?

Did you try with some other USB drive?

---

### Post by JacobVengeance on 2010-12-21
> **sikander3786 said:**
> And if you just remove the USB drive, it gets past the Bios screen and successfully boots the other OS there?

Did you try with some other USB drive?

If I try booting with the USB plugged in at all it hangs until I reboot. 

I only have this one drive to test it with..

---

### Post by sikander3786 on 2010-12-21
> **JacobVengeance said:**
> If I try booting with the USB plugged in at all it hangs until I reboot. 

I only have this one drive to test it with..
Ok. Re-format your USB drive to FAT32, use Unetbootin and burn Ubuntu image once again and try to boot from it. If it still hangs there, it is either some problem with the USB drive or USB port or Bios. But definitely, not Ubuntu :-)

Resetting the Bios settings to default might help.

Are you sure the USB drive is healthy? And also, the USB ports there? I mean did you ever notice any problem with either of them?

---

### Post by JacobVengeance on 2010-12-22
> **sikander3786 said:**
> Ok. Re-format your USB drive to FAT32, use Unetbootin and burn Ubuntu image once again and try to boot from it. If it still hangs there, it is either some problem with the USB drive or USB port or Bios. But definitely, not Ubuntu :-)

Resetting the Bios settings to default might help.

Are you sure the USB drive is healthy? And also, the USB ports there? I mean did you ever notice any problem with either of them?

I ended up installing via Wubi and then using USB creator on it and then uninstalling wubi and then installing from USB I created with it and it worked.

---

