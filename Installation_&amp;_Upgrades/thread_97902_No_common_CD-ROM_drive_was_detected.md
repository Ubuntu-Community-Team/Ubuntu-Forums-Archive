---
title: "No common CD-ROM drive was detected"
date: 2005-12-01
forum: Installation &amp; Upgrades
---

### Post by pulento9 on 2005-12-01
hello everybody

I'm a new member and I just entered into the world of linux and I choose Ubuntu.

Here is my problem, I download the imagen of the ubuntu website which is arround 2.80GB dvd image and I pass it using NERO 7, everything goes well, i'm ready to install this new OS and I boot up, boots great detects cdrom great but right After selecting language, location and keyboard I get a error messege saying "No common CD-ROM drive was detected" it ask me to use a a diskete to install the cdrom drivers which I dont know what in the earth it's talking about.  I have tried reburning the image, i have tried the live version and still the same problem.  I have a Pentium 3 256MB memory and a DVD BURNER which does pretty much everything, you know reads dvds, burns dvds etc,,, that's the only cdrom (dvdrom) I have.

How can I fix the problem?
thank you

---

### Post by hatefulthreatening on 2005-12-01
Have you tried the normal cd image?

---

### Post by pulento9 on 2005-12-02
Yes I have.  I have used a normal CD image.

---

### Post by hatefulthreatening on 2005-12-02
[http://www.ubuntuforums.org/showthread.php?t=4447This]("http://www.ubuntuforums.org/showthread.php?t=4447") ubuntu forums thread might yield some answer..

Do you have a serial ata drive?

---

### Post by hatefulthreatening on 2005-12-02
looks like it's a  known debian installer bug. So I'm guessing it's also a known ubuntu installer bug.

> SATA driver can block access to CD drive in installations from CD. On systems having a SATA IDE controller that also has the CD drive connected to it, you may see the installer hanging during hardware detection for the CD drive or failing to read the CD just afterwards. A possible reason is that the SATA driver (ata_piix and maybe others) is blocking access to the CD drive.
 You can try to work around this by booting the installer in expert mode and, in the "Detect and mount CD-ROM" step, selecting only the drivers needed for CD support. These are (ide-)generic, ide-cd and isofs.
 The drivers needed to access the disk will still be loaded, but at a later stage. By loading the CD drivers before the SATA driver in this way, you may be able to complete the installation. Note that CD-ROM access may still be an issue after rebooting into the installed system.

---

### Post by pulento9 on 2005-12-02
No, I do not have SATA, just plain PATA DRIVES,,, one HD and  one CD BURNER, so it's a bug,,, mmm that's too bad plus I dont know how to do the workarround,,, I was a bit excited, well anyways that's too bad, thanks guys.

---

### Post by pulento9 on 2005-12-03
so there is no fix for this issue? wowww

---

