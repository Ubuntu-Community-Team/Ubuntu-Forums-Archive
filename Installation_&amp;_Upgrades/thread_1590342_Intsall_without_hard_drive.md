---
title: "Intsall without hard drive"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by the_chief on 2010-10-07
Ok I have an old laptop running XP that is not working properly and I would like to install Ubuntu to give he machine new life. I cannot boot from the USB install stick, however if I take the hard drive out I can get the computer to boot Ubuntu off the USB stick and can get the computer running. When I put the hard drive back in I cannot install Ubuntu on it. Any ideas on a work around on this install. Thanks for any help

---

### Post by sikander3786 on 2010-10-07
Did you try setting your USB device as the first boot device? Enter Bios by hitting whatever key it accepts, F2 in most cases and under Boot Device Priority, select your USB drive as the First Boot Device, save changes and reboot.

---

### Post by pricetech on 2010-10-07
Some will give you a boot menu where you can choose which drive to boot from.  F12 if it's a Dell, F10 as I recall for HP.  It will vary.

---

### Post by the_chief on 2010-10-07
The Acer 3000 laptop is from 2005 however, boot from USB is not on the boot menu. When I pull out the hard drive though, I can totally boot from the USB stick. The problem is when I get Ubuntu up I dont have anywhere to install. I put the hard drive back in but it does not recognize it. Presumably I could update the bios or Grub but I am nervous about doing these things. Any other thoughts?

---

### Post by sikander3786 on 2010-10-08
Sometimes USB Drives appear under the HDD heading in Bios Menu and are recognized as an HDD not a USB. Did you check there? It might not be appearing in the Boot Menu, but it should be present in the Bios menu and can be changed from there.

---

