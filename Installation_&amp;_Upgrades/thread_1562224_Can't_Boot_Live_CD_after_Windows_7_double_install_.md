---
title: "Can't Boot Live CD after Windows 7 double install (Busy Box pops up)"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by d3mncln3r on 2010-08-27
Hi, I know I did this back asswards but I had little other option at the time.

I have two hard drives in my laptop, they are NOT raid configured. I installed 32-bit Ubuntu on the second HD, third partition: Sdb3. I then installed 64-bit Windows 7 on the same hard drive, first partition: Sdb1 (Sdb2 is formatted NTFS and will be used as storage). Windows installed fine.

Then I installed Windows in 32-bit on the first hard drive, first partion: Sda1. Sda2 will again be used as storage.

When I boot up, Windows boot manager gives me the option of the two windows OS's to install (but not Ubuntu of course). 

I wanted to boot into the Live CD, where I would reinstall grub, assuming it would recognize my two Windows, and I could boot into any of the three OS's upon start-up.

The Ubuntu Live CD, will act as though it is going to boot, bringing me up to the loading screen, then it cuts out to "busy box" and I am not sure what to do. Buys box is almost like a command prompt, but I don't understand the commands.

The main goal here is obviously to install grub so I can get the grub menu option to boot one of the three OS's, but I don't know how to do this without booting into the Live CD.

Any thoughts?

---

### Post by d3mncln3r on 2010-08-27
Figured it out... problem was my corrupted dvd... always check the dvd folks!

---

