---
title: "Immediate Boot / Install Crash"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by jdm93rx_7 on 2006-11-01
I am trying to install Xubutu or Ubuntu (6.06.1) onto my PC.  It currently has XP Pro the primary ATA.

When I boot to the CD, I get the install screen.  When I choose an option, it tries to boot, and after about 1 second, the PC automatically reboots.

I have tried the following CDs:
- Ubuntu Desktop
- Xubuntu Desktop
- Xubuntu Desktop Alternate with text install

I have also unplugged all USB devices, secondary CD-ROM, all PCI cards, and all but one memory stick (of 512MB).

I also tried the noapic and nolapic switches as suggested for hardware prolems in the help file.

Hardware is a Compaq s7300cl, Celeron 2.8.  I would think if the hardware was good enough for XP Pro, it would be good enough for Ubuntu.

The only other clue is that I use an Acronis "ghost" CD, which is based on Linux, and I have to boot that one to "Safe Mode" if I want to use it with this PC.

Thanks in advance for any help.

---

### Post by gn2 on 2006-11-01
Is the Acronis CD an incremental back-up that you use with Windows?

Is it in when you are trying to run Ubuntu Live CD?

More information would help :-?

---

### Post by jdm93rx_7 on 2006-11-01
Acronis is just a harddrive imaging software with bootable CD that loads a linux kernel.  It's got an option for safemode, which is the only option that works with my PC.  But was only mentioning that as a possible clue.

The real issue is trying to install Ubuntu from the burned ISO cd... which does use linux live, except in the case of the test based install.

I have the exact same problem with all three CDs mentioned in my original post.  The CDs do work on my laptop.

It appears to be an issue between my Compaq hardware, and that version of the Linux kernel.

---

### Post by gn2 on 2006-11-01
Suggest checking if hardware is compatible with Linux.

Not an easy task, but this might get the ball rolling: [http://www.linux-drivers.org/](http://www.linux-drivers.org/)

Are the discs cd-rw, because changing to cd-r may help if they are?

---

