---
title: "Booting from SD/USB?"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by Trevorius on 2007-11-24
Hi, I was just thinking, since there are some Linux live Cds that offer the copy to ram option, I was wondering how I would create a highspeed/low-power consumption, mobile solution that allowed me to boot from a 2GB SD card, or less preferably a USB drive, and never have to use the HDD or CD drive for anything, or perhaps even not have it present. 

At the moment, I'm running a dual boot with XP (although i never use it), but my bios doesn't have any option for USB or SD in the boot order (it currently has the HDD, CD, and Network). Is there some way for me to add this option to it, or perhaps configure GRUB to do so?

---

### Post by prodezigner on 2007-11-24
There's no way to force the BIOS for other boot options... However... if you *DISCLAIMER: NOT RESPONSIBLE FOR ACCIDENTS* flash your BIOS that option may become available to you.

I don't know about GRUB handling it or not... but I know there are methods to install a LiveCD to USB drives and I would 'assume' one could do the same with the SD card using the same directions.

---

### Post by Trevorius on 2007-11-25
> **prodezigner said:**
> There's no way to force the BIOS for other boot options... However... if you *DISCLAIMER: NOT RESPONSIBLE FOR ACCIDENTS* flash your BIOS that option may become available to you.

I don't know about GRUB handling it or not... but I know there are methods to install a LiveCD to USB drives and I would 'assume' one could do the same with the SD card using the same directions.
Thanks, but I'm not sure I'm ready to fool with the bios with my level of knowledge unless there was a way to ensure safety (ie backup settings, etc). I'll keep looking into it tho. Good suggestion.

---

### Post by Herman on 2007-11-25
You can try chainloading a USB disk's MBR with GRUB, or the boot sector of a partition in a USB disk, if GRUB, LiLo or Syslinux or some other bootloader is installed in the MBR or boot sector.

Probably you can also use the configfile or kernel commands too.

If your BIOS supports USB booting it should work. It's worth a try. If your BIOS doesn't support and a BIOS flash doesn't help then there's not much you can do.
You can run a Live CD in persistent mode intead, and save files and settings in a USB. 

Here is a good how-to, [LiveUsbPendrivePersistent - Ubuntu Wiki]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

Regards, Herman

---

