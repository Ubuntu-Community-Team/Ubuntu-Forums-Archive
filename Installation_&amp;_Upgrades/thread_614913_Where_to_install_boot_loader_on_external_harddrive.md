---
title: "Where to install boot loader on external harddrive"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by dc_jt on 2007-11-16
Hi Im in the process of installing ubuntu to an external hard drive, however when I get to the final step and go to advanced it says install boot loader which is checked and underneath has (hd0).

DO I leave this as it is or do I need to change it? By the way I have unplugged my internal hard drive whilst doing this.

Thanks

---

### Post by dc_jt on 2007-11-16
Do I actually need a boot loader?

My computer can boot from usb so if I have my external hard drive plugged in then will it boot from this and if not then it will boot from my internal hard drive??

Please someone give me an answer??

Thanks

---

### Post by logos34 on 2007-11-16
> **dc_jt said:**
> DO I leave this as it is or do I need to change it? By the way I have unplugged my internal hard drive whilst doing this.

If the internal is disconnected, then leave it (hd0).

> Do I actually need a boot loader?

My computer can boot from usb so if I have my external hard drive plugged in then will it boot from this and if not then it will boot from my internal hard drive??


Yes, you need a bootloader (whether grub, lilo, GAG, etc).

When you want to boot from usb, simply hit F2 or whatever and change the hard disk boot priority in the bios.

---

