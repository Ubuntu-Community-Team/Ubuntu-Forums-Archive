---
title: "pls help......ubuntu 11.04 on external hard disk"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by jas1291 on 2011-10-02
i installed 11.04 on external drive
it showed success
when it boot only show 
 grub>

---

### Post by yanom on 2011-10-02
...are you selecting the USB drive from your BIOS? Are you sure you're booting from the USB drive and not the Hard drive?

Installing Ubuntu to a USB hard drive is most successful if your internal hard drive(s) are **unplugged** whilst you are installing to the USB drive. Install to the USB drive, then, once Ubuntu is all finished, plug the internal hard drive(s) back in.

What happened here is that your computer installed GRUB, the bootloader, **partially to your USB drive and partially to your internal hard drive!** You now must put a bootloader back onto your internal drive.

...does the internal hard drive have Windows?

---

### Post by jas1291 on 2011-10-02
my internal hard disk is unplugged.....and i am mounting correctly

---

