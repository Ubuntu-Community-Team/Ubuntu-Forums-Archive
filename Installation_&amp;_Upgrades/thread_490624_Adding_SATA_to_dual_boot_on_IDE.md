---
title: "Adding SATA to dual boot on IDE"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by narehart on 2007-07-02
Ok heres my problem:  I have a tower with both a IDE and a SATA hard drive.  I tried unsuccessfully for three days to put a dual boot on my IDE of Ubuntu and XP.  I kept receiving GRUB errors after installing Ubuntu and noticed that when I booted off a live CD my hard drive assignment numbers (hd0,02) would change randomly.

After struggling with this for a while I came across a thread where somebody claimed that GRUB has issues with a SATA IDE setup.  So, I unplugged my SATA and installed my dual boot on the IDE.  It now works beautifully but I really need that SATA for media storage.

So my question is this: If I plug my SATA back in will it work correctly or will GRUB get messed up again?

---

### Post by louieb on 2007-07-02
Just plug the sata drive back in  won't hurt anything that unplugging it won't fix.
Make sure your BIOS is set to boot the IDE drive first.
BTW: Much better title that you other thread with the same question.
[http://ubuntuforums.org/showthread.php?t=489095](http://ubuntuforums.org/showthread.php?t=489095)

---

### Post by koshari on 2007-07-02
grub gets the sata hard drive number off a lookup table contained in devices.map.

so your sata drive sdb2 could be called by hd2,2 hy grub, check the devices.map file in /boot/grub directory.

---

### Post by koshari on 2007-07-02
> If I plug my SATA back in will it work correctly or will GRUB get messed up again?

i cant see why it would, the linux os would simply see it as sda (or b or c depending on if you have other sata/usb drives.)

---

### Post by narehart on 2007-07-02
Thanks for the quick responses.  I'll be plugging my SATA back in tonight...

---

