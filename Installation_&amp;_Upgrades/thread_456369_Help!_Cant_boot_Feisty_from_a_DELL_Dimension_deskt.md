---
title: "Help! Cant boot Feisty from a DELL Dimension desktop!"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by intricate on 2007-05-27
I have a DELL Dimension desktop, 2 years old, that I'm trying to boot from the CD drive to install Feisty 7.04. The Feisty disk is absolutely good and has been used for other installs on other computers.  No matter what I do, even selecting the CD Drive as the first boot drive, the DELL DOES NOT SEE the Feisty install disk and then boots in to the other sucky OS, WIN XP.

All I can think of tis that the BIOS on the DELL DIMENSION needs to be flashed to upgrade. Are there any other  users who have had this problem and overcame it to share their solution?

Thank you fellow Ubuntuers!

---

### Post by Dennis the Menace on 2007-05-27
I've a Dell Dimension 2400 with XP pro, I never had any problems installing Edgy or Feisty.
So I don't know what your problem could be.
Not much help I know, just thought I'd tell you.

---

### Post by Ergo on 2007-05-27
Just as a way to troubleshoot, you could try unplugging your hard drive.  It would force the machine to use the cdrom.

---

### Post by confused57 on 2007-05-27
> **intricate said:**
> I have a DELL Dimension desktop, 2 years old, that I'm trying to boot from the CD drive to install Feisty 7.04. The Feisty disk is absolutely good and has been used for other installs on other computers.  No matter what I do, even selecting the CD Drive as the first boot drive, the DELL DOES NOT SEE the Feisty install disk and then boots in to the other sucky OS, WIN XP.

All I can think of tis that the BIOS on the DELL DIMENSION needs to be flashed to upgrade. Are there any other  users who have had this problem and overcame it to share their solution?

Thank you fellow Ubuntuers!
Have you tried pressing  "F12" during boot of your Dell?

---

### Post by Dennis the Menace on 2007-05-28
The way I did it was "press F2 at start and then disable HD and just let it boot from the CD", I'd no problems with either my Dell 2400 or Dell 8250.

---

### Post by MartynT on 2007-05-28
Have you tried booting from any other CDs ?  (Windows XP, Alternate CD, [System Rescue Disk]("http://www.sysresccd.org/Main_Page") )

If that doesn't work then you probably have a BIOS setup problem.  Disabling/removing the HDD won't force it to use the CD, it will just prevent it from using the HDD ;)

If other CDs do work, then the problem may well be with your LiveCD.  I know you've used it previously, but still.

I had several goes before I got an install to work.  First 6.04 crashed on install, then I tried 7.04 and that wouldn't even boot into LiveCD, finally I downloaded another 7.04 iso from a different mirror, to different media and used a different burner.  Finally, "it" ran out of hoops for me to jump through and decided to work :D

Good luck and post your solution if you find one.

Martyn.

---

