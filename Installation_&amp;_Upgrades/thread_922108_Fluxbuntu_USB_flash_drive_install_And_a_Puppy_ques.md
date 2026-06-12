---
title: "Fluxbuntu: USB flash drive install? And a Puppy question."
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by BEND IT 7 on 2008-09-16
I have past experience with Puppy installed on a flash drive, and have really liked it, but as a big Ubuntu fan (have desktop edition for sure) I would like to use an Ubuntu-based OS on a flash drive.  Fluxbuntu seems the best fit, size and memory usage wise, but I was wondering three things:
1) can it be done and easily booted?
2) can it be booted from a *partitioned* flash drive (I plan on splitting it about half Windows data and half Linux)?  By they way, does that work for Puppy, too?  Installing and booting to a partitioned flash drive.
3) how would a person go about doing this?

Thanks.

---

### Post by Sef on 2008-09-17
Read [Installation from USB Stick]("https://help.ubuntu.com/community/Installation/FromUSBStick").

---

### Post by snowpine on 2008-09-17
> **Sef said:**
> Read [Installation from USB Stick]("https://help.ubuntu.com/community/Installation/FromUSBStick").

Those are the instructions for installing *from* a USB stick, but I believe the OP wants to install *to* a USB stick. 

I haven't actually tried this with Fluxbuntu, but I have done it with Crunchbang, which is similar in terms of size and system requirements. The short answer is yes, you can install to a USB stick just as you would a regular hard drive. It is a totally normal installation in every way, no special instructions (apart from pointing the installer to the USB stick, not your hard drive). I would recommend *not* creating a swap partition if your computer has enough ram (since USB media is not designed for the constant read/write that swap requires). 

You need to be sure that Grub is written to the MBR of the USB stick, not your hard drive. I actually have a spare laptop with no hard drive that I use for exactly this purpose, therefore I can't tell you exactly which steps you'd need to take to protect your hard drive. So make sure you know exactly what you're doing.

The other drawback is that the bios on many older computers doesn't support booting from USB. I assume you have already tested whether your computer has this capability.

I don't know the answer to your partitioning question, sorry.

ps There is a 2nd type of USB installation called a LiveUSB. I do it with SliTaz, and I think Puppy has this capability as well (not 100% sure), but Fluxbuntu definitely does not (since it has no Live CD). The advantages of doing it this way are that it takes up less space on the USB drive and minimizes read/writes, prolonging the life of the media.

---

