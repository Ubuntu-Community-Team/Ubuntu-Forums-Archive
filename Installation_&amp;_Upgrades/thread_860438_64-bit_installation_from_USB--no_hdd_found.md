---
title: "64-bit installation from USB--no hdd found"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by wolfmanyoda on 2008-07-15
Hello, I'm trying to intall the 64-bit version from my USB drive. All goes well at first, it boots up fine, but when I try to actually install it there is no hard disk found.
 
Here's some specs:

MSI P45 mainboard
Intel core 2 quad Q6600
4 gig RAM
GeForce 9600GT
Western Digital 640GB SATA drive, it has windows on a 200GB partition, my files on another 300GB partition, and about 100GB leftover for Ubuntu, if I can get it to work.
Any help is appreciated.

EDIT: I just saw this on another thread, I'll try it out and see what happens:
all_generic_ide
EDIT 2: That didn't work.

---

### Post by markbuntu on 2008-07-15
Try setting SATA to IDE in the bios. This is a particular problem with those mobos but the bios does contain an option for treating SATA as IDE.

---

### Post by wolfmanyoda on 2008-07-15
Ok, but would that degrade the hard drive perfprmance in either ubuntu or windows?

---

### Post by wolfmanyoda on 2008-07-16
I scoured my BIOS and couldn't find that setting. I may have to install an IDE drive just for ubuntu.

---

### Post by wolfmanyoda on 2008-07-16
Well that went bad. I installed an IDE drive, booted up from my USB and installed Ubuntu. Since it couldn't see the SATA drive my dual-boot doesn't work because grub only sees one OS, Ubuntu. I can't be plugging and unplugging hard drives everytime I want to switch between Ubuntu and Windows.
Guess I'll just pray for the next version of Ubuntu to be SATA friendly. :(

---

### Post by wolfmanyoda on 2008-07-17
Ok a dude on another forum suggested I do a Wubi install. I'm giving that a try, it's downloading now.

---

### Post by wolfmanyoda on 2008-07-18
Wubi worked. :guitar:

---

