---
title: "root=/dev/sda problem on portable USB ubuntu"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by Pelham123 on 2007-06-21
I have Dapper 6.06 installed on an internal SATA drive on my PC. I recently installed Dapper on a 4Gb USB flash drive having disconnected my internal drives with the install. USB 6.06 flash is working fine, but I came across a problem when I try to boot from the USB flash on my home PC with internal hard drives connected. Both devices have have the GRUB root=/dev/sda. I tried editing the GRUB boot line at the boot menu to /dev/sdb for the flash but at the log-in screen it said it couldnt load the home directory.

I appreciate that there are some conflicts, but I dont quite know where to start. I am at present only able to boot my 6.06 flash if I disconnect the internal drives. Is there any way to change the root=/dev/sda on my flash that will make the changes without causing any OS confusion?

---

### Post by RealG187 on 2007-06-21
You can run Ubuntu off a USB?

---

### Post by Pelham123 on 2007-06-25
As long as your PC can boot from USB in its BIOS settings, then sure thing. Am running a complete install from a Corsair 4Gb flash drive, a little slow but handy to take to work...

---

### Post by RealG187 on 2007-06-25
My Laptop can boot USB, dunno about my P3...

---

