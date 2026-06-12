---
title: "No Boot Sector"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by mbohnert on 2010-05-11
I have a rather puzzling error. I recently purchased an usb external hard drive with the intent of installing Ubuntu on it. I have had great success with installing various linux flavors on usb thumb drives but I need a little larger space for engineering applications that I use.
 
Anyway, I removed my laptop's internal hard drive and installed ubuntu 9.10 on a recently formated external hard drive. Everything worked fine at first. Upon restarting I get an error that says "no boot sector" and it asks to hit either f1 to retry. 
 
When I hit retry, Grub loads most of the time. Occasionally it does not work.
 
Any ideas why this isn't working? Is Grub just not installing correctly? I searched for this error but I found nothing that directly applied.

---

### Post by dstew on 2010-05-12
That error probably comes from your computer's BIOS. It sounds like there are some hardware issues between the USB hard drive and your computer's USB system. You might check in the BIOS to see if there is a setting that might be changed to allow a smoother boot from the external USB drive.

If Grub works sometimes, it is probably set up right.

---

### Post by oldfred on 2010-05-12
welcome to the forums.

Some BIOS want a boot flag on a primary partition (assumes windows?). Ubuntu does not use a boot flag, windows requires one to define the active ( or bootable ) partition.

You can use gparted or disk utility to put a boot flag on a primary partition. For linux use it can be on anyone as it is not used to boot.

---

