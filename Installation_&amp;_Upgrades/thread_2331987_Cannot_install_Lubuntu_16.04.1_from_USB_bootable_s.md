---
title: "Cannot install Lubuntu 16.04.1 from USB bootable stick"
date: 2016-07-27
forum: Installation &amp; Upgrades
---

### Post by angelo16 on 2016-07-27
Hi Guys, I am trying to make a bootable usb stick with lubuntu.

After download the iso file, I used the usb-creator-gtk to create the bootable stick in a Ubuntu Mate (16.04). Everything is fine with the end message "Installation is complete.  You may now run Ubuntu on other computers by booting them with this drive inserted" , but when I put the usb stick in the new machine it says no bootable disk.

---

### Post by Rex Bouwense on 2016-07-27
There may be several reasons for this.  First the new machine may not be set up to boot from a flash drive.  You have to change that in the BIOS.  Second if the new machine is a laptop, some laptops recognize a flash drive as another hard drive.  If that is the case here then you have to move the flash drive ahead of your computer hard drive (once again in the BIOS.)  Those are two obvious reasons.  If your computer is UEFI equipped then there may be other causes.  Is the new machine UEFI?

---

### Post by smelheim85 on 2016-07-27
If you can't find if your new laptop has UEFI enabled by default.  Could you provide the specs for the computer, model, OS, things of that nature and we can figure it out if you can't find the answer.

---

### Post by angelo16 on 2016-07-28
Hi, guys. It is a machine  with Lubuntu already. I've found the problem it was the USB stick, for some reason U-Mate has identified as a 4Gb instead of 1Gb and did generate bootable the USB, but that Lubuntu machine did not at the boot time. After some search, I've found instructions how to correct the partition info on the USB stick and generated again the bootable usb and now everything is fine.

By the way, how can I set this as solved ?

---

### Post by sudodus on 2016-07-28
Congratulations and thanks for sharing your solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

