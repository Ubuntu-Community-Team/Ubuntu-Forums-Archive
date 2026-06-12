---
title: "?trick BIOS to think USB FLASH is a USB CDROM?"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by 1branchonthevine on 2009-12-19
I have an older system that fortunately allows booting from a USB Cdrom, but unfortunately it does not support a bootable USB flash drive. Is it possible to trick the BIOS to think the USB flash is a Cdrom? Maybe restructuring the media format from fat to ISO9660, or something?

We want to make a backup image of a system, but it doesn't fit on a single cd, so we were hoping someone out there could tell us if there is a way to do this on a flash drive. THANKS A MILLION!

Just to clarify... I have no problem making a bootable USB flash drive... ours already works on a newer machine... whe just hope we can get the older system to boot from this USB flash media.

---

### Post by phillw on 2009-12-19
> **1branchonthevine said:**
> I have an older system that fortunately allows booting from a USB Cdrom, but unfortunately it does not support a bootable USB flash drive. Is it possible to trick the BIOS to think the USB flash is a Cdrom? Maybe restructuring the media format from fat to ISO9660, or something?

We want to make a backup image of a system, but it doesn't fit on a single cd, so we were hoping someone out there could tell us if there is a way to do this on a flash drive. THANKS A MILLION!

Just to clarify... I have no problem making a bootable USB flash drive... ours already works on a newer machine... whe just hope we can get the older system to boot from this USB flash media.

BIOS's and usb boot devices are funny bed-fellows. I have to set my BIOS to USB-CD for it to boot from my USB stick, plain USB doesn't work !!

As most of the stuff on a system, isn't the actual system (~home is usually a big part), you could look at a backup without ~home, and then one of JUST ~home.

I'm not sure if either of these allow for multiple CD splitting 
like Pybackpack --> [http://www.ubuntugeek.com/pybackpack...x-desktop.html]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html")
Or Clonezilla --> [http://www.tuxradar.com/content/how-...ves-clonezilla]("http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla")

These guys have some good stuff [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

At the bottom of that page are options to test for usb booting & what to do if you cannot.

Regards,

Phill.

---

### Post by 1branchonthevine on 2009-12-22
I haven't tried any solution yet, but I think I'll give this one a try...

"We can trick the BIOS by modifying the number of heads and sectors being displayed from the USB flash device to match that of a zip drive."
[http://www.pendrivelinux.com/booting-linux-from-usb-zip-on-older-systems/](http://www.pendrivelinux.com/booting-linux-from-usb-zip-on-older-systems/)

I just wish someone could confirm whether or not the same could be done to trick the BIOS into thinking the flash drive was a crdom... but this is definitely worth the try.

I'll do my best to post back.
Thanks!

---

